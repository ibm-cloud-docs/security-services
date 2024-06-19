---

copyright:
  years: 2024
lastupdated: "2024-06-19"

keywords:

subcollection: security-services

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# XXX the {{site.data.keyword.secrets-manager_full_notm}} trial plan
{: #ts-secrets-mgr-trial}
{: troubleshoot}

{: shortdesc}

You can create only one Trial instance of {{site.data.keyword.secrets-manager_short}} per account.
{: tsSymptoms}

- **Deployment error**: An error displays in the {{site.data.keyword.secrets-manager_short}} deployment step if a Trial instance is already deployed in the same account.
- **Redeployment failure**: If the automation provisions a Trial plan instance of {{site.data.keyword.secrets-manager_short}} and is undeployed and then redeployed with the Trial plan in the same account, the deployment of the `2b - Security Service - {{site.data.keyword.secrets-manager_short}}` member fails. This failure occurs because of the limitation of one Trial version of {{site.data.keyword.secrets-manager_short}} in an account.

    After deletion, you must remove the {{site.data.keyword.secrets-manager_short}} service from the reclamation state.


## What are reclamations?
{: #ts-reclamations-what-are}

In {{site.data.keyword.cloud_notm}}, when you delete a resource, it doesn't immediately disappear. Instead, it enters a reclamation state, where it remains for a short time (usually 7 days) before being permanently deleted. During the reclamation state, you can recover the resource, if needed.

To minimize costs, the deployable architecture deploys a Trial plan instance of {{site.data.keyword.secrets-manager_short}} by default. However, the Trial plan has some limitations. To avoid these limitations, you can deploy a Standard plan instance from the **Optional settings** of the deployable architecture.
{: tsCauses}


Before you can create a new Trial instance, delete the {{site.data.keyword.secrets-manager_short}} service from the reclamation state.
{: tsResolve}

Run the following {{site.data.keyword.cloud_notm}} CLI commands. The first command lists all the resources in reclamation state.

```sh
ibmcloud resource reclamations
```
{: pre}

Find the reclamation ID of the Secrets Manager service. Use that ID in the following command.

```sh
ibmcloud resource reclamation-delete <reclamation-id>
```
{: pre}
