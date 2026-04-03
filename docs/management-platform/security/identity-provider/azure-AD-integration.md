# Azure AD integration with MFA

VC Hub identity provider supports integration with Azure AD (Microsoft Entra ID). After integration, users can sign in through Entra ID and use multi-factor authentication (MFA), which improves account security.

## Prerequisites

- Access to Azure portal: [https://portal.azure.com/](https://portal.azure.com/)
- Permission to create app registrations in Microsoft Entra ID
- VC Hub login URL and logout URL
- A test user account in Entra ID

## Configure Microsoft Entra ID

1. Sign in to the Azure portal, then open **Microsoft Entra ID**.

   ![Open Microsoft Entra ID](10.png)

2. In the left panel, select **App registrations**, then select **+ New registration**.

   ![Create app registration](11.png)

3. Open **Authentication** for the app registration. In **Web redirect URIs**, add the VC Hub login URL and logout URL.

   ![Configure redirect URIs](12.png)

4. Open **Token configuration**, then add the required optional claims.

   ![Configure token claims](13.png)

5. Open **Certificates & secrets**, then create a client secret.

   ![Create client secret](14.png)

6. Copy the **Application (client) ID**.

   ![Copy client ID](42.png)

7. Copy the **client secret value**.

   ![Copy client secret](15.png)

8. Open **Overview**, select **Endpoints**, then copy the **OpenID Connect metadata document** URL.

   ![Copy OpenID metadata URL](16.png)

## Enable MFA for users

9. Return to the root of **Microsoft Entra ID**, then open **Users**.

   ![Open Users](17.png)

10. Select **Per-user MFA**.

    ![Open Per-user MFA](18.png)

11. Select the target users and choose **Enable MFA**.

    ![Enable MFA](19.png)

## Configure VC Hub identity provider

12. In VC Hub, open the identity provider page and create a new provider using:

- Client ID
- Client secret
- OpenID Connect metadata document URL

    ![Create VC Hub provider](20.png)

## Verify the login flow

13. In the Azure AD provider settings, select **Login Test**. The browser should redirect to the Microsoft sign-in page.

    ![Redirect to Microsoft sign-in](21.png)

    ![Microsoft sign-in page](22.png)

14. Sign in with a personal or domain account. A number-matching challenge is displayed.

    ![Number-matching challenge](23.png)

15. Enter the number in Microsoft Authenticator on the mobile device to complete authentication.

    ![MFA authentication complete](24.png)



  

