---
title: "GCP - How do I get a list of all Projects in an Organization ?"
date: 2026-09-06T00:00:00
draft: false
---
## GCP (Google Cloud): Getting a list of all Project in a GCP Org (tenant)

When dealing with Google Cloud (GCP), how can we get a list of all existing projects (for example) ? There are a number of good posts out there about this, so I'm not presenting anything especially novel here. But - if nothing else - hopefully this will be useful to others, and I'm recording it here for posterity.

Pulling GCP IAM information typically means dealing with how GCP effectively uses Projects as a boundary/encapsulation. Which requires a multi-step approach, such as follows:

```gcloud
# gcloud list all projects in root folder of organization in GCP:
gcloud alpha projects search --query="parent.id=<tenant_ID_Here"

gcloud projects list --filter 'parent.id=<id_here> \
 AND parent.type=organization' | awk '{print $1 }' > projects.txt
```

And from there, reference the following with something like:

```gcloud
for Project in projects.txt; do gcloud projects get-iam-policy Project; done
```



*Originally posted December, 2023*

