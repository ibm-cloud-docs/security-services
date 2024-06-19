---

copyright:
  years: 2024
lastupdated: "2024-06-19"

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
