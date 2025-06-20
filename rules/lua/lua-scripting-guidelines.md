---
name: Lua Scripting Guidelines
globs: "**/*.lua"
alwaysApply: false
description: Guidelines for writing effective Lua scripts and automation
---

# Lua Scripting Guidelines

## Script Structure

- Start scripts with proper shebang for executable files
- Use clear script organization with logical sections
- Include script documentation at the top
- Handle command-line arguments appropriately
- Implement proper exit codes for script success/failure

## Argument Processing

- Use `arg` table for command-line arguments
- Validate input arguments before processing
- Provide helpful usage messages for incorrect arguments
- Use libraries like `argparse` for complex argument handling
- Handle both short and long option formats

## File Operations

- Always check file operations for errors
- Use proper file handle management with explicit closing
- Handle file permissions and access errors gracefully
- Use `io.lines()` for efficient line-by-line processing
- Implement atomic file operations when needed

## Environment Integration

- Use `os.getenv()` for environment variable access
- Handle missing environment variables gracefully
- Use `os.execute()` carefully with proper error checking
- Sanitize inputs when executing external commands
- Use `io.popen()` for capturing command output

## Configuration Management

- Use Lua tables for configuration data
- Load configuration from external files when appropriate
- Provide sensible defaults for configuration values
- Validate configuration parameters
- Support both JSON and Lua configuration formats

## Logging and Output

- Use consistent logging levels (debug, info, warn, error)
- Implement structured logging for better parsing
- Use stderr for error messages and warnings
- Use stdout only for actual script output
- Implement quiet and verbose modes appropriately

## Error Handling

- Use `pcall` for recoverable operations
- Provide meaningful error messages with context
- Log errors appropriately before exiting
- Use appropriate exit codes for different error types
- Implement retry logic for transient failures

## Cross-Platform Considerations

- Use `package.config` to detect path separators
- Handle platform-specific file paths appropriately
- Use `os.type` or similar detection for platform-specific code
- Test scripts on target platforms
- Use portable libraries when available

## Performance for Scripts

- Avoid unnecessary computations in loops
- Use local variables for frequently accessed values
- Cache expensive operations when possible
- Process data in chunks for large datasets
- Profile long-running scripts for bottlenecks

## Security Considerations

- Validate and sanitize all external inputs
- Avoid executing arbitrary code from untrusted sources
- Use secure temporary file creation
- Handle sensitive data appropriately
- Implement proper permission checks

## Testing Scripts

- Write unit tests for script functions
- Test with various input scenarios
- Test error conditions and edge cases
- Use mocking for external dependencies
- Implement integration tests for end-to-end workflows

## Documentation

- Include usage examples in script comments
- Document expected input and output formats
- Explain complex algorithms or business logic
- Provide troubleshooting information
- Keep documentation updated with code changes