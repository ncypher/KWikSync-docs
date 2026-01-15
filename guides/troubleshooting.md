# Troubleshooting Guide

[ Back to Documentation](../README.md)

---

## Overview

This guide helps you diagnose and resolve common issues with KWikSync. If your issue isn't covered here, contact support at ServiceNowSupport@kw-corp.com.

---

## Quick Diagnostics

### Check Sync Status

1. Navigate to **KWikSync**  **KWikSync Hub**
2. Check the sync status indicator
3. Review last sync timestamp

### Check Error Log

1. Navigate to **KWikSync**  **Error Log**
2. Filter for recent errors
3. Note error codes and messages

---

## Common Issues

### Sync Not Running

**Symptoms:**
- Data not updating
- Sync status shows "Not Running"
- Last sync timestamp is old

**Solutions:**

| Check | Action |
|-------|--------|
| Customer Key | Verify key in Connection Settings |
| Sync Schedule | Confirm schedule is enabled |
| IntegrationHub | Verify ETL license is active |
| Network | Check firewall and proxy settings |

**Steps:**
1. Navigate to **KWikSync**  **Connection Settings**
2. Verify Customer Key is entered correctly
3. Click **Test Connection**
4. If test fails, contact KW Corporation for key verification

---

### Access Denied Errors

**Symptoms:**
- "Access denied" message
- Unable to view dashboards
- Unable to modify records

**Solutions:**

| Issue | Resolution |
|-------|------------|
| Missing role | Assign `x_kwr_kwiksync.user` role |
| Admin features blocked | Assign `x_kwr_kwiksync.admin` role |
| ACL conflict | Contact ServiceNow admin |

**Steps:**
1. Navigate to **User Administration**  **Users**
2. Open your user record
3. Check the **Roles** related list
4. Add the appropriate KWikSync role if missing

---

### Dashboard Not Loading

**Symptoms:**
- Blank dashboard
- Loading spinner doesn't stop
- Error message displayed

**Solutions:**

| Cause | Fix |
|-------|-----|
| Browser cache | Clear cache and refresh |
| JavaScript error | Check browser console (F12) |
| Missing role | Verify role assignment |
| Theme conflict | Try switching themes |

**Steps:**
1. Press **Ctrl+Shift+Delete** to clear browser cache
2. Refresh the page
3. If issue persists, try a different browser
4. Check browser console (F12) for JavaScript errors

---

### Missing Data After Sync

**Symptoms:**
- Records not appearing
- Data seems incomplete
- Counts don't match source

**Solutions:**

| Cause | Fix |
|-------|-----|
| Filter applied | Clear dashboard filters |
| Sync in progress | Wait for sync to complete |
| Field mapping | Review field mapping configuration |
| Sync error | Check Error Log for failures |

**Steps:**
1. Clear any active filters on the dashboard
2. Navigate to **KWikSync**  **Sync Log**
3. Verify last sync completed successfully
4. Check **Error Log** for failed records

---

### Slow Performance

**Symptoms:**
- Dashboards load slowly
- Sync takes too long
- Timeouts occurring

**Solutions:**

| Cause | Fix |
|-------|-----|
| Large dataset | Use filters to limit results |
| Concurrent syncs | Schedule syncs during off-peak |
| Network latency | Check network connectivity |
| Browser resources | Close unnecessary tabs |

**Steps:**
1. Apply filters to reduce displayed records
2. Check if multiple syncs are running simultaneously
3. Review sync duration trends in Sync Log
4. Contact your IT team for network assessment

---

### Sync Conflicts

**Symptoms:**
- Duplicate records
- Overwritten data
- Inconsistent values

**Solutions:**

| Cause | Fix |
|-------|-----|
| Bidirectional conflict | Review conflict resolution settings |
| Duplicate keys | Check for duplicate external IDs |
| Timing issue | Adjust sync schedule |

**Steps:**
1. Navigate to **KWikSync**  **Error Log**
2. Look for conflict warnings
3. Review the affected records in both systems
4. Contact support if conflicts persist

---

## Error Codes Reference

| Code | Description | Resolution |
|------|-------------|------------|
| ERR_001 | Invalid Customer Key | Verify key in Connection Settings |
| ERR_002 | Connection timeout | Check network connectivity |
| ERR_003 | Authentication failed | Refresh Customer Key |
| ERR_004 | Field mapping error | Review field mapping configuration |
| ERR_005 | Duplicate record | Check for duplicate external IDs |
| ERR_006 | Missing required field | Ensure all required fields are mapped |
| ERR_007 | Rate limit exceeded | Reduce sync frequency |
| ERR_008 | Data validation failed | Review data format in source |

---

## Diagnostic Tools

### Sync Log

Location: **KWikSync**  **Sync Log**

Use for:
- Viewing sync history
- Checking sync duration
- Identifying patterns

### Error Log

Location: **KWikSync**  **Error Log**

Use for:
- Viewing error details
- Identifying failed records
- Troubleshooting specific issues

### System Logs

Location: **System Logs**  **Application Logs**

Filter by: `x_kwr_kwiksync`

Use for:
- Detailed technical debugging
- Script errors
- API issues

---

## Still Need Help?

If you've tried the above solutions and still have issues:

### Contact Support

- **Email**: ServiceNowSupport@kw-corp.com
- **Hours**: Monday - Friday, 8 AM - 6 PM EST

### Information to Include

When contacting support, please provide:

1. **Description** of the issue
2. **Steps to reproduce**
3. **Error messages** (exact text or screenshots)
4. **Sync Log** entries from the time of issue
5. **Error Log** entries if applicable
6. **Browser** and version
7. **ServiceNow instance** version

---

## Related Guides

-  [Getting Started](getting-started.md) - Installation and setup
-  [User Guide](user-guide.md) - Feature overview
-  [Administrator Guide](admin-guide.md) - Advanced configuration

---

[ Back to Documentation](../README.md)
