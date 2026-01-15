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

1. Navigate to **KWikSync**  **Connection Settings**
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
1. Navigate to **KWikSync**  **KWikSync Hub**
2. Click **Sync Now**
3. Monitor progress in the Sync Log

### Sync Scheduling

Configure automated synchronization:
1. Navigate to **Connection Settings**
2. Set the **Sync Frequency**
3. Optionally set a **Sync Window** (e.g., off-peak hours only)
4. Save changes

### Monitoring Sync Operations

**Sync Log:**
- Navigate to **KWikSync**  **Sync Log**
- View all sync operations with timestamps
- Filter by date, status, or record type

**Error Log:**
- Navigate to **KWikSync**  **Error Log**
- View failed operations and error details
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
| `x_kwr_kwiksync_field_mapping` | Field mapping configuration |
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

All operations are logged for compliance:
- Sync operations logged in Sync Log
- Errors logged in Error Log
- Standard ServiceNow audit on all table records

---

## Maintenance

### Log Cleanup

Periodically clean up old log entries:
1. Navigate to **KWikSync**  **Sync Log**
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
