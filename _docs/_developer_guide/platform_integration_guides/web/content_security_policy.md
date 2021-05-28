---
nav_title: Content Security Policy
platform: Web
page_order: 25
page_type: reference
description: "This article covers Content-Security-Policy headers needed with the Braze Web SDK"
---

# Content Security Policy Headers

Content-Security-Policy provides added security by restricting how and where content can be loaded on your website.

{% alert important %}
This article is intended for developers working on websites that enforce CSP rules, and how to integrate with Braze. It is not intended as advice on how you should approach security.
{% endalert %}

## Nonce Attributes {#nonce}

If you use a `nonce` value in your `script-src` or `style-src` directives, pass that value to the `contentSecurityNonce` initialization option to propagate it to newly created scripts and styles generated by the SDK.

```javascript
import braze from "@braze/web-sdk";

braze.initialize(apiKey, {
  baseUrl: baseUrl,
  contentSecurityNonce: "YOUR-NONCE-HERE", // assumes a "nonce-YOUR-NONCE-HERE" CSP value
});
```

## Directives {#directives}

### connect-src {#connect-src}

- `connect-src https://sdk.iad-01.braze.com` - allows the SDK to communicate with Braze APIs.
  - Change this URL to match your `baseUrl` initialization option's API Endpoint, as found [here](https://www.braze.com/docs/user_guide/administrative/access_braze/sdk_endpoints/).

### script-src {#script-src}

- `script-src https://js.appboycdn.com` - required when using the CDN-hosted integration.
- `script-src 'unsafe-eval'` - required only when using the integration snippet which contains reference to `appboyQueue`
  - To avoid using this directive, integrate using NPM instead.
- `script-src 'nonce-...'` or `script-src 'unsafe-inline'` are required for certain In-App Messages (custom HTML, for example).

## Font Awesome {#font-awesome}

To disable the automatic inclusion of Font Awesome, use the `doNotLoadFontAwesome` initialization option:

```javascript
import braze from "@braze/web-sdk";

braze.initialize(apiKey, {
  baseUrl: baseUrl,
  doNotLoadFontAwesome: true,
});
```

If you choose to use the Font Awesome, the following CSP directives are required:

- `style-src https://use.fontawesome.com`
- `style-src 'nonce-...'` or `style-src 'unsafe-inline'` are also required.
- `font-src https://use.fontawesome.com`