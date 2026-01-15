# Integration Overview

[ Back to Documentation](../README.md)

---

## Overview

KWikSync provides robust integration capabilities for connecting ServiceNow with external data sources. This document covers the technical architecture and integration patterns.

---

## Architecture

\\\

                        External Systems                          
         
    ERP         CRM         Custom      Other Sources    
         

                                                   
        
                             
                    
                      IntegrationHub 
                           ETL       
                    
                             
        
                      KWikSync Core              
             
                   Field Mapping               
              Transform  Validate  Load      
             
        
                             

                      KWikSync Tables                             
                 
   Projects   Tickets     Assets   Locations     ...     
                 

\\\

---

## Integration Methods

### IntegrationHub ETL

KWikSync leverages ServiceNow's IntegrationHub ETL framework:

| Component | Purpose |
|-----------|---------|
| **Extract** | Pull data from external sources |
| **Transform** | Apply field mapping and validation |
| **Load** | Insert/update KWikSync tables |

**Requirements:**
- IntegrationHub ETL license
- Configured data sources
- Field mapping rules

### REST API

KWikSync exposes REST endpoints for programmatic access:

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/x_kwr_kwiksync/sync` | POST | Trigger manual sync |
| `/api/x_kwr_kwiksync/status` | GET | Get sync status |
| `/api/x_kwr_kwiksync/records/{table}` | GET | Retrieve records |

---

## Data Flow

### Inbound Sync (External  ServiceNow)

1. **Trigger** - Scheduled job or manual initiation
2. **Extract** - Connect to external source, retrieve data
3. **Transform** - Apply field mapping, validate data
4. **Load** - Create or update records in KWikSync tables
5. **Log** - Record operation in Sync Log

### Outbound Sync (ServiceNow  External)

1. **Detect** - Identify changed records
2. **Extract** - Gather modified data
3. **Transform** - Format for external system
4. **Push** - Send to external endpoint
5. **Confirm** - Verify successful delivery

---

## Authentication

### Customer Key Authentication

KWikSync uses Customer Key authentication:

1. Customer Key issued by KW Corporation
2. Key stored securely in Connection Settings
3. Key included in all sync operations
4. Keys can be rotated on request

### Security

- All data transmitted via HTTPS
- Keys encrypted at rest
- Access controlled via ACLs
- Full audit trail maintained

---

## Data Tables

### Core Tables

| Table | API Name | Description |
|-------|----------|-------------|
| Configuration | `x_kwr_kwiksync_configuration` | App settings |
| Projects | `x_kwr_kwiksync_projects` | Project records |
| Tickets | `x_kwr_kwiksync_tickets` | Work orders |
| Tasks | `x_kwr_kwiksync_kw_corp_ticket_tasks` | Task records |
| Assets | `x_kwr_kwiksync_assets` | Inventory |
| Locations | `x_kwr_kwiksync_locations` | Sites/facilities |
| Deliverables | `x_kwr_kwiksync_deliverables` | Project deliverables |

### System Tables

| Table | API Name | Description |
|-------|----------|-------------|
| Sync Log | `x_kwr_kwiksync_sync_log` | Operation history |
| Field Mapping | `x_kwr_kwiksync_field_mapping` | Mapping config |
| Error Log | `x_kwr_kwiksync_error_log` | Error tracking |

---

## Error Handling

### Retry Logic

Failed operations are automatically retried:

| Attempt | Delay |
|---------|-------|
| 1st retry | 1 minute |
| 2nd retry | 5 minutes |
| 3rd retry | 15 minutes |
| Final | Logged as failed |

### Error Logging

All errors are captured in the Error Log with:
- Timestamp
- Error code
- Error message
- Affected record
- Stack trace (if applicable)

---

## Rate Limiting

To ensure system stability:

| Limit | Value |
|-------|-------|
| API calls per minute | 60 |
| Records per sync batch | 1000 |
| Concurrent syncs | 1 |

---

## Best Practices

1. **Schedule wisely** - Run syncs during off-peak hours
2. **Monitor logs** - Review Sync Log and Error Log regularly
3. **Test changes** - Use test environments for field mapping changes
4. **Incremental sync** - Sync only changed records when possible
5. **Error alerts** - Configure notifications for sync failures

---

## Related Documentation

- [Field Mapping Reference](field-mapping.md)
- [Administrator Guide](../guides/admin-guide.md)
- [Troubleshooting](../guides/troubleshooting.md)

---

[ Back to Documentation](../README.md)
