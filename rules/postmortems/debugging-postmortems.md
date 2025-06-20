---
description: Debugging and Postmortems
alwaysApply: false
---

# Post-Mortem Documentation Rule

## Purpose
Generate structured post-mortem documents after debugging sessions to capture the problem-solving process, solutions found, and lessons learned.

## Template Structure

### 1. Issue Summary
- **Problem Statement**: Clear, concise description of the issue
- **Impact**: Who/what was affected and how
- **Timeline**: When the issue started and when it was resolved
- **Severity**: Critical/High/Medium/Low

### 2. Root Cause Analysis
- **Initial Symptoms**: What was observed initially
- **Investigation Steps**: Chronological list of debugging actions taken
- **False Leads**: What didn't work and why
- **Root Cause**: The actual underlying issue(s)

### 3. Resolution
- **Solution Implemented**: Exact changes made to fix the issue
- **Code Changes**: List of files modified with brief descriptions
- **Testing**: How the fix was verified
- **Rollout**: How the fix was deployed

### 4. Lessons Learned
- **What Went Well**: Effective debugging strategies
- **What Could Be Improved**: Areas for better preparation
- **Action Items**: Preventive measures for the future
- **Documentation Updates**: What needs to be documented

### 5. Technical Details
- **Error Messages**: Exact error text for searchability
- **Stack Traces**: Relevant stack traces
- **Environment**: Where the issue occurred (local/staging/production)
- **Dependencies**: External services or libraries involved

## High-Level Rules for Debugging

### 1. Start with Observability
- Always check logs first (application, edge functions, database)
- Verify environment variables and secrets
- Check network requests in browser DevTools
- Use debugging tools specific to the platform (Supabase Dashboard, etc.)

### 2. Isolate the Problem
- Create minimal reproducible examples
- Test in different environments
- Remove variables one by one
- Use binary search to narrow down code sections

### 3. Document As You Go
- Keep a running log of what you've tried
- Note any error messages verbatim
- Track which changes made things better/worse
- Save working states before making major changes

### 4. Verify Assumptions
- Don't assume configuration is correct
- Check that APIs return what you expect
- Verify authentication/authorization at each layer
- Test with different user roles/permissions

### 5. Common Gotchas
- **Environment Variables**: Not available in all contexts (e.g., Edge Functions)
- **CORS**: Different origins require proper headers
- **RLS Policies**: Can silently filter results
- **Caching**: Clear caches when testing fixes
- **Async Operations**: Race conditions and timing issues

## Example Post-Mortem Structure

```markdown
# Post-Mortem: [Issue Title]
Date: [YYYY-MM-DD]
Author: [Name]
Duration: [Time spent debugging]

## Issue Summary
**Problem**: GitHub sync failing with "GitHub token not configured" error
**Impact**: Users unable to sync repository data
**Timeline**: Discovered on [date], resolved on [date]
**Severity**: High - core functionality broken

## Root Cause Analysis
**Initial Symptoms**: 
- Error message in UI: "GitHub token not configured"
- Edge Function returning 500 error

**Investigation Steps**:
1. Checked Edge Function logs - found missing env var
2. Verified secrets were set with `supabase secrets list`
3. Tested direct API calls with curl
4. [etc...]

**Root Cause**: Edge Functions require secrets to be set via `supabase secrets set` command, not just in .env file

## Resolution
**Solution**: Set GitHub token as Edge Function secret
**Code Changes**: 
- Updated deployment docs
- Added secret validation in Edge Function

## Lessons Learned
**What Went Well**: Systematic approach to checking each layer
**Action Items**: 
- Add secret validation to CI/CD
- Create debugging guide for Edge Functions
```

## Usage
1. After resolving a complex issue, create a new file in `/tasks/` named `post-mortem-[feature]-[date].md`
2. Use this template to structure your findings
3. Be specific about error messages and solutions for future searchability
4. Include code snippets where relevant
5. Link to related PRs, issues, or documentation

## Benefits
- Creates searchable knowledge base
- Helps team members facing similar issues
- Identifies patterns in recurring problems
- Improves debugging efficiency over time
- Documents tribal knowledge
