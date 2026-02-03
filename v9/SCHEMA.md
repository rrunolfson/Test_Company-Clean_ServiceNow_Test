# Database Schema Documentation
# Clean ServiceNow Test Integration

**Scope:** x_ic_clean_test
**Version:** 1.0.0
**Tables:** 1

---

## Table of Contents

1. [Clean ServiceNow Test Integration CI](#clean-servicenow-test-integration-ci)

---

## Schema Overview

This application modifies the ServiceNow database schema by creating custom tables and fields.
All schema changes are scoped to prevent conflicts with other applications.

### Schema Safety

- All tables use scoped names to avoid conflicts
- Fields are created with appropriate constraints
- Indexes are defined for performance optimization
- ACL rules control access to data

---

## Clean ServiceNow Test Integration CI

**Table Name:** `x_ic_clean_test`
**Extends:** `cmdb_ci`

**Description:** Custom CI table for Clean ServiceNow Test Integration CI integration data

### Fields

| Field | Type | Label | Mandatory | Description |
|-------|------|-------|-----------|-------------|
| `systemId` | string | SystemId |  | Unique system identifier |
| `deviceId` | string | DeviceId |  | Device identifier |
| `deviceName` | string | DeviceName |  | Human-readable device name |
| `status` | string | Status |  | Device operational status |
| `lastContact` | glide_date_time | LastContact |  | Last communication timestamp |

### Field Details

#### SystemId (`systemId`)

- **Type:** string
- **Mandatory:** No

Unique system identifier

#### DeviceId (`deviceId`)

- **Type:** string
- **Mandatory:** No

Device identifier

#### DeviceName (`deviceName`)

- **Type:** string
- **Mandatory:** No

Human-readable device name

#### Status (`status`)

- **Type:** string
- **Mandatory:** No

Device operational status

#### LastContact (`lastContact`)

- **Type:** glide_date_time
- **Mandatory:** No

Last communication timestamp

### Usage Examples

#### Query Records
```javascript
var gr = new GlideRecord('x_ic_clean_test');
gr.query();
while (gr.next()) {
  gs.info(gr.getValue('systemId'));
}
```

#### Create Record
```javascript
var gr = new GlideRecord('x_ic_clean_test');
gr.initialize();
gr.setValue('systemId', 'example value');
gr.setValue('deviceId', 'example value');
gr.setValue('deviceName', 'example value');
var sysId = gr.insert();
gs.info('Created record: ' + sysId);
```

#### Update Record
```javascript
var gr = new GlideRecord('x_ic_clean_test');
gr.addQuery('sys_id', '<record_sys_id>');
gr.query();
if (gr.next()) {
  gr.setValue('systemId', 'new value');
  gr.update();
  gs.info('Record updated');
}
```

---

## Migration & Upgrade Notes

### Initial Installation

1. All tables are created automatically during app installation
2. Dictionary entries are generated for all fields
3. Indexes are created for performance
4. ACL rules are applied for scoped access

### Upgrading

When upgrading to newer versions:

- **Schema changes** are applied automatically
- **Existing data** is preserved
- **New fields** are added with default values
- **Deprecated fields** are not removed (for safety)

**Best Practice:** Always test upgrades in a sub-production instance first.

### Rollback

To rollback schema changes:

1. **Backup data** from custom tables before rollback
2. **Uninstall application** via System Applications
3. **Manually delete tables** if they persist
4. **Restore from backup** if needed

**WARNING:** Uninstalling does not automatically delete tables or data.

---

## Data Dictionary Export

For compliance and documentation purposes, export the data dictionary:

1. Navigate to **System Definition > Dictionary**
2. Filter by table names listed in this document
3. Export as XML or Excel
4. Store with application documentation
