---
name: Secure Coding Practices
globs: "**/*.{js,ts,py,go,java,rb,cs}"
alwaysApply: true
description: Security-focused development practices to prevent vulnerabilities
---

You are an expert in application security, secure coding practices, and vulnerability prevention.

## Security Principles

- Never trust user input
- Apply defense in depth
- Fail securely
- Use least privilege principle
- Keep security simple
- Fix security issues correctly

## Input Validation and Sanitization

### Validate All Inputs

```typescript
// Input validation example
interface UserInput {
    email: string;
    age: number;
    username: string;
}

function validateUserInput(input: any): UserInput {
    // Type checking
    if (!input || typeof input !== 'object') {
        throw new Error('Invalid input format');
    }
    
    // Email validation
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!emailRegex.test(input.email)) {
        throw new Error('Invalid email format');
    }
    
    // Age validation
    const age = parseInt(input.age, 10);
    if (isNaN(age) || age < 0 || age > 150) {
        throw new Error('Invalid age');
    }
    
    // Username validation (alphanumeric + underscore only)
    const usernameRegex = /^[a-zA-Z0-9_]{3,30}$/;
    if (!usernameRegex.test(input.username)) {
        throw new Error('Invalid username format');
    }
    
    return {
        email: input.email.toLowerCase().trim(),
        age: age,
        username: input.username.trim()
    };
}
```

### SQL Injection Prevention

```python
# Bad: SQL injection vulnerable
def get_user_bad(user_id):
    query = f"SELECT * FROM users WHERE id = {user_id}"
    return db.execute(query)

# Good: Using parameterized queries
def get_user_secure(user_id):
    query = "SELECT * FROM users WHERE id = ?"
    return db.execute(query, (user_id,))

# Better: Using ORM with built-in protection
def get_user_orm(user_id):
    return User.query.filter_by(id=user_id).first()
```

## Authentication and Authorization

### Secure Password Handling

```javascript
const bcrypt = require('bcrypt');
const crypto = require('crypto');

class AuthService {
    // Password hashing
    async hashPassword(password) {
        const saltRounds = 12; // Use appropriate cost factor
        return await bcrypt.hash(password, saltRounds);
    }
    
    // Password verification
    async verifyPassword(password, hash) {
        return await bcrypt.compare(password, hash);
    }
    
    // Secure token generation
    generateSecureToken() {
        return crypto.randomBytes(32).toString('hex');
    }
    
    // JWT with expiration
    generateJWT(userId) {
        return jwt.sign(
            { userId, type: 'access' },
            process.env.JWT_SECRET,
            { 
                expiresIn: '15m',
                issuer: 'your-app',
                audience: 'your-app-users'
            }
        );
    }
}
```

### Session Management

```python
# Secure session configuration
app.config.update(
    SESSION_COOKIE_SECURE=True,  # HTTPS only
    SESSION_COOKIE_HTTPONLY=True,  # No JS access
    SESSION_COOKIE_SAMESITE='Lax',  # CSRF protection
    PERMANENT_SESSION_LIFETIME=timedelta(minutes=30),
    SESSION_COOKIE_NAME='__Host-session'  # Cookie prefix
)

# Session validation
def validate_session(session_id):
    session = Session.query.filter_by(id=session_id).first()
    
    if not session:
        raise SecurityError("Invalid session")
    
    if session.expired_at < datetime.utcnow():
        raise SecurityError("Session expired")
    
    if session.ip_address != request.remote_addr:
        # Log potential session hijacking
        logger.warning(f"IP mismatch for session {session_id}")
        raise SecurityError("Session validation failed")
    
    return session
```

## Data Protection

### Encryption

