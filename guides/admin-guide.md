# Administrator Guide

[ Back to Documentation](../README.md)

---

## Overview

This guide covers advanced configuration, security settings, and administrative tasks for KWikSync. Intended for ServiceNow administrators and KWikSync admins.

---

## Role Management

### Available Roles

| Role | Access Level | Use Case |
|------|--------------|----------|
| `x_kwr_kwiksync.admin` | Full access to all features, settings, and configuration | System administrators |
| `x_kwr_kwiksync.user` | Read/write access to data, no configuration access | End users, managers, technicians |

### Assigning Roles

**Individual Assignment:**
1. Navigate to **User Administration**  **Users**
2. Open the user record
3. In the **Roles** related list, click **Edit**
4. Add `x_kwr_kwiksync.admin` or `x_kwr_kwiksync.user`
5. Click **Save**

**Group Assignment:**
1. Navigate to **User Administration**  **Groups**
2. Create or edit a group (e.g., "KWikSync Users")
3. Add the appropriate role to the group
4. Add users to the group

---

## Connection Settings

### Accessing Settings

1. Navigate to **KWikSync**  **Settings**  **Connection Settings**
2. Requires `x_kwr_kwiksync.admin` role

### Configuration Options

| Setting | Description |
|---------|-------------|
| **Customer Key** | Unique identifier provided by KW Corporation |
| **Sync Frequency** | How often automatic sync runs (hourly, daily, etc.) |
| **Sync Direction** | Inbound, outbound, or bidirectional |
| **Error Notifications** | Email alerts for sync failures |

### Testing Connection

1. After entering your Customer Key, click **Test Connection**
2. A success message confirms valid configuration
3. If the test fails, verify your Customer Key and network connectivity

---

## Sync Management

### Manual Sync

Trigger synchronization on-demand:
1. Navigate to **KWikSync**  **KWikSync Connection Dashboard** (or click SYNC on any card)
2. Use **SYNC ALL TABLES** or individual **SYNC** buttons per module
3. Monitor progress via the **Activity Log** in the dashboard UI

>  **Tip**: The Connection Dashboard shows real-time status (IDLE/SYNCING) and messages in the Activity Log.

### Sync Scheduling

Configure automated synchronization:
1. Navigate to **Connection Settings**
2. Set the **Sync Frequency**
3. Optionally set a **Sync Window** (e.g., off-peak hours only)
4. Save changes

### Monitoring Sync Operations

**Real-Time Monitoring (Connection Dashboard):**
- Navigate to **KWikSync**  **Settings**  **Connection Settings**
- Watch the **Activity Log** panel for live sync messages
- Each card displays record count and last sync timestamp
- Status indicators show IDLE or SYNCING state

**Sync Log (Historical):**
- Navigate to **KWikSync**  **Sync Log** (table view)
- View all sync operations with timestamps
- Filter by date, status, or table
- See records processed, created, updated, and failed counts

**Error Log:**
- Navigate to **KWikSync**  **Error Log**
- View failed operations and error details
- Includes error type, severity, and stack trace
- Use for troubleshooting sync issues

---

## Data Management

### Field Mapping

KWikSync uses configurable field mapping to translate data between systems:

1. Navigate to **KWikSync**  **Field Mapping**
2. View existing mappings
3. Modify mappings as needed (admin only)

### Data Tables

KWikSync manages the following tables:

| Table | Purpose |
|-------|---------|
| `x_kwr_kwiksync_configuration` | Application settings |
| `x_kwr_kwiksync_projects` | Project records |
| `x_kwr_kwiksync_tickets` | Ticket/work order records |
| `x_kwr_kwiksync_kw_corp_ticket_tasks` | Task records |
| `x_kwr_kwiksync_assets` | Asset/inventory records |
| `x_kwr_kwiksync_locations` | Location/site records |
| `x_kwr_kwiksync_deliverables` | Deliverable records |
| `x_kwr_kwiksync_sync_log` | Sync operation history |
| `x_kwr_kwiksync_error_log` | Error tracking |

---

## Security & Access Control

### ACL Configuration

All KWikSync tables are protected by Access Control Lists (ACLs):

- **Read**: Requires `x_kwr_kwiksync.user` or `x_kwr_kwiksync.admin`
- **Write**: Requires `x_kwr_kwiksync.user` or `x_kwr_kwiksync.admin`
- **Delete**: Requires `x_kwr_kwiksync.admin`
- **Admin**: Requires `x_kwr_kwiksync.admin`

### Audit Trail

All operations are logged for compliance using KWikSync's custom logging tables:

| Log Table | Purpose |
|-----------|---------|
| `x_kwr_kwiksync_sync_log` | Records all sync operations with timestamps, table names, record counts (processed/created/updated/failed), and status |
| `x_kwr_kwiksync_error_log` | Captures errors with type, severity, message, stack trace, and resolution status |

**Standard ServiceNow Audit:**
- All KWikSync table records also leverage ServiceNow's native audit capabilities
- Field-level changes tracked via sys_audit table
- Access to audit data via standard ServiceNow reporting

>  **Note**: KWikSync logging is custom-built within the scoped application and does not require additional ServiceNow plugins.

---

## Maintenance

### Log Cleanup

Periodically clean up old log entries:
1. Navigate to **KWikSync**  **Sync Log** or **Error Log**
2. Filter for records older than retention period
3. Delete or archive as needed

### Performance Optimization

- Schedule syncs during off-peak hours
- Use filters to sync only changed records
- Monitor sync duration trends

---

## Integration Details

### IntegrationHub ETL

KWikSync leverages IntegrationHub ETL for data transformation:

- Requires **IntegrationHub ETL** license
- Uses native ETL tables for compatibility
- Supports complex field transformations

### API Endpoints

KWikSync exposes REST APIs for advanced integration:
- See [Integration Overview](../api/integration-overview.md)
- See [Field Mapping Reference](../api/field-mapping.md)

---

## Support

### Getting Help

- **Email**: ServiceNowSupport@kw-corp.com
- **Support Hours**: Monday - Friday, 8 AM - 6 PM EST

### Reporting Issues

1. Navigate to **KWikSync**  **Support**
2. Click **Submit Issue**
3. Include:
   - Detailed description
   - Steps to reproduce
   - Error messages (if any)
   - Screenshots (if helpful)

---

## Related Guides

-  [Getting Started](getting-started.md) - Installation and setup
-  [User Guide](user-guide.md) - Feature overview
-  [Troubleshooting](troubleshooting.md) - Common issues

---

[ Back to Documentation](../README.md)
