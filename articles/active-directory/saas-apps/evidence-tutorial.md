---
title: 'Tutorial: Azure Active Directory integration with Evidence.com'
description: Learn how to configure single sign-on between Azure Active Directory and Evidence.com.
services: active-directory
author: jeevansd
manager: CelesteDG
ms.reviewer: celested
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: tutorial
ms.date: 04/03/2023
ms.author: jeedes
---

# Tutorial: Azure Active Directory single sign-on (SSO) integration with Evidence.com

In this tutorial, you'll learn how to integrate Evidence.com with Azure Active Directory (Azure AD). When you integrate Evidence.com with Azure AD, you can:

* Control in Azure AD who has access to Evidence.com.
* Enable your users to be automatically signed-in to Evidence.com with their Azure AD accounts.
* Manage your accounts in one central location - the Azure portal.

## Prerequisites

To get started, you need the following items:

* An Azure AD subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/free/).
* Evidence.com single sign-on (SSO) enabled subscription.

## Scenario description

In this tutorial, you configure and test Azure AD SSO in a test environment.

* Evidence.com supports **SP** initiated SSO.

## Add Evidence.com from the gallery

To configure the integration of Evidence.com into Azure AD, you need to add Evidence.com from the gallery to your list of managed SaaS apps.

1. Sign in to the Azure portal using either a work or school account, or a personal Microsoft account.
1. On the left navigation pane, select the **Azure Active Directory** service.
1. Navigate to **Enterprise Applications** and then select **All Applications**.
1. To add new application, select **New application**.
1. In the **Add from the gallery** section, type **Evidence.com** in the search box.
1. Select **Evidence.com** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

 Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, as well as walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Azure AD SSO for Evidence.com

Configure and test Azure AD SSO with Evidence.com using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between an Azure AD user and the related user in Evidence.com.

To configure and test Azure AD SSO with Evidence.com, perform the following steps:

1. **[Configure Azure AD SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.
    1. **[Create an Azure AD test user](#create-an-azure-ad-test-user)** - to test Azure AD single sign-on with B.Simon.
    1. **[Assign the Azure AD test user](#assign-the-azure-ad-test-user)** - to enable B.Simon to use Azure AD single sign-on.
1. **[Configure Evidence.com SSO](#configure-evidencecom-sso)** - to configure the single sign-on settings on application side.
    1. **[Create Evidence.com test user](#create-evidencecom-test-user)** - to have a counterpart of B.Simon in Evidence.com that is linked to the Azure AD representation of user.
1. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Azure AD SSO

Follow these steps to enable Azure AD SSO in the Azure portal.

1. In the Azure portal, on the **Evidence.com** application integration page, find the **Manage** section and select **single sign-on**.
1. On the **Select a single sign-on method** page, select **SAML**.
1. On the **Set up single sign-on with SAML** page, click the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](common/edit-urls.png)

1. On the **Set up single sign-on with SAML** page, perform the following steps:

    1. In the **Sign on URL** text box, type a URL using the following pattern:
    `https://<yourtenant>.evidence.com`

    1. In the **Identifier (Entity ID)** text box, type a URL using the following pattern:
    `https://<yourtenant>.evidence.com`

    1. In the **Reply URL** textbox, type a URL using the following pattern: 
    `https://<your tenant>.evidence.com/?class=UIX&proc=Login`

    > [!NOTE]
    > These values are not real. Update these values with the actual Sign on URL, Identifier and Reply URL. Contact [Evidence.com Client support team](https://my.axon.com/s/contactsupport) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Azure portal.

5. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, click **Download** to download the **Certificate (Base64)** from the given options as per your requirement and save it on your computer.

    ![The Certificate download link](common/certificatebase64.png)

1. On the **Set up Evidence.com** section, copy the appropriate URL(s) based on your requirement.

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

In this section, you'll enable B.Simon to use Azure single sign-on by granting access to Evidence.com.

1. In the Azure portal, select **Enterprise Applications**, and then select **All applications**.
1. In the applications list, select **Evidence.com**.
1. In the app's overview page, find the **Manage** section and select **Users and groups**.
1. Select **Add user**, then select **Users and groups** in the **Add Assignment** dialog.
1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then click the **Select** button at the bottom of the screen.
1. If you are expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
1. In the **Add Assignment** dialog, click the **Assign** button.

## Configure Evidence.com SSO

1. In a separate web browser window, sign into your Evidence.com tenant as an administrator and navigate to **Admin** Tab.

2. Click on **Agency Single Sign On**.

3. Select **SAML Based Single Sign On**.

4. Copy the **Azure AD Identifier**, **Login URL** and **Logout URL** values shown in the Azure portal and to the corresponding fields in Evidence.com.

5. Open your downloaded Certificate(Base64) file in notepad, copy the content of it into your clipboard, and then paste it to the **Security Certificate** box. 

6. Save the configuration in Evidence.com.

### Create Evidence.com test user

For Azure AD users to be able to sign in, they must be provisioned for access inside the Evidence.com application. This section describes how to create Azure AD user accounts inside Evidence.com.

**To provision a user account in Evidence.com:**

1. In a web browser window, sign into your Evidence.com company site as an administrator.

2. Navigate to **Admin** tab.

3. Click on **Add User**.

4. Click the **Add** button.

5. The **Email Address** of the added user must match the username of the users in Azure AD who you wish to give access. If the username and email address are not the same value in your organization, you can use the **Evidence.com > Attributes > Single Sign-On** section of the Azure portal to change the nameidenitifer sent to Evidence.com to be the email address.

## Test SSO 

In this section, you test your Azure AD single sign-on configuration with following options. 

* Click on **Test this application** in Azure portal. This will redirect to Evidence.com Sign-on URL where you can initiate the login flow. 

* Go to Evidence.com Sign-on URL directly and initiate the login flow from there.

* You can use Microsoft My Apps. When you click the Evidence.com tile in the My Apps, this will redirect to Evidence.com Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Next steps

Once you configure Evidence.com you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](/cloud-app-security/proxy-deployment-aad).
