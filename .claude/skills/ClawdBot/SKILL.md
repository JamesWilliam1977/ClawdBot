```markdown
# ClawdBot Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill provides a comprehensive guide to contributing to the ClawdBot codebase, a TypeScript project with no formal framework. It outlines the project's coding conventions, commit patterns, and common development workflows. You'll learn how to structure code, write and organize tests, and follow established processes for updating locale metadata, adding features, managing gateway methods, updating provider catalogs, and maintaining iMessage monitor state. This guide is designed to help new and existing contributors maintain consistency and quality across the codebase.

## Coding Conventions

- **File Naming:**  
  Use kebab-case for all file names.  
  _Example:_  
  ```
  user-profile.ts
  message-handler.test.ts
  ```

- **Import Style:**  
  Use relative imports for internal modules.  
  _Example:_  
  ```typescript
  import { fetchUser } from './user-service';
  ```

- **Export Style:**  
  Use named exports for all modules.  
  _Example:_  
  ```typescript
  // user-service.ts
  export function fetchUser(id: string) { ... }
  ```

- **Commit Messages:**  
  Follow conventional commit prefixes: `fix`, `chore`, `refactor`, `test`, `feat`.  
  _Example:_  
  ```
  feat: add support for new provider catalog
  fix: resolve iMessage monitor state bug
  ```

## Workflows

### Refresh UI Locale Metadata
**Trigger:** When updating or synchronizing UI translations or locale metadata.  
**Command:** `/refresh-locale`

1. Edit or regenerate the relevant locale meta JSON file in `ui/src/i18n/.i18n/`.
2. Commit the change with a message indicating the locale was refreshed.

_Example:_  
```
ui/src/i18n/.i18n/fr.meta.json
```
```
chore: refresh French locale metadata
```

---

### Feature or Bugfix with Tests
**Trigger:** When adding a new feature or fixing a bug, ensuring it's covered by tests.  
**Command:** `/feature-with-tests`

1. Edit or create implementation files (e.g., `.ts`).
2. Edit or create corresponding test files (e.g., `.test.ts`) in the same or related directory.
3. Commit both implementation and test changes together.

_Example:_  
```
src/agents/user-agent.ts
src/agents/user-agent.test.ts
```
```
feat: add user agent with tests
```

---

### Add or Update Gateway Method
**Trigger:** When adding a new or updating an existing gateway API method.  
**Command:** `/new-gateway-method`

1. Edit or create a file in `src/gateway/server-methods/*.ts`.
2. Edit or create the corresponding test file in `src/gateway/server-methods/*.test.ts`.
3. Optionally update related schema or utility files.

_Example:_  
```
src/gateway/server-methods/send-message.ts
src/gateway/server-methods/send-message.test.ts
```
```
feat: add send-message gateway method
```

---

### Provider Catalog Update
**Trigger:** When adding, updating, or fixing provider catalog/model metadata.  
**Command:** `/update-provider-catalog`

1. Edit `provider-catalog.ts` or `model-catalog.ts`.
2. Edit or update the corresponding test files.
3. Commit both files together.

_Example:_  
```
src/agents/model-catalog.ts
src/agents/model-catalog.test.ts
```
```
fix: update model catalog for new provider
```

---

### iMessage Monitor State Update
**Trigger:** When changing how iMessage monitor state is stored or processed.  
**Command:** `/update-imessage-monitor`

1. Edit or create iMessage monitor implementation files in `extensions/imessage/src/monitor/`.
2. Edit or create corresponding test files.
3. Edit or create migration or persistence logic.
4. Update related documentation in `docs/channels/imessage*.md`.

_Example:_  
```
extensions/imessage/src/monitor/state-manager.ts
extensions/imessage/src/monitor/state-manager.test.ts
extensions/imessage/src/state-migrations.ts
docs/channels/imessage-sqlite.md
```
```
refactor: migrate iMessage monitor state to SQLite
```

## Testing Patterns

- **Framework:**  
  All tests use [Vitest](https://vitest.dev/).

- **File Pattern:**  
  Test files are named with the `.test.ts` suffix and are placed alongside or near the implementation files.

- **Example Test File:**  
  ```typescript
  // src/agents/user-agent.test.ts
  import { describe, it, expect } from 'vitest';
  import { fetchUser } from './user-agent';

  describe('fetchUser', () => {
    it('should return user data for valid ID', async () => {
      const user = await fetchUser('123');
      expect(user).toHaveProperty('id', '123');
    });
  });
  ```

## Commands

| Command                 | Purpose                                                      |
|-------------------------|--------------------------------------------------------------|
| /refresh-locale         | Refresh or update UI locale metadata                         |
| /feature-with-tests     | Add a new feature or bugfix with corresponding tests         |
| /new-gateway-method     | Add or update a gateway server method                        |
| /update-provider-catalog| Update provider or model catalog and related tests           |
| /update-imessage-monitor| Update iMessage monitor state logic and documentation        |
```