```typescript
import { createCipheriv, createDecipheriv, randomBytes, scrypt } from 'crypto';
import { promisify } from 'util';

class EncryptionService {
    private algorithm = 'aes-256-gcm';
    private scryptAsync = promisify(scrypt);
    
    async encrypt(text: string, password: string): Promise<string> {
        const salt = randomBytes(32);
        const key = await this.scryptAsync(password, salt, 32) as Buffer;
        const iv = randomBytes(16);
        const cipher = createCipheriv(this.algorithm, key, iv);
        
        const encrypted = Buffer.concat([
            cipher.update(text, 'utf8'),
            cipher.final()
        ]);
        
        const tag = cipher.getAuthTag();
        
        return Buffer.concat([salt, iv, tag, encrypted]).toString('base64');
    }
    
    async decrypt(encryptedData: string, password: string): Promise<string> {
        const buffer = Buffer.from(encryptedData, 'base64');
        const salt = buffer.slice(0, 32);
        const iv = buffer.slice(32, 48);
        const tag = buffer.slice(48, 64);
        const encrypted = buffer.slice(64);
        
        const key = await this.scryptAsync(password, salt, 32) as Buffer;
        const decipher = createDecipheriv(this.algorithm, key, iv);
        decipher.setAuthTag(tag);
        
        return decipher.update(encrypted) + decipher.final('utf8');
    }
}
```

### Secure File Handling

```python
import os
import hashlib
from pathlib import Path

class SecureFileHandler:
    ALLOWED_EXTENSIONS = {'.jpg', '.png', '.pdf', '.doc', '.docx'}
    MAX_FILE_SIZE = 10 * 1024 * 1024  # 10MB
    
    def validate_file(self, file):
        # Check file size
        file.seek(0, 2)
        size = file.tell()
        file.seek(0)
        
        if size > self.MAX_FILE_SIZE:
            raise ValueError("File too large")
        
        # Validate extension
        extension = Path(file.filename).suffix.lower()
        if extension not in self.ALLOWED_EXTENSIONS:
            raise ValueError("File type not allowed")
        
        # Check file content matches extension
        file_header = file.read(512)
        file.seek(0)
        
        if not self._validate_file_type(file_header, extension):
            raise ValueError("File content does not match extension")
        
        return True
    
    def save_file_securely(self, file, user_id):
        # Generate secure filename
        timestamp = datetime.utcnow().timestamp()
        random_str = secrets.token_hex(16)
        extension = Path(file.filename).suffix.lower()
        
        filename = hashlib.sha256(
            f"{user_id}{timestamp}{random_str}".encode()
        ).hexdigest() + extension
        
        # Save to secure location outside web root
        secure_path = Path('/secure/uploads') / filename
        file.save(secure_path)
        
        # Set restrictive permissions
        os.chmod(secure_path, 0o600)
        
        return filename
```

## Security Headers

```javascript
// Express.js security headers
const helmet = require('helmet');

app.use(helmet({
    contentSecurityPolicy: {
        directives: {
            defaultSrc: ["'self'"],
            scriptSrc: ["'self'", "'unsafe-inline'"],
            styleSrc: ["'self'", "'unsafe-inline'"],
            imgSrc: ["'self'", "data:", "https:"],
            connectSrc: ["'self'"],
            fontSrc: ["'self'"],
            objectSrc: ["'none'"],
            mediaSrc: ["'self'"],
            frameSrc: ["'none'"],
        },
    },
    hsts: {
        maxAge: 31536000,
        includeSubDomains: true,
        preload: true
    }
}));

// Additional security headers
app.use((req, res, next) => {
    res.setHeader('X-Frame-Options', 'DENY');
    res.setHeader('X-Content-Type-Options', 'nosniff');
    res.setHeader('Referrer-Policy', 'strict-origin-when-cross-origin');
    res.setHeader('Permissions-Policy', 'geolocation=(), microphone=()');
    next();
});
```

## Best Practices

- Never store secrets in code
- Use environment variables for configuration
- Implement rate limiting
- Log security events
- Keep dependencies updated
- Use static analysis tools
- Perform security code reviews
- Test for common vulnerabilities