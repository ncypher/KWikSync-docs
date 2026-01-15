# Field Mapping Reference

[ Back to Documentation](../README.md)

---

## Overview

Field mapping defines how data translates between external systems and KWikSync tables. This reference covers the mapping configuration and available options.

---

## How Field Mapping Works

\\\
External Field    Transform Rule    KWikSync Field

project_name       Direct Copy        name
status_code        Value Map          state
created_date       Date Format        sys_created_on
\\\

---

## Mapping Configuration

### Accessing Field Mapping

1. Navigate to **KWikSync**  **Field Mapping**
2. Requires `x_kwr_kwiksync.admin` role
3. View existing mappings or create new ones

### Mapping Record Fields

| Field | Description |
|-------|-------------|
| **Source Table** | External data table name |
| **Source Field** | External field name |
| **Target Table** | KWikSync table name |
| **Target Field** | KWikSync field name |
| **Transform Type** | How to transform the value |
| **Transform Config** | Additional transformation settings |
| **Active** | Enable/disable this mapping |

---

## Transform Types

### Direct Copy

Copies the value without modification.

| Setting | Value |
|---------|-------|
| Transform Type | `direct` |
| Use Case | Text fields, IDs, simple values |

**Example:**
\\\
Source: customer_name = "Acme Corp"
Target: name = "Acme Corp"
\\\

---

### Value Map

Maps source values to target values using a lookup table.

| Setting | Value |
|---------|-------|
| Transform Type | `value_map` |
| Use Case | Status codes, categories, enums |

**Example Configuration:**
\\\json
{
  "mappings": {
    "OPEN": "1",
    "IN_PROGRESS": "2",
    "CLOSED": "3"
  },
  "default": "1"
}
\\\

**Result:**
\\\
Source: status = "IN_PROGRESS"
Target: state = "2"
\\\

---

### Date Format

Converts date formats between systems.

| Setting | Value |
|---------|-------|
| Transform Type | `date_format` |
| Use Case | Date fields with different formats |

**Example Configuration:**
\\\json
{
  "source_format": "MM/DD/YYYY",
  "target_format": "YYYY-MM-DD"
}
\\\

**Result:**
\\\
Source: created = "01/15/2026"
Target: sys_created_on = "2026-01-15"
\\\

---

### Concatenate

Combines multiple fields into one.

| Setting | Value |
|---------|-------|
| Transform Type | `concatenate` |
| Use Case | Building full names, addresses |

**Example Configuration:**
\\\json
{
  "fields": ["first_name", "last_name"],
  "separator": " "
}
\\\

**Result:**
\\\
Source: first_name = "John", last_name = "Smith"
Target: full_name = "John Smith"
\\\

---

### Lookup

References another table to get a value.

| Setting | Value |
|---------|-------|
| Transform Type | `lookup` |
| Use Case | Reference fields, foreign keys |

**Example Configuration:**
\\\json
{
  "lookup_table": "x_kwr_kwiksync_locations",
  "match_field": "external_id",
  "return_field": "sys_id"
}
\\\

---

### Script

Custom JavaScript transformation for complex logic.

| Setting | Value |
|---------|-------|
| Transform Type | `script` |
| Use Case | Complex business logic |

**Example Configuration:**
\\\javascript
// Transform script
(function(value, record) {
    if (value > 100) {
        return 'High';
    } else if (value > 50) {
        return 'Medium';
    }
    return 'Low';
})(value, record);
\\\

---

## Table Mapping Reference

### Projects Table

| Source Field | Target Field | Transform |
|--------------|--------------|-----------|
| project_id | external_id | Direct |
| project_name | name | Direct |
| status | state | Value Map |
| start_date | start_date | Date Format |
| end_date | end_date | Date Format |
| customer_id | customer | Lookup |

### Tickets Table

| Source Field | Target Field | Transform |
|--------------|--------------|-----------|
| ticket_id | external_id | Direct |
| ticket_number | number | Direct |
| description | short_description | Direct |
| priority | priority | Value Map |
| assigned_to | assigned_to | Lookup |
| project_id | project | Lookup |
| location_id | location | Lookup |

### Assets Table

| Source Field | Target Field | Transform |
|--------------|--------------|-----------|
| asset_id | external_id | Direct |
| asset_tag | asset_tag | Direct |
| description | name | Direct |
| quantity | quantity | Direct |
| location_id | location | Lookup |
| category | category | Value Map |

### Locations Table

| Source Field | Target Field | Transform |
|--------------|--------------|-----------|
| location_id | external_id | Direct |
| location_name | name | Direct |
| address | street | Direct |
| city | city | Direct |
| state | state | Direct |
| zip | zip | Direct |
| country | country | Direct |

---

## Validation Rules

Field mapping includes built-in validation:

| Rule | Description |
|------|-------------|
| **Required** | Field must have a value |
| **Format** | Value must match expected format |
| **Length** | Value must be within length limits |
| **Range** | Numeric value must be in range |
| **Reference** | Referenced record must exist |

---

## Best Practices

1. **Document mappings** - Keep notes on why specific mappings were chosen
2. **Test thoroughly** - Verify mappings in a test environment first
3. **Handle nulls** - Define behavior for missing values
4. **Use defaults** - Set sensible defaults for optional fields
5. **Version control** - Track mapping changes over time

---

## Troubleshooting Mappings

### Common Issues

| Issue | Cause | Solution |
|-------|-------|----------|
| Data not syncing | Inactive mapping | Enable the mapping |
| Wrong values | Incorrect value map | Update mapping config |
| Date errors | Format mismatch | Check date format config |
| Missing records | Lookup failure | Verify lookup configuration |

### Debugging

1. Check Error Log for mapping-specific errors
2. Review Sync Log for failed records
3. Test transformations with sample data
4. Enable debug logging if available

---

## Related Documentation

- [Integration Overview](integration-overview.md)
- [Administrator Guide](../guides/admin-guide.md)
- [Troubleshooting](../guides/troubleshooting.md)

---

[ Back to Documentation](../README.md)
