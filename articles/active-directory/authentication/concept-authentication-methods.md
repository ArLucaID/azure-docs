---
title: Authentication methods and features
description: Learn about the different authentication methods and features available in Azure Active Directory to help improve and secure sign-in events

services: active-directory
ms.service: active-directory
ms.subservice: authentication
ms.topic: conceptual
ms.date: 06/07/2023

ms.author: justinha
author: justinha
manager: amycolannino

ms.collection: M365-identity-device-management
ms.custom: contperf-fy20q4

# Customer intent: As an identity administrator, I want to understand what authentication options are available in Azure AD and how or why I can use them to improve and secure user sign-in events.
---
# What authentication and verification methods are available in Azure Active Directory?

Microsoft recommends passwordless authentication methods such as Windows Hello, FIDO2 security keys, and the Microsoft Authenticator app because they provide the most secure sign-in experience. Although a user can sign-in using other common methods such as a username and password, passwords should be replaced with more secure authentication methods.

:::image type="content" border="true" source="media/concept-authentication-methods/authentication-methods.png" alt-text="Illustration of the strengths and preferred authentication methods in Azure AD." :::

Azure AD Multi-Factor Authentication (MFA) adds additional security over only using a password when a user signs in. The user can be prompted for additional forms of authentication, such as to respond to a push notification, enter a code from a software or hardware token, or respond to an SMS or phone call.

To simplify the user on-boarding experience and register for both MFA and self-service password reset (SSPR), we recommend you [enable combined security information registration](howto-registration-mfa-sspr-combined.md). For resiliency, we recommend that you require users to register multiple authentication methods. When one method isn't available for a user during sign-in or SSPR, they can choose to authenticate with another method. For more information, see [Create a resilient access control management strategy in Azure AD](concept-resilient-controls.md).

Here's a [video](https://www.youtube.com/watch?v=LB2yj4HSptc&feature=youtu.be) we created to help you choose the best authentication method to keep your organization safe.

## Authentication method strength and security

When you deploy features like Azure AD Multi-Factor Authentication in your organization, review the available authentication methods. Choose the methods that meet or exceed your requirements in terms of security, usability, and availability. Where possible, use authentication methods with the highest level of security.

The following table outlines the security considerations for the available authentication methods. Availability is an indication of the user being able to use the authentication method, not of the service availability in Azure AD:

| Authentication method          | Security | Usability | Availability |
|--------------------------------|:--------:|:---------:|:------------:|
| Windows Hello for Business     | High     | High      | High         |
| Microsoft Authenticator        | High     | High      | High         |
| Authenticator Lite             | High     | High      | High         |
| FIDO2 security key             | High     | High      | High         |
| Certificate-based authentication | High | High | High       |
| OATH hardware tokens (preview) | Medium   | Medium    | High         |
| OATH software tokens           | Medium   | Medium    | High         |
| SMS                            | Medium   | High      | Medium       |
| Voice                          | Medium   | Medium    | Medium       |
| Password                       | Low      | High      | High         |

For the latest information on security, check out our blog posts:

