> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Single Sign-On (SSO)

> Configure Enterprise Single Sign-On for your organization through domain verification and identity provider setup

Blitzy supports Enterprise Single Sign-On (SSO), allowing your organization to authenticate users through your existing Identity Provider (IdP) - Okta, Microsoft Entra ID, Google Workspace, or any other SAML-compatible provider.

> [!NOTE]
>
> **Jump to:** [Before You Begin](#before-you-begin) | [Domain Verification](#step-1-domain-verification) | [IdP Configuration](#step-2-identity-provider-idp-configuration) | [SCIM Provisioning](#idp-managed-provisioning-scim-20) | [Troubleshooting](#troubleshooting)

Setting up SSO requires two steps, typically performed by two different administrators:

| Step | Who performs it | What it involves |
| - | - | - |
| [1. Domain Verification](#step-1-domain-verification) | DNS Administrator | Adding a TXT record to your DNS settings |
| [2. Identity Provider Configuration](#step-2-identity-provider-idp-configuration) | Security / IT Administrator | Granting Blitzy access to your IdP |

> [!NOTE]
>
> **Already signing in with Microsoft?** No action required. The SSO setup below adds stronger security and a seamless login experience.

## Before You Begin

* **Super Admin access** - Required in Blitzy to initiate the setup
* **DNS Administrator** - Needed for Step 1 to add a record to your domain's DNS settings. This is a minor, non-disruptive change.
* **Security or IT Administrator** - Needed for Step 2 to configure your Identity Provider

## Step 1: Domain Verification

Domain verification proves to Blitzy that your organization owns the domain used for employee email addresses (e.g., `yourcompany.com`). This is a one-time step performed by your DNS Administrator.

**1. Open Authentication Settings**

Navigate to **Settings** by clicking the **gear icon** in the top-right corner of your workspace. Select the **Authentication** tab.

**2. Start Domain Verification**

In the **Domain Verification** section, click **Verify**.

> [!NOTE]
>
> This step should be performed by a Super Admin.

![The Blitzy Settings page with the Authentication tab selected, showing the Domain Verification section and Verify button](https://mintcdn.com/blitzy-c2eefe5a/aSqbecWObkFpnh9C/images/sso-auth-settings.png?fit=max\&auto=format\&n=aSqbecWObkFpnh9C\&q=85\&s=5a6cc7b2bdef0095e445e0b1f3b5d53e)

**3. Enter Your Domain and Add the DNS Record**

Enter your organization's domain. Blitzy generates a **TXT record** that your DNS Administrator must add to your domain's DNS settings.

Provide this TXT record to your DNS Administrator. They will add it in your DNS provider's control panel (e.g., Cloudflare, Route 53, GoDaddy).

![The domain entry prompt showing the organization domain field](https://mintcdn.com/blitzy-c2eefe5a/aSqbecWObkFpnh9C/images/sso-domain-entry.png?fit=max\&auto=format\&n=aSqbecWObkFpnh9C\&q=85\&s=39e5e8a57c2732cba632ed6efc0b772e)

**4. Wait for Verification**

DNS propagation can take up to **48 hours**. The verification process runs automatically in the background - no action is needed during this time.

![The DNS record details and verification pending state](https://mintcdn.com/blitzy-c2eefe5a/aSqbecWObkFpnh9C/images/sso-dns-record.png?fit=max\&auto=format\&n=aSqbecWObkFpnh9C\&q=85\&s=47f9da3ba9ee68844fa5408cebda246c)

**5. Confirm Verified Domain**

Once validated, a success message appears. Return to the Blitzy platform to confirm the domain shows as verified.

![The Domain Verification success state confirming the domain has been verified](https://mintcdn.com/blitzy-c2eefe5a/aSqbecWObkFpnh9C/images/sso-domain-verified.png?fit=max\&auto=format\&n=aSqbecWObkFpnh9C\&q=85\&s=4d6e189fd589f29941907431b4304248)

## Step 2: Identity Provider (IdP) Configuration

Once your domain is verified, a Security or IT Administrator can connect your Identity Provider to enable SSO login for your organization.

**1. Open the SSO Configuration**

From the **Authentication** settings page, click **Configure** in the Single Sign-On section.

![The Authentication settings page showing the Configure button for SSO setup](https://mintcdn.com/blitzy-c2eefe5a/aSqbecWObkFpnh9C/images/sso-configure-button.png?fit=max\&auto=format\&n=aSqbecWObkFpnh9C\&q=85\&s=6573a34fb7c2811b5e4e6ff44d29201d)

**2. Select Your Identity Provider**

Choose your organization's Identity Provider from the list. Supported providers include Okta, Microsoft Entra ID (Azure AD), Google Workspace, OneLogin, and others.

After selecting your provider, Blitzy displays setup instructions tailored to that specific IdP.

![The Identity Provider selection screen showing available provider options](https://mintcdn.com/blitzy-c2eefe5a/aSqbecWObkFpnh9C/images/sso-select-provider.png?fit=max\&auto=format\&n=aSqbecWObkFpnh9C\&q=85\&s=0914bd8613b83e7174eb3b96d73021c6)

**3. Complete the IdP Setup**

Follow the step-by-step instructions shown on screen. These instructions are specific to your chosen provider and walk you and your IdP administrator through all required configuration steps.

> [!TIP]
>
> Keep Blitzy and your IdP's admin console open in separate browser tabs - you will be copying values between them.

![The step-by-step IdP configuration instructions for the selected provider](https://mintcdn.com/blitzy-c2eefe5a/aSqbecWObkFpnh9C/images/sso-idp-setup-steps.png?fit=max\&auto=format\&n=aSqbecWObkFpnh9C\&q=85\&s=1875d9db898666c520da554d11029741)

**4. Test the Connection**

After completing the configuration, use the **Test Connection** option to verify SSO is working correctly before rolling it out to your organization.

![The Test Connection success screen at the end of the SSO setup flow](https://mintcdn.com/blitzy-c2eefe5a/aSqbecWObkFpnh9C/images/sso-test-connection.png?fit=max\&auto=format\&n=aSqbecWObkFpnh9C\&q=85\&s=4bcf4258b6ed350cc71b796b9fb7e8b7)

**5. Confirm SSO Status**

Return to the **Authentication** settings page. The updated status confirms SSO is active.

![The Authentication settings page showing the SSO connection as active](https://mintcdn.com/blitzy-c2eefe5a/aSqbecWObkFpnh9C/images/sso-connected-status.png?fit=max\&auto=format\&n=aSqbecWObkFpnh9C\&q=85\&s=e53faccdeb28e96e72ebc4bb004efc1b)

## Troubleshooting

> **Domain verification is taking longer than expected**
>
> DNS propagation can take up to 48 hours depending on your DNS provider and TTL settings. If verification has not completed after 48 hours, confirm the TXT record was added correctly and contact [support@blitzy.com](mailto:support@blitzy.com).

> **Identity Provider not listed**
>
> Blitzy supports any SAML 2.0-compatible Identity Provider. If your provider is not listed, select **Custom SAML** and follow the instructions, or reach out to [support@blitzy.com](mailto:support@blitzy.com) for assistance.

> **SSO test is failing**
>
> Double-check that all values (ACS URL, Entity ID, etc.) were copied accurately between Blitzy and your IdP. Even a small typo causes the connection to fail. If the issue persists, contact your IdP administrator or reach out to Blitzy support.

### Getting Help

Contact [support@blitzy.com](mailto:support@blitzy.com) or reach out to your Blitzy account representative.

## IdP-Managed Provisioning (SCIM 2.0)

SCIM directory sync brings your identity provider's groups into Blitzy through WorkOS. The separate **IdP-managed mode** toggle controls whether Blitzy continuously enforces mapped teams and roles.

### How It Works

Both modes use the same group mapping table. Role priority is **Super Admin**, then **Admin**, then **Member**, then **Viewer** - the highest matching role wins.

| Behavior | IdP-managed mode off | IdP-managed mode on |
| - | - | - |
| **Team placement** | New users join the default team, regardless of the mapping's selected team | Users join all mapped teams |
| **Roles** | Highest matching role at first login; managed manually afterward | Highest matching role per team, continuously enforced |
| **Team page** | Teams, memberships, and roles are editable | Existing team and member edits are locked; team creation is allowed |
| **IdP group changes** | Checked at login; existing memberships and roles stay unchanged | Memberships and roles update on sync and login |

Super Admin access applies across the org.

> [!TIP]
>
> IdP changes are not instant. Updates take effect after the next directory sync or user login. See the **IdP group changes** row in the [behavior table](#how-it-works) for details per mode.

> [!NOTE]
>
> Member and Admin mappings need a team selected in either mode. A row showing **Member** or **Admin** without a team is **Unmapped** and grants no initial access.

### First Login and Access Removal

With IdP-managed mode **off**, the Blitzy account is created on the user's first SSO login, not on directory sync. A matching access-granting mapping is required; otherwise, login is denied and no account is created.

Removing a user from one IdP group while they remain in others has no effect - existing team memberships and roles stay unchanged. Removing a user from every mapped group blocks their next login but leaves their account and team memberships in place.

With IdP-managed mode **on**, access follows the user's remaining mappings.

Removing a user from one group drops them from the corresponding team at the next sync. Losing all mapped access removes their team memberships but retains their individual Blitzy account.

### Changing Modes

Turning IdP-managed mode **on** applies mappings to existing users and overwrites any manual role or team changes. Turning it **off** preserves current assignments and unlocks the Team page. Directory sync stays active; earlier assignments are not restored.

### Setup

**1. Connect your directory**

In **Settings > Authentication**, select **SCIM directory sync** under **User provisioning**. Click **Configure** under **Directory connection** to open the WorkOS Admin Portal. Follow its instructions to connect your IdP and enable group push.

**2. Map groups to teams and roles**

Return to Blitzy. Assign a role to each synced group that should grant access. For Member and Admin roles, select a team as well - team placement applies when IdP-managed mode is on (in mode-off, new users join the default team regardless). Review unmapped rows.

**3. Choose and save the management mode**

Set **IdP-managed mode** using the [behavior comparison](#how-it-works). Before enabling it, ensure the mappings retain your Super Admin access and include everyone who needs access. Save and complete the confirmation shown.

**4. Verify access**

Test SSO login with a new user in a mapped group. Check **Settings > Teams** for the team placement and role matching your chosen mode in the [behavior table](#how-it-works).

> [!WARNING]
>
> SCIM provisioning requires SSO to be configured and active. Complete the [SSO setup](#step-1-domain-verification) before enabling SCIM.

> **[Teams & Roles](teams.md)**
>
> Manage teams and member access

> **[Environment Configuration](../../build_preparation/setup/environment_config.md)**
>
> Configure environments for code generation


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.