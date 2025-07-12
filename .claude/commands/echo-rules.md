# Echo AI System Rules

## Core Operating Principles

### 1. Code Quality Standards
- Always prioritize type safety and runtime safety
- Follow the two-step fix rule: runtime safety first, then type safety
- Validate all inputs before processing
- Use proper null/undefined checks

### 2. Development Workflow Rules
- Read project instructions (CLAUDE.md) before making changes
- Document errors in AI-ERROR-TRACKER.md immediately when issues arise
- Follow the mandatory error documentation protocol
- Test locally with `npm run build` before committing

### 3. Content and Styling Guidelines
- Use Tailwind CSS v3 with numbered color variants
- Apply `!important` prefix for button text colors to prevent inheritance
- Use proper Unicode characters instead of HTML entities in data files
- Validate dynamic components before rendering

### 4. Architecture Compliance
- Maintain component size under 150 lines for AI manipulation
- Use proper TypeScript types throughout
- Follow the established component structure
- Keep configuration centralized in config files

### 5. Deployment Safety Rules
- Always validate array.split() results before string operations
- Check for undefined/null before calling string methods
- Maintain TypeScript contracts in array processing
- Use context-appropriate escaping rules

### 6. Error Handling Protocol
- Apply runtime safety checks first
- Implement proper error boundaries
- Validate all external data sources
- Provide fallback behaviors for critical components

### 7. Memory and Context Rules
- Maintain conversation context across sessions
- Reference previous solutions for similar problems
- Build upon established patterns and fixes
- Document successful solutions for future reference

### 8. Supabase Storage Rules
- Always use Row Level Security (RLS) policies for user data isolation
- Generate signed URLs for temporary secure access (24-hour expiration max)
- Store file metadata in database tables for tracking and compliance
- Use proper storage path structure: `{type}/{client_id}/{filename}`
- Validate file types and sizes before upload (PDF only, 10MB max)
- Implement proper error handling for storage operations
- Use Supabase service role key for admin operations only
- Leverage built-in encryption at rest (AES-256) for sensitive documents

## Response Patterns

### Code Analysis
- Identify potential runtime errors before type errors
- Check for common deployment failure patterns
- Validate component dependencies and imports
- Assess TypeScript compliance

### Problem Solving
- Apply established patterns from project history
- Reference successful fixes from error tracker
- Consider deployment implications of changes
- Prioritize user experience and functionality

### Communication
- Provide clear, actionable solutions
- Explain the reasoning behind fixes
- Reference specific project guidelines
- Maintain professional development standards

## Emergency Protocols

### Critical Deployment Failures
1. Immediately identify error type (runtime vs type)
2. Apply two-step fix methodology
3. Test with `npm run build`
4. Document solution in error tracker
5. Consider rollback if urgent

### CSS Inheritance Issues
- Use `!important` prefix for critical styles
- Test visual rendering in browser
- Validate button text visibility
- Check component isolation

### String Processing Errors
- Validate inputs before string operations
- Check array split results
- Implement proper error handling
- Maintain type safety

These rules ensure consistent, reliable development practices and help prevent common issues that have occurred in this project's history.