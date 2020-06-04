---
title: Connect Apps to Salesforce
connection: Salesforce
image: /media/connections/salesforce.png
seo_alias: salesforce
index: 6
description: How to connect your app to Salesforce using Auth0.
toc: true
topics:
  - connections
  - social
  - salesforce
contentType: how-to
useCase:
    - customize-connections
    - add-idp
---

# Connect Apps to Salesforce

You can add functionality to your web app that allows your users to log in with Salesforce. 

## Prerequisites

Before connecting your Auth0 app to Salesforce, you must have a [Salesforce](https://login.salesforce.com/) account.

## Steps

To connect your app to Salesforce, you will:

1. [Set up your app in Salesforce](#set-up-your-app-in-salesforce)
2. [Create and enable a connection in Auth0](#create-and-enable-a-connection-in-auth0)
3. [Test the connection](#test-the-connection)

### Set up your app in Salesforce

1. Log into [Salesforce](https://login.salesforce.com/) and click **Settings > Setup**.

2. Go to **Platform Tools > Apps**. Under **App Manager** click **New Connected App**.

3. Complete the New Connected App form. 

4. Select **Enable OAuth Settings** under **API (Enable OAuth Settings)**.
5. Enter your <dfn data-key="callback">callback URL</dfn>: 

  `https://${account.namespace}/login/callback`

<%= include('../_find-auth0-domain-redirects') %>

6. Add *Access your basic information* to the **Selected OAuth Scopes**.
7. Click **Save**. Once your app is registered, your `Consumer Key` and `Consumer Secret` are displayed.

### Create and enable a connection in Auth0

[Set up the Salesforce social connection](/dashboard/guides/connections/set-up-connections-social) in Auth0. Make sure you have the **API key** and the **API secret key** generated.

### Test the connection

You're ready to [test your connection](/dashboard/guides/connections/test-connections-social). After logging in, you'll be prompted to allow your app access. To do so, click **Install unlisted app**.

## Salesforce Community Authentication

Authenticating users in a Salesforce community uses different endpoints that the regular Salesforce app.

The authorization URL for a Community site is: `https://{name of your community}.force.com/{community path}/oauth2/authorize`.

In the following example, the community is named __contoso__ and it is for __customers__: 

```text
https://contoso.force.com/customers/oauth2/authorize?
response_type=token&
client_id=your_app_id&
redirect_uri=your_redirect_uri
```

Auth0 will automatically pass all required OAuth2 parameters (such as `response_type`, `client_id`, and so on) and concatenate other elements to the path (such as `oauth2/authorize`). All that is required is that you configure the __base__ community site URL: `https://contoso.force.com/customers`.

For full details refer to this [Salesforce article](http://www.salesforce.com/us/developer/docs/chatterapi/Content/quickstart_communities.htm).

It is common to customize the login page for __Community__ sites. If you do so, remember that the login page is part of the login transaction and you must honor the OAuth2 flow. [This sample](https://github.com/salesforceidentity/basic-custom-login) provides details.

<%= include('../_quickstart-links.md') %>
