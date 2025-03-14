---
title: 'Tutorial: Azure Active Directory single sign-on (SSO) integration with Facebook Work Accounts | Microsoft Docs'
description: Learn how to configure single sign-on between Azure Active Directory and Facebook Work Accounts.
services: active-directory
author: jeevansd
manager: CelesteDG
ms.reviewer: CelesteDG
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: tutorial
ms.date: 09/03/2021
ms.author: jeedes

---

# Tutorial: Azure Active Directory single sign-on (SSO) integration with Facebook Work Accounts

In this tutorial, you'll learn how to integrate Facebook Work Accounts with Azure Active Directory (Azure AD). When you integrate Facebook Work Accounts with Azure AD, you can:

* Control in Azure AD who has access to Facebook Work Accounts.
* Enable your users to be automatically signed-in to Facebook Work Accounts with their Azure AD accounts.
* Manage your accounts in one central location - the Azure portal.

## Prerequisites

To get started, you need the following items:

* An Azure AD subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/free/).
* Facebook Work Accounts single sign-on (SSO) enabled subscription.

## Scenario description

In this tutorial, you configure and test Azure AD SSO in a test environment.

* Facebook Work Accounts supports **SP and IDP** initiated SSO.

## Add Facebook Work Accounts from the gallery

To configure the integration of Facebook Work Accounts into Azure AD, you need to add Facebook Work Accounts from the gallery to your list of managed SaaS apps.

1. Sign in to the Azure portal using either a work or school account, or a personal Microsoft account.
1. On the left navigation pane, select the **Azure Active Directory** service.
1. Navigate to **Enterprise Applications** and then select **All Applications**.
1. To add new application, select **New application**.
1. In the **Add from the gallery** section, type **Facebook Work Accounts** in the search box.
1. Select **Facebook Work Accounts** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

## Configure and test Azure AD SSO for Facebook Work Accounts

Configure and test Azure AD SSO with Facebook Work Accounts using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between an Azure AD user and the related user in Facebook Work Accounts.

To configure and test Azure AD SSO with Facebook Work Accounts, perform the following steps:

1. **[Configure Azure AD SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **[Create an Azure AD test user](#create-an-azure-ad-test-user)** - to test Azure AD single sign-on with B.Simon.
    1. **[Assign the Azure AD test user](#assign-the-azure-ad-test-user)** - to enable B.Simon to use Azure AD single sign-on.
1. **[Configure Facebook Work Accounts SSO](#configure-facebook-work-accounts-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Facebook Work Accounts test user](#create-facebook-work-accounts-test-user)** - to have a counterpart of B.Simon in Facebook Work Accounts that is linked to the Azure AD representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Azure AD SSO

Follow these steps to enable Azure AD SSO in the Azure portal.

1. In the Azure portal, on the **Facebook Work Accounts** application integration page, find the **Manage** section and select **single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, click the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, perform the following steps:

    a. In the **Identifier** text box, type a URL using the following pattern:
    `https://work.facebook.com/company/<ID>`

    b. In the **Reply URL** text box, type a URL using the following pattern:
    ` https://work.facebook.com/work/saml.php?__cid=<ID>`

1. Click **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

    In the **Sign-on URL** text box, type the URL:
    `https://work.facebook.com`

	> [!NOTE]
	> These values are not real. Update these values with the actual Identifier and Reply URL. Engage the [Work Accounts team](https://www.workplace.com/help/work) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Azure portal.

1. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section,  find **Certificate (Base64)** and select **Download** to download the certificate and save it on your computer.

	![The Certificate download link](common/certificatebase64.png)

1. On the **Set up Facebook Work Accounts** section, copy the appropriate URL(s) based on your requirement.

	![Copy configuration URLs](common/copy-configuration-urls.png)

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

In this section, you'll enable B.Simon to use Azure single sign-on by granting access to Facebook Work Accounts.

1. In the Azure portal, select **Enterprise Applications**, and then select **All applications**.
1. In the applications list, select **Facebook Work Accounts**.
1. In the app's overview page, find the **Manage** section and select **Users and groups**.
1. Select **Add user**, then select **Users and groups** in the **Add Assignment** dialog.
1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then click the **Select** button at the bottom of the screen.
1. If you are expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
1. In the **Add Assignment** dialog, click the **Assign** button.

## Configure Facebook Work Accounts SSO

1. Log in to your Facebook Work Accounts company site as an administrator.

1. Go to **Security** > **Single Sign-On**.

1. Enable **Single-sign on(SSO)** checkbox and click **+Add new SSO Provider**.

    ![Screenshot shows the SSO Account.](./media/facebook-work-accounts-tutorial/security.png "SSO Account")

1. On the **Single Sign-On (SSO) Setup** page, perform the following steps:

    ![Screenshot shows the SSO Configuration.](./media/facebook-work-accounts-tutorial/certificate.png "Configuration")

    1. Enter a valid **Name of the SSO Provider**.

    1. In the **SAML URL** textbox, paste the **Login URL** value which you have copied from the Azure portal.

    1. In the **SAML Issuer URL** textbox, paste the **Azure AD Identifier** value which you have copied from the Azure portal.

    1. **Enable SAML logout redirection** checkbox and in the **SAML Logout URL** textbox, paste the **Logout URL** value which you have copied from the Azure portal.

    1. Open the downloaded **Certificate (Base64)** from the Azure portal into Notepad and paste the content into the **SAML Certificate** textbox.

    1. Copy **Audience URL** value, paste this value into the **Identifier** textbox in the **Basic SAML Configuration** section in the Azure portal.

    1. Copy **ACS (Assertion Consumer Service) URL** value, paste this value into the **Reply URL** text box in the **Basic SAML Configuration** section in the Azure portal.

    1. In the **Test SSO Setup** section, enter a valid email in the textbox and click **Test SSO**.

    1. Click **Save Changes**.

### Create Facebook Work Accounts test user

In this section, you create a user called Britta Simon in Facebook Work Accounts. Work with the [Work Accounts team](https://www.workplace.com/help/work) to add the users in the Facebook Work Accounts platform. Users must be created and activated before you use single sign-on.

## Test SSO 

In this section, you test your Azure AD single sign-on configuration with following options. 

#### SP initiated:

* Click on **Test this application** in Azure portal. This will redirect to Facebook Work Accounts Sign on URL where you can initiate the login flow.  

* Go to Facebook Work Accounts Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

* Click on **Test this application** in Azure portal and you should be automatically signed in to the Facebook Work Accounts for which you set up the SSO. 

You can also use Microsoft My Apps to test the application in any mode. When you click the Facebook Work Accounts tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Facebook Work Accounts for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](../user-help/my-apps-portal-end-user-access.md).

## Next steps

Once you configure Facebook Work Accounts you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-aad).
