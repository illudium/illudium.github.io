---
title: "GCP (Google Cloud) IAP"
date: 2026-09-07T00:00:00
draft: false
---
## IAP in Google Cloud

IAP is phenomonal technology that should be more widely known by those working with GCP.

No bastion host (or jump box) required.

The documentian landing page is provided by Google here, https://cloud.google.com/security/products/iap

Noteworthy highlights being:

> #### Centralized access control
>
> IAP provides a single point of control for managing user access to web applications and cloud resources.
>
> #### Works with cloud and on-premises apps
>
> IAP can protect access to applications hosted on Google Cloud, other clouds, and on-premises.
>
> #### Protects apps and VMs
>
> With [TCP forwarding](https://cloud.google.com/iap/docs/tcp-forwarding-overview/), IAP can protect SSH and RDP access to your VMs hosted on Google Cloud. Your VM instances don't even need public IP addresses.



For some time, getting IAP setup for CloudRun was entirely doable, but was recently simplified.

In a nutshell:

>1. In the Google Cloud console, go to Cloud Run
>2. Select **Services** from the Cloud Run navigation menu.
>3. If you are configuring a new service, click **Deploy container** and fill out the initial service settings.
>4. If you are configuring an existing service, click the service, then click the **Security** tab.
>5. Select **Require authentication**, then select **Identity-Aware Proxy (IAP)**.
>6. Optional: To grant access to users, follow the instructions to [Manage user or group access](https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run#manage-access) for IAP. If you encounter issues when configuring access for users outside of your organization, see the [Troubleshooting](https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run#troubleshooting) section. To save the configuration, click **Save**.
>7. Click **Create** for a new service. Click **View diff & redeploy**, then **Deploy changes** for an existing service.

However, I'll normally always be working with such matters programmatically whenever possible,
so we'd be looking at https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run#gcloud



In a very welcome move, Google has also simplified configuring access for external users. 
See https://docs.cloud.google.com/run/docs/securing/identity-aware-proxy-cloud-run#console_2