- [It's time to hang up on phone transports for authentication](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/it-s-time-to-hang-up-on-phone-transports-for-authentication/ba-p/1751752)
- [Authentication vulnerabilities and attack vectors](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/all-your-creds-are-belong-to-us/ba-p/855124)

> [!TIP]
> For flexibility and usability, we recommend that you use the Microsoft Authenticator app. This authentication method provides the best user experience and multiple modes, such as passwordless, MFA push notifications, and OATH codes.

## How each authentication method works

Some authentication methods can be used as the primary factor when you sign in to an application or device, such as using a FIDO2 security key or a password. Other authentication methods are only available as a secondary factor when you use Azure AD Multi-Factor Authentication or SSPR.

The following table outlines when an authentication method can be used during a sign-in event:

| Method                         | Primary authentication | Secondary authentication  |
|--------------------------------|:----------------------:|:-------------------------:|
| Windows Hello for Business     | Yes                    | MFA\*                     |
| Microsoft Authenticator (Push) | No                     | MFA and SSPR              |
| Microsoft Authenticator (Passwordless) | Yes            | No                        |
| Authenticator Lite             | No                     | MFA                       |
| FIDO2 security key             | Yes                    | MFA                       |
| Certificate-based authentication | Yes                  | No                        |
| OATH hardware tokens (preview) | No                     | MFA and SSPR              |
| OATH software tokens           | No                     | MFA and SSPR              |
| SMS                            | Yes                    | MFA and SSPR              |
| Voice call                     | No                     | MFA and SSPR              |
| Password                       | Yes                    |                           |

> \* Windows Hello for Business, by itself, does not serve as a step-up MFA credential. For example, an MFA Challenge from Sign-in Frequency or SAML Request containing forceAuthn=true. Windows Hello for Business can serve as a step-up MFA credential by being used in FIDO2 authentication. This requires users to be enabled for FIDO2 authentication to work successfully.

All of these authentication methods can be configured in the Azure portal, and increasingly using the [Microsoft Graph REST API](/graph/api/resources/authenticationmethods-overview).

To learn more about how each authentication method works, see the following separate conceptual articles:

* [Windows Hello for Business](/windows/security/identity-protection/hello-for-business/hello-overview)
* [Microsoft Authenticator app](concept-authentication-authenticator-app.md)
* [FIDO2 security key](concept-authentication-passwordless.md#fido2-security-keys)
* [Certificate-based authentication](concept-certificate-based-authentication.md)
* [OATH hardware tokens (preview)](concept-authentication-oath-tokens.md#oath-hardware-tokens-preview)
* [OATH software tokens](concept-authentication-oath-tokens.md#oath-software-tokens)
* [SMS sign-in](howto-authentication-sms-signin.md) and [verification](concept-authentication-phone-options.md#mobile-phone-verification)
* [Voice call verification](concept-authentication-phone-options.md)
* Password

> [!NOTE]
> In Azure AD, a password is often one of the primary authentication methods. You can't disable the password authentication method. If you use a password as the primary authentication factor, increase the security of sign-in events using Azure AD Multi-Factor Authentication.

The following additional verification methods can be used in certain scenarios:

* [App passwords](howto-mfa-app-passwords.md) - used for old applications that don't support modern authentication and can be configured for per-user Azure AD Multi-Factor Authentication.
* [Security questions](concept-authentication-security-questions.md) - only used for SSPR
* [Email address](concept-sspr-howitworks.md#authentication-methods) - only used for SSPR

## Usable and non-usable methods

Administrators can view user authentication methods in the Azure portal. Usable methods are listed first, followed by non-usable methods. 

Each authentication method can become non-usable for different reasons. For example, a Temporary Access Pass may expire, or FIDO2 security key may fail attestation. The portal will be updated to provide the reason for why the method is non-usable. 

Authentication methods that are no longer available due to "Require re-register multifactor authentication" are also displayed here.

:::image type="content" border="true" source="media/concept-authentication-methods/non-usable.png" alt-text="Screenshot of non-usable authentication methods." :::


## Next steps

To get started, see the [tutorial for self-service password reset (SSPR)][tutorial-sspr] and [Azure AD Multi-Factor Authentication][tutorial-azure-mfa].

To learn more about SSPR concepts, see [How Azure AD self-service password reset works][concept-sspr].

To learn more about MFA concepts, see [How Azure AD Multi-Factor Authentication works][concept-mfa].

Learn more about configuring authentication methods using the [Microsoft Graph REST API](/graph/api/resources/authenticationmethods-overview).

To review what authentication methods are in use, see [Azure AD Multi-Factor Authentication authentication method analysis with PowerShell](/samples/azure-samples/azure-mfa-authentication-method-analysis/azure-mfa-authentication-method-analysis/).

<!-- INTERNAL LINKS -->
[tutorial-sspr]: tutorial-enable-sspr.md
[tutorial-azure-mfa]: tutorial-enable-azure-mfa.md
[concept-sspr]: concept-sspr-howitworks.md
[concept-mfa]: concept-mfa-howitworks.md
