# File Manifest - Clean ServiceNow Test Integration

**Scope:** x_ic_clean_test
**Version:** 1.0.0
**Total Files:** 6

---

## File Categories

- **CONFIG**: 3 files (3 required, 0 optional)
- **DOC**: 1 files (1 required, 0 optional)
- **FLUENT**: 1 files (1 required, 0 optional)
- **SERVER**: 1 files (1 required, 0 optional)

---

## Configuration Files

### `now.config.json` **[REQUIRED]**

ServiceNow SDK configuration defining scope, directories, and build outputs

### `package.json` **[REQUIRED]**

NPM package metadata with application name, version, and build scripts

### `tsconfig.json` **[REQUIRED]**

TypeScript compiler configuration for Fluent and server modules

## Documentation

### `README.md` **[REQUIRED]**

Comprehensive installation guide, schema documentation, and troubleshooting

## Fluent Metadata

### `src/fluent/main.now.ts` **[REQUIRED]**

ServiceNow Fluent DSL metadata defining tables, fields, relationships, and behaviors

**Key Functions:**
- Defines CMDB CI class structure
- Creates table relationships and hierarchies
- Configures field types, labels, and constraints
- Sets up identification and reconciliation rules

## Server-Side Logic

### `src/server/runtimeConfig.ts` **[REQUIRED]**

Runtime configuration loader for accessing sys_properties and settings

---

## Installation Impact

### File System Changes

All files are installed within the application scope and do not modify global system files.

### Database Changes

- **New Table:** `x_ic_clean_test_clean_servicenow_test_ci` with custom fields
- **System Properties:** Configuration values with scope prefix

### Update Set Contents

The installation creates or modifies:
- Dictionary entries (for custom fields)
- UI elements (forms, lists, pages)
- Script includes (server-side logic)
- Client scripts (UI behavior)

---

## Removal & Cleanup

To completely remove this application:

1. **Delete the application** via System Applications > Applications
2. **Manually delete tables** if they were created (backup data first)
3. **Remove system properties** with scope prefix via System Properties > All
4. **Review ACLs** and remove scoped rules if needed
5. **Check scheduled jobs** and delete any integration-related jobs

**WARNING:** Deleting the application does NOT automatically delete tables or data. Always backup before removal.
