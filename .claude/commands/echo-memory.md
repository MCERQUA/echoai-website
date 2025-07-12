# Echo AI System Memory

## Project Context Memory

### Current Project: CCA (Contractor Insurance Website)
- **Technology Stack**: Next.js 15, TypeScript, Tailwind CSS v3, React 19
- **Architecture**: Component-based, modular design, files under 150 lines
- **Deployment**: Netlify with forms integration

### Historical Problem Patterns

#### 1. CSS Inheritance Issues
- **Problem**: Button text colors inherited from parent elements
- **Solution**: Use `!important` prefix (`!text-white`, `!text-gray-900`)
- **Status**: Resolved 2025-06-27
- **Pattern**: Always force critical button styles

#### 2. String Method Errors
- **Problem**: Calling `.replace()`, `.trim()` on undefined values
- **Solution**: Validate before string operations
- **Common Location**: Time processing, array splitting
- **Prevention**: Check `typeof string === 'string'` first

#### 3. HTML Entity Display Issues
- **Problem**: HTML entities showing as literal text (`&apos;`)
- **Solution**: Use proper Unicode characters in data files
- **Impact**: UX issue - content displays incorrectly
- **Fix Applied**: 2025-06-27, 11+ occurrences corrected

#### 4. Netlify Forms Integration
- **Challenge**: 2.5+ days of troubleshooting
- **Resolution**: Multiple debugging sessions, final success
- **Key Learning**: Form endpoint configuration critical
- **Status**: All 3 forms working successfully

### Successful Solution Patterns

#### Two-Step Fix Methodology
1. **Runtime Safety**: Prevent crashes with null/undefined checks
2. **Type Safety**: Maintain TypeScript contracts
- **Success Rate**: High reliability in preventing deployment failures

#### Component Validation Pattern
```typescript
// Established pattern for dynamic components
const Component = componentMap[key as keyof typeof componentMap]
if (!Component) return null
return <Component className="..." />
```

#### String Processing Safety Pattern
```typescript
// Proven pattern for string operations
const parts = input.split(' - ')
if (parts.length !== 2) return null
const [first, second] = parts
if (!first || !second || typeof first !== 'string') return null
return first.replace('pattern', 'replacement')
```

### Configuration Knowledge

#### Key Files and Their Purposes
- `/config/site.config.ts`: Business information, contact details
- `/config/navigation.config.ts`: Site navigation structure
- `CLAUDE.md`: Project instructions and guidelines
- `docs/AI-ERROR-TRACKER.md`: Error documentation system

#### Tailwind CSS Specifics
- Uses v3 (not v4)
- Numbered color variants (`text-primary-500`)
- Custom color scales: primary (blue), secondary (orange)
- Utility function: `cn()` for conditional classes

### Recent Development Milestones

#### Forms Resolution (Latest Achievement)
- **Duration**: 2.5+ days of intensive debugging
- **Outcome**: All forms now working correctly
- **Impact**: Major UX improvement, client satisfaction
- **Learning**: Persistence and systematic debugging pays off

#### Deployment Stability Improvements
- **Error Prevention**: Proactive validation patterns
- **Type Safety**: Enhanced TypeScript usage
- **Testing**: Local build verification before deployment
- **Documentation**: Comprehensive error tracking

### Development Workflow Memory

#### Best Practices Established
1. Always read `CLAUDE.md` before code changes
2. Update error tracker immediately when issues arise
3. Test with `npm run build` locally
4. Document successful solutions for future reference

#### Common Debugging Approach
1. Identify error type (runtime vs type)
2. Check for established patterns in memory
3. Apply proven solution patterns
4. Validate fix thoroughly
5. Document outcome

### Project-Specific Knowledge

#### Business Domain: Contractor Insurance
- Services: Workers comp, general liability, commercial auto, etc.
- Target Audience: Construction contractors, builders
- Geographic Focus: Arizona (primary)
- Content Strategy: Educational blog posts, service descriptions

#### Technical Implementation Details
- MDX for content management
- Structured data for SEO
- Google Reviews integration
- Responsive design with mobile-first approach
- Performance optimization with image handling

This memory system helps maintain context across development sessions and provides quick access to proven solutions and project-specific knowledge.