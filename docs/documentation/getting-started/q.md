---
title: q
deprecated: false
hidden: false
metadata:
  robots: index
---
---
title: Akamai Proxy Integration
excerpt: Fingerprint JS agent v3.6.0 or later is required.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  image: >-
    https://files.readme.io/7acadd2002c3136955d545ac09f935a31b4f57f4442a63ddce30cfd43ebb76c6-fpjs-preview.png
  robots: index
next:
  description: ''
---
*Fingerprint Akamai Proxy Integration* is responsible for proxying identification and agent-download requests between your website and Fingerprint through your Akamai infrastructure. The integration consists of a set of property rules you need to add to your Akamai property configuration. The property rules template is available on [GitHub](https://github.com/fingerprintjs/fingerprint-pro-akamai-proxy-integration).

![](https://files.readme.io/f581952-akamai-proxy-integration.png)

> 🚧 Limitations and expectations
>
> ### Integration in Beta
>
> This integration is in Beta. Please report any issues to our [support team](https://fingerprint.com/support/).
>
> ### Limited to Enterprise plan
>
> Support for the Akamai Proxy Integration is provided only to customers on the **Enterprise** Plan. Other customers are encouraged to use [Custom subdomain setup](https://dev.fingerprint.com/docs/custom-subdomain-setup) or [Cloudflare Proxy Integration](https://dev.fingerprint.com/docs/cloudflare-integration).
>
> ### Manual updates occasionally required
>
> The underlying data contract in the identification logic can change to keep up with browser and device releases. Using the Akamai Proxy Integration might require occasional manual updates on your side. Ignoring these updates will lead to lower accuracy or service disruption.

## The benefits of using the Akamai Proxy Integration

* Significant increase in accuracy in browsers with strict privacy features such as Safari or Firefox.
* Cookies are now recognized as “first-party.” This means they can live longer in the browser and extend the lifetime of visitor IDs.
* Ad blockers will not block our Fingerprint JS agent from loading. Attempts to connect to an external URL will be stopped by most ad blockers while attempts to connect to the same site URL will be allowed.
* Ad blockers will not block our identification requests since they are sent to the specific path or subdomain that belongs to the same site.
* Insight and control over the identification requests that can be combined with other Akamai features like property rules and traffic reports.
* With the Akamai Proxy Integration, you can manage unlimited subdomains and paths and provide Fingerprint services to all your customers at any scale while benefiting from all the 1st-party integration improvements.
* Cookie security: Akamai Proxy Integration drops all the cookies sent from the origin website. The source is open-source so this behavior can be transparently verified and audited.
* Easy to meet compliance and auditing requirements.

## Integration setup overview

1. Issue a proxy secret in the Fingerprint Dashboard.
2. Create path variables used by the Akamai property rules and client agent configuration on your website or mobile app.
3. Install and configure the integration in your Akamai account. You have 2 options:
   1. [Using Terraform](https://dev.fingerprint.com/docs/deploy-akamai-proxy-integration-via-terraform) (recommended).
   2. [Using Akamai Property Manager API](https://dev.fingerprint.com/docs/deploy-akamai-proxy-integration-via-papi).

Finally, configure the Fingerprint JavaScript agent on your website or client application.

### Step 1: Issue a Fingerprint proxy secret

Issue a Fingerprint proxy secret to authenticate requests from your Akamai infrastructure.

1. Go to the [Fingerprint dashboard](https://dashboard.fingerprint.com) and select your workspace.
2. In the left menu, navigate to [**API keys**](https://dashboard.fingerprint.com/api-keys).
3. Click **Create Proxy Key**.
4. Give it a name, for example, `Akamai proxy integration`.
5. Click **Create API Key**.

You will use the proxy secret value in the following step, so store it somewhere safe.

## Step 2: Create path variables

Set the path variables you will use throughout your property configuration and the JavaScript agent configuration on your website. These values are arbitrary. Just decide what your values are and write them down somewhere.

In this guide, we will use readable values corresponding to the variable names to make it easier to follow:

```
FPJS_INTEGRATION_PATH="FPJS_INTEGRATION_PATH"
FPJS_AGENT_PATH="FPJS_AGENT_PATH"
FPJS_RESULT_PATH="FPJS_RESULT_PATH"
```

However, your values used in production should look more like random strings:

```text
FPJS_INTEGRATION_PATH="ore54guier"
FPJS_AGENT_PATH="vbcnkxb654"
FPJS_RESULT_PATH="5yt489hgfj"
```

That is because ad blockers might automatically block requests from any URL containing fingerprint-related terms like "fingerprint", "fpjs", "track", etc. Random strings are the safest. So whenever you see a value like `FPJS_INTEGRATION_PATH` in this guide, you should use your random value instead.

## Step 3: Install and configure the integration in your Akamai property

You can choose from two available installation methods.

### Using Terraform (recommended)

If you manage your infrastructure as code using Terraform, you can use the Fingerprint Akamai proxy integration Terraform module. This installation method does not include any mechanism for automatic updates. The proxy function code is updated every time you run `terraform apply`.

If you prefer the Terraform installation method, continue with [**Install Akamai proxy integration using Terraform**](https://dev.fingerprint.com/docs/deploy-akamai-proxy-integration-via-terraform), then come back to this page to configure the Fingerprint JavaScript agent on your website.

### Using Akamai Property Manager API

If you don't use Terraform to manage your infrastructure, you can deploy the integration using Akamai Property Manager API. This installation method does not include any mechanism for automatic updates. You will need to manually repeat the deployment process every time you update the integration.

If you prefer the Akamai Property Manager API installation method, continue with [**Install Akamai proxy integration using Akamai Property Manager API**](https://dev.fingerprint.com/docs/deploy-akamai-proxy-integration-via-papi), then come back to this page to configure the Fingerprint JavaScript agent on your website.

## Configure Fingerprint Pro Agent

1. Use the random path variables created in deployment steps according to your deployment method to construct the `scriptUrlPattern` (agent download) and `endpoint` (get result) URLs.
2. Configure the Fingerprint JS Agent on your website accordingly:

```javascript NPM package
import * as FingerprintJS from '@fingerprintjs/fingerprintjs-pro'

// Initialize the agent at application startup.
const fpPromise = FingerprintJS.load({
  apiKey: 'PUBLIC_API_KEY',
  scriptUrlPattern: [
    'https://yourwebsite.com/FPJS_INTEGRATION_PATH/FPJS_AGENT_PATH?apiKey=<apiKey>&version=<version>&loaderVersion=<loaderVersion>',
    FingerprintJS.defaultScriptUrlPattern, // Fallback to default CDN in case of error
  ],
  endpoint: [
    'https://yourwebsite.com/FPJS_INTEGRATION_PATH/FPJS_RESULT_PATH?region=us',
    FingerprintJS.defaultEndpoint // Fallback to default endpoint in case of error
  ],
});
```
```javascript CDN
const url = 'https://yourwebsite.com/FPJS_INTEGRATION_PATH/FPJS_AGENT_PATH?apiKey=<PUBLIC_API_KEY>';
const fpPromise = import(url)
  .then(FingerprintJS => FingerprintJS.load({
    endpoint: [
      'https://yourwebsite.com/FPJS_INTEGRATION_PATH/FPJS_RESULT_PATH?region=us',
      FingerprintJS.defaultEndpoint // Fallback to default endpoint in case of error
    ]
  }));
```

If everything is configured correctly, you should receive the latest Fingerprint client-side script and the identification result through your Akamai integration. If you have any questions, reach out to our [support team](https://fingerprint.com/support/).

## Monitoring the integration

Go to **Dashboard** > [**SDKs & integrations**](https://dashboard.fingerprint.com/integrations) > **Akamai** to see the status of your integration. Here you can monitor: 

* If the integration is up to date.
* How many identification requests are coming through the integration (and how many are not).
* The error rate of proxied identification requests (caused by missing or incorrect proxy secret).

The information on the status page is cached so allow a few minutes for the latest data points to be reflected.

![](https://files.readme.io/61c1cc5a104862d25564f5caeac0b70e00b9b57f4bffe999a427d6772c69a42f-CleanShot_2024-11-07_at_12.49.162x.png)
s