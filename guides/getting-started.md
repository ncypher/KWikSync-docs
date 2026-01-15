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

### Option A: Private App Share (Recommended)

KWikSync is distributed as a private application through KW Corporation.

**Step 1: Request Access**
1. Contact KW Corporation at ServiceNowSupport@kw-corp.com
2. Provide your ServiceNow instance URL
3. You will receive an app share invitation

**Step 2: Accept the App Share**
1. Log in to your ServiceNow instance as an administrator
2. Navigate to **System Applications**  **My Company Applications**
3. Look for the pending KWikSync application share
4. Click **Accept** to add the app to your instance
5. Click **Install** to complete the installation

### Option B: Update Set Import

For instances without app share access:

**Step 1: Obtain Update Set**
1. Contact KW Corporation for the KWikSync Update Set file
2. You will receive an XML file via secure transfer

**Step 2: Import Update Set**
1. Navigate to **System Update Sets**  **Retrieved Update Sets**
2. Click **Import Update Set from XML**
3. Select the KWikSync XML file
4. Click **Upload**

**Step 3: Preview and Commit**
1. Open the imported Update Set
2. Click **Preview Update Set**
3. Review any conflicts or issues
4. Click **Commit Update Set**

### Step 3: Verify Installation

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

1. Navigate to **KWikSync**  **Settings**  **Connection Settings**
2. Enter your **Customer Key** (provided by KW Corporation)
3. Configure sync schedule preferences
4. Click **Save**
5. Click **Test Connection** to verify

---

## First Sync

Once configured, you're ready to run your first synchronization:

1. Navigate to **KWikSync**  **KWikSync Hub** (the home page)
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
