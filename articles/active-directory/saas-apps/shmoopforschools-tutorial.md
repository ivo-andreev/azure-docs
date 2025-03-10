---
title: "Tutorial: Azure Active Directory integration with Shmoop For Schools | Microsoft Docs"
description: Learn how to configure single sign-on between Azure Active Directory and Shmoop For Schools.
services: active-directory
author: jeevansd
manager: CelesteDG
ms.reviewer: celested
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: tutorial
ms.date: 12/18/2020
ms.author: jeedes
---

# Tutorial: Integrate Shmoop For Schools with Azure Active Directory

In this tutorial, you'll learn how to integrate Shmoop For Schools with Azure Active Directory (Azure AD). When you integrate Shmoop For Schools with Azure AD, you can:

- Control in Azure AD who has access to Shmoop For Schools.
- Enable your users to be automatically signed-in to Shmoop For Schools with their Azure AD accounts.
- Manage your accounts in one central location - the Azure portal.

## Prerequisites

To get started, you need the following items:

- An Azure AD subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/free/).
- Shmoop For Schools single sign-on (SSO) enabled subscription.

## Scenario description

In this tutorial, you configure and test Azure AD SSO in a test environment.

- Shmoop For Schools supports **SP** initiated SSO
- Shmoop For Schools supports **Just In Time** user provisioning

## Adding Shmoop For Schools from the gallery

To configure the integration of Shmoop For Schools into Azure AD, you need to add Shmoop For Schools from the gallery to your list of managed SaaS apps.

1. Sign in to the Azure portal using either a work or school account, or a personal Microsoft account.
1. On the left navigation pane, select the **Azure Active Directory** service.
1. Navigate to **Enterprise Applications** and then select **All Applications**.
1. To add new application, select **New application**.
1. In the **Add from the gallery** section, type **Shmoop For Schools** in the search box.
1. Select **Shmoop For Schools** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

## Configure and test Azure AD SSO for Shmoop For Schools

Configure and test Azure AD SSO with Shmoop For Schools using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between an Azure AD user and the related user in Shmoop For Schools.

To configure and test Azure AD SSO with Shmoop For Schools, perform the following steps:

1. **[Configure Azure AD SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
   1. **[Create an Azure AD test user](#create-an-azure-ad-test-user)** - to test Azure AD single sign-on with B.Simon.
   1. **[Assign the Azure AD test user](#assign-the-azure-ad-test-user)** - to enable B.Simon to use Azure AD single sign-on.
2. **[Configure Shmoop For Schools SSO](#configure-shmoop-for-schools-sso)** - to configure the Single Sign-On settings on application side.
   1. **[Create Shmoop For Schools test user](#create-shmoop-for-schools-test-user)** - to have a counterpart of B.Simon in Shmoop For Schools that is linked to the Azure AD representation of user.
3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Azure AD SSO

Follow these steps to enable Azure AD SSO in the Azure portal.

1. In the Azure portal, on the **Shmoop For Schools** application integration page, find the **Manage** section and select **Single sign-on**.
1. On the **Select a Single sign-on method** page, select **SAML**.
1. On the **Set up Single Sign-On with SAML** page, click the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Sign on URL** text box, type a URL using the following pattern:
   `https://schools.shmoop.com/public-api/saml2/start/<uniqueid>`

   b. In the **Identifier (Entity ID)** text box, type a URL using the following pattern:
   `https://schools.shmoop.com/<uniqueid>`

   > [!NOTE]
   > These values are not real. Update these values with the actual Sign on URL and Identifier. Contact [Shmoop For Schools Client support team](mailto:support@shmoop.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Azure portal.

1. Shmoop For Schools application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](common/default-attributes.png)

1. In addition to above, Shmoop For Schools application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.

   | Name | Source Attribute   |
   | ---- | ------------------ |
   | role | user.assignedroles |

   > [!NOTE]
   > Shmoop for School supports two roles for users: **Teacher** and **Student**. Set up these roles in Azure AD so that users can be assigned the appropriate roles. To understand how to configure roles in Azure AD, see [here](../develop/howto-add-app-roles-in-azure-ad-apps.md#app-roles-ui).

1. On the **Set up Single Sign-On with SAML** page, In the **SAML Signing Certificate** section, click copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](common/copy-metadataurl.png)

### Create an Azure AD test user

In this section, you'll create a test user in the Azure portal called B.Simon.

1. From the left pane in the Azure portal, select **Azure Active Directory**, select **Users**, and then select **All users**.
1. Select **New user** at the top of the screen.
1. In the **User** properties, follow these steps:
   1. In the **Name** field, enter `B.Simon`.
   1. In the **User name** field, enter the username@companydomain.extension. For example, `B.Simon@contoso.com`.
   1. Select the **Show password** check box, and then write down the value that's displayed in the **Password** box.
   1. Click **Create**.

### Assign the Azure AD test user

In this section, you'll enable B.Simon to use Azure single sign-on by granting access to Shmoop For Schools.

1. In the Azure portal, select **Enterprise Applications**, and then select **All applications**.
1. In the applications list, select **Shmoop For Schools**.
1. In the app's overview page, find the **Manage** section and select **Users and groups**.
1. Select **Add user**, then select **Users and groups** in the **Add Assignment** dialog.
1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then click the **Select** button at the bottom of the screen.
1. If you have setup the roles as explained in the above, you can select it from the **Select a role** dropdown.
1. In the **Add Assignment** dialog, click the **Assign** button.

## Configure Shmoop For Schools SSO

To configure single sign-on on **Shmoop For Schools** side, you need to send the **App Federation Metadata Url** to [Shmoop For Schools support team](mailto:support@shmoop.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Shmoop For Schools test user

In this section, a user called B.Simon is created in Shmoop For Schools. Shmoop For Schools supports just-in-time user provisioning, which is enabled by default. There is no action item for you in this section. If a user doesn't already exist in Shmoop For Schools, a new one is created after authentication.

> [!NOTE]
> If you need to create a user manually, contact the [Shmoop For Schools support team](mailto:support@shmoop.com).

## Test SSO

In this section, you test your Azure AD single sign-on configuration with following options.

- Click on **Test this application** in Azure portal. This will redirect to Shmoop For Schools Sign-on URL where you can initiate the login flow.

- Go to Shmoop For Schools Sign-on URL directly and initiate the login flow from there.

- You can use Microsoft My Apps. When you click the Shmoop For Schools tile in the My Apps, this will redirect to Shmoop For Schools Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Next steps

Once you configure Shmoop For Schools you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-any-app).
