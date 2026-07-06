```markdown
# bytebot Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill provides a comprehensive guide to the development patterns used in the `bytebot` TypeScript codebase. It covers file organization, coding conventions, testing strategies, and automated workflows for maintaining dependencies across multiple packages. Whether you're contributing code, reviewing pull requests, or managing dependencies, this document will help you align with the established practices of the repository.

## Coding Conventions

### File Naming
- **Style:** kebab-case
- **Example:**  
  ```
  user-profile.ts
  data-fetcher.test.ts
  ```

### Import Style
- **Relative imports** are used throughout the codebase.
- **Example:**
  ```typescript
  import { fetchData } from './utils/fetch-data';
  ```

### Export Style
- **Named exports** are preferred.
- **Example:**
  ```typescript
  // In user-profile.ts
  export function getUserProfile(id: string) { ... }

  // In another file
  import { getUserProfile } from './user-profile';
  ```

### Commit Patterns
- **Type:** Freeform (no strict prefixes)
- **Average length:** ~64 characters
- **Example:**
  ```
  Fix bug in data fetcher when API returns empty response
  ```

## Workflows

### Dependency Update Across Multiple Packages
**Trigger:** When you need to keep npm dependencies up to date across all packages in the monorepo.  
**Command:** `/update-dependencies`

1. Identify outdated dependencies in each package directory.
2. Update `package.json` and `package-lock.json` in each affected package.
3. Commit all updated files together, ideally with a changelog or a list of updated dependencies.

**Files Involved:**
- `packages/*/package.json`
- `packages/*/package-lock.json`

**Frequency:** Approximately 2-4 times per month.

**Example Workflow:**
```bash
# 1. Check for outdated dependencies
npm outdated --workspaces

# 2. Update dependencies in each package
npm update --workspaces

# 3. Review and commit changes
git add packages/*/package.json packages/*/package-lock.json
git commit -m "Update dependencies across all packages"
```

## Testing Patterns

- **File Pattern:** Test files are named using the pattern `*.test.*` (e.g., `user-profile.test.ts`).
- **Testing Framework:** Not explicitly detected; check the repository for details.
- **Example Test File:**
  ```typescript
  // user-profile.test.ts
  import { getUserProfile } from './user-profile';

  describe('getUserProfile', () => {
    it('returns user data for valid ID', () => {
      // test implementation
    });
  });
  ```

## Commands

| Command              | Purpose                                                         |
|----------------------|-----------------------------------------------------------------|
| /update-dependencies | Update npm dependencies across all packages in the monorepo      |
```
