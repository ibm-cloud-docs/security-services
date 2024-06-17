---

copyright:
  years: 2024
lastupdated: "2024-06-17"

keywords:

subcollection: security-services

---

{{site.data.keyword.attribute-definition-list}}

# Planning for the core security services deployable architectures
{: #prereqs}

## Before you begin
{: #prereq-steps}

Make sure that you set up the following items before you deploy the architecture.

- Create an API key in the target account with sufficient permissions. The target account is the account that will host the resources that are deployed by this deployable architecture. For more information, see [Managing user API keys](/docs/account?topic=account-userapikey&interface=ui). Store the value of the API key because you need it later.

    On evaluation environments, grant the `Administrator` role on the **IAM Identity Service**, **All Identity and Access enabled services**, and on the **Activity Tracker Event Routing** and **All Account Management** services. For a production environment, restrict access to the minimum level of permissions indicated in the [permissions tab](/catalog/7df1e4ca-d54c-4fd0-82ce-3d13247308cd/architecture/deploy-arch-ibm-core-security-svcs-0294f96e-7314-48d1-a710-c08a541b2119#permissions) of the deployable architecture.
- (Optional) Install the {{site.data.keyword.cloud_notm}} CLI Project plug-in by running the `ibmcloud plugin install project` command. For more information, see the [Project CLI reference](/docs/cli?topic=cli-projects-cli).

## Limitations with the {{site.data.keyword.secrets-manager_full_notm}} trial plan
{: #limitations-secrets-manager}

To minimize costs, the deployable architecture deploys a Trial plan instance of {{site.data.keyword.secrets-manager_short}} by default. However, the Trial plan has some limitations. To avoid these limitations, you can deploy a Standard plan instance from the **Optional settings** of the deployable architecture.

You can create only one Trial instance of {{site.data.keyword.secrets-manager_short}} per account.

- **Deployment error**: An error displays in the {{site.data.keyword.secrets-manager_short}} deployment step if a Trial instance is already deployed in the same account.
- **Redeployment failure**: If the automation provisions a Trial plan instance of {{site.data.keyword.secrets-manager_short}} and is undeployed and then redeployed with the Trial plan in the same account, the deployment of the `2b - Security Service - {{site.data.keyword.secrets-manager_short}}` member fails. This failure occurs because of the limitation of one Trial version of {{site.data.keyword.secrets-manager_short}} in an account.

    After deletion, you must remove the {{site.data.keyword.secrets-manager_short}} service from the reclamation state.

### What are reclamations?
{: #reclamations-what-are}

In {{site.data.keyword.cloud_notm}}, when you delete a resource, it doesn't immediately disappear. Instead, it enters a reclamation state, where it remains for a short time (usually 7 days) before being permanently deleted. During the reclamation state, you can recover the resource, if needed.

### Deleting reclamations
{: #delete-reclamations}

Before you can create a new Trial instance, delete the {{site.data.keyword.secrets-manager_short}} service from the reclamation state by running the following {{site.data.keyword.cloud_notm}} CLI commands:

```sh
ibmcloud resource reclamations # Lists all the resources in reclamation state. Find the reclamation ID of the Secrets Manager service
ibmcloud resource reclamation-delete <reclamation-id>
```
