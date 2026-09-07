---
title: "GCP (Google Cloud) IAP"
date: 2026-09-07T00:00:00
draft: false
---
## IAP in Google Cloud

Google's IAP is phenomonal technology that should be more widely known by those working with GCP.

Secure access to resources, with no bastion host (or jump box) required.

The landing page for IAP documentation is here, [**https://cloud.google.com/security/products/iap**](https://cloud.google.com/security/products/iap)

Noteworthy highlights being:

> ***Centralized access control\***

When it comes to using IAP with CloudRun - for some time - setup was slightly more convoluted than one might hope for. Entirely doable, but this was recently simplified.

In a nutshell:

> ***In the Google Cloud console, go to Cloud RunSelect Services from the Cloud Run navigation menu.If you are configuring a new service, click Deploy container and fill out the initial service settings.If you are configuring an existing service, click the service, then click the Security\*** [***tab.Select\***](http://tab.select/) ***Require authentication, then select Identity-Aware Proxy (IAP).Optional: To grant access to users, follow the instructions to\*** [***Manage user or group access\***](https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run#manage-access) ***for IAP. If you encounter issues when configuring access for users outside of your organization, see the\*** [***Troubleshooting\***](https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run#troubleshooting) ***section. To save the configuration, click\*** [***Save.Click\***](http://save.click/) ***Create for a new service. Click View diff & redeploy, then Deploy changes for an existing service.\***

However - for my part -  I’ll normally always be working with such matters programmatically whenever possible, so we’d be looking at [**https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run#gcloud**](https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run#gcloud)

In a very welcome move, Google has also simplified configuring access for external users. See [**https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run#console_2**](https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run#console_2)
