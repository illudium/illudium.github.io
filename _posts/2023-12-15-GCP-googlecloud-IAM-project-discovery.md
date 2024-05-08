## GCP (Google Cloud): Discovery - collecting, reviewing auditing Projects and IAM

Pulling GCP IAM information typically means dealing with how GCP effectively uses Projects as a boundary/encapsulation.

Start by listing all projects in the root folder of an organization in GCP:

```gcloud
gcloud alpha projects search --query="parent.id=<tenant_ID_Here"
```

AND

```gcloud
gcloud projects list --filter 'parent.id=<id_here> AND parent.type=organization' | awk '{print $1 }' > projects.txt
```

And from there, reference the following with something like

```shell
for Project in projects.txt; do gcloud projects get-iam-policy Project; done
```


For more information and reference, see 
https://stackoverflow.com/questions/44746358/how-do-i-list-all-iam-users-for-my-google-cloud-project



**Dec 15, 2023**

