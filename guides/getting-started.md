# Getting Started with KWikSync

[ Back to Documentation](../README.md)

---

## Overview

Welcome to KWikSync! This guide will walk you through the installation, initial configuration, and first steps to get your data synchronization up and running.

---

## Prerequisites

Before installing KWikSync, ensure you have:

| Requirement | Details |
|-------------|---------|
| **ServiceNow Instance** | Tokyo release or later |
| **IntegrationHub** | ETL license enabled |
| **Admin Access** | Required for installation |
| **Customer Key** | Provided by KW Corporation |

---

## Installation

### Step 1: Install from ServiceNow Store

1. Log in to your ServiceNow instance as an administrator
2. Navigate to **System Applications**  **All Available Applications**  **All**
3. Search for **KWikSync**
4. Click **Install**
5. Accept the license agreement
6. Wait for installation to complete (typically 2-3 minutes)

### Step 2: Verify Installation

After installation completes:

1. Navigate to the Application Navigator (left sidebar)
2. Type **KWikSync** in the filter
3. You should see the KWikSync menu with all modules

---

## Initial Configuration

### Assign Roles

KWikSync uses two roles for access control:

| Role | Description | Assign To |
|------|-------------|-----------|
| `x_kwr_kwiksync.admin` | Full administrative access | System administrators |
| `x_kwr_kwiksync.user` | Standard user access | End users, managers |

**To assign roles:**

1. Navigate to **User Administration**  **Users**
2. Open the user record
3. Scroll to the **Roles** related list
4. Click **Edit**
5. Add the appropriate KWikSync role
6. Click **Save**

### Configure Connection Settings

1. Navigate to **KWikSync**  **Connection Settings**
2. Enter your **Customer Key** (provided by KW Corporation)
3. Configure sync schedule preferences
4. Click **Save**
5. Click **Test Connection** to verify

---

## First Sync

Once configured, you're ready to run your first synchronization:

1. Navigate to **KWikSync**  **KWikSync Hub**
2. Review the dashboard status
3. Click **Sync Now** to initiate manual sync
4. Monitor progress in the Sync Log

---

## Next Steps

Now that KWikSync is installed and configured:

-  [User Guide](user-guide.md) - Learn about all features and dashboards
-  [Administrator Guide](admin-guide.md) - Advanced configuration options
-  [Training Video](../training/training-video.md) - Watch the full walkthrough

---

## Need Help?

- **Email**: ServiceNowSupport@kw-corp.com
- **Support Hours**: Monday - Friday, 8 AM - 6 PM EST

---

[ Back to Documentation](../README.md)
