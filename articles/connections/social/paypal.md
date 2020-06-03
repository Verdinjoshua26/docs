---
title: Connect Apps to PayPal
connection: PayPal
image: /media/connections/paypal.png
seo_alias: paypal
index: 10
description: How to obtain a Client Id and Client Secret for PayPal.
toc: true
topics:
  - connections
  - social
  - paypal
contentType: how-to
useCase:
    - customize-connections
    - add-idp
---

# Connect Apps to PayPal

You can add functionality to your app that allows your users to login with PayPal.

## Prerequisites

Before connecting your Auth0 app to PayPal, you will need to have an account on the [PayPal Developer](https://developer.paypal.com/) portal.

## Steps

To connect your app to PayPal, you will:

1. [Set up your app in PayPal](#set-up-your-app-in-paypal)
2. [Create and enable a connection in Auth0](#create-and-enable-a-connection-in-auth0)
3. [Test the connection](#test-the-connection)

### Set up your app in PayPal

1. Log in to [PayPal Developer Portal](https://developer.paypal.com/) and click on **Dashboard**.
2. On the **My Apps & Credentials** page, scroll down to under the **REST API Apps** section and click **Create App**.
3. Provide a value for **App Name** and click **Create App**. PayPal will display the **Client ID** and **Secret** values.

::: note
By default you are editing your Sandbox account. Switch to your live account by toggling to **Live** on the top right of the page.
:::

4. Scroll to the **Sandbox App Settings** section and **Show** the **Return URL** box. Enter your <dfn data-key="callback">callback URL</dfn>:

  `https://${account.namespace}/login/callback`

<%= include('../_find-auth0-domain-redirects') %>

5. To control the scope of access to customer data (such as profile information, email address, home address, and phone number) through Auth0, you need to enable access to this information by selecting the desired attributes under the **Advanced Options**, which becomes available to you if you enable the **Log In with PayPal** feature.

6. For your Sandbox account to work, check the Full Name, Date of birth, Timezone, Locale, and Language because Auth0 requires this Basic Profile information.

7. Click **Save**:

### Create and enable a connection in Auth0

[Set up the Bitbucket social connection](/dashboard/guides/connections/set-up-connections-social) in Auth0. Make sure you have the **API key** and the **API secret key** generated.

### Test the connection

You're ready to [test your connection](/dashboard/guides/connections/test-connections-social). After logging in, you'll be prompted to allow your app access. To do so, click **Install unlisted app**.

<%= include('../_quickstart-links.md') %>
