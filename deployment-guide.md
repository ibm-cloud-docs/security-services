---

copyright:
  years: 2024
lastupdated: "2024-06-20"

keywords: security services, deployable architecture, IaC

subcollection: security-services

---

{{site.data.keyword.attribute-definition-list}}

# Deploying the Core Security Services deployable architecture
{: #deploy-css}

You can deploy a deployable architecture from the {{site.data.keyword.cloud_notm}} catalog.
{: shortdesc}

To deploy the core security services architecture through the {{site.data.keyword.cloud_notm}} catalog, follow these steps.

Make sure that you comply with the prerequisites in the [planning](/docs/security-services?topic=security-services-prereqs) topic.
{: important}



## Step 1. Add the architecture to a project
{: #deploy-details-deploy}

1.  Go to the {{site.data.keyword.cloud_notm}} [catalog](/catalog#reference_architecture){: external} and search for the Core Security Services deployable architecture.
1.  Click the tile for the deployable architecture to open the details.
1.  Select the latest product version in the Architecture section.
1.  Click **Review deployment options**.
1.  Select the **Add to project** deployment type in Deployment options, and then click **Add to project**.

    For more information about the enterprise account structures, see the [Central administration account](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-admin-hub-account) white paper.

    1.  Name your project, enter a description, and specify a configuration name. Click **Create**.

## Step 2. Configure your stack
{: #deploy-configure}

Create your configuration by setting variables.


1.  From the **Security** panel, select the authentication method that you want to use to deploy your architecture.

    Add the API key that you identified in the [planning](/docs/security-services?topic=security-services-prereqs) topic.


1.  In the **Security** > **Authentication** tab in the **Configure** section, select the API key

1.  Enter values for required fields from the **Required** tab.

    1.  Enter a prefix. This prefix is added to the beginning of the name of most resources that are created by the deployable architecture. The prefix helps to make sure that the resource names are unique, and it avoids clashes with other resources in the same account.
    1.  Select the region to create the resources, and provide a resource group name.
1.  Review values for optional fields from the **Optional** tab:

    1.  Select the pricing plans for {{site.data.keyword.secrets-manager_short}} and {{site.data.keyword.compliance_short}}. These fields are optional fields. However, they are required to build the sample app.
    1.  Review the other input variables.

1.  Click **Save**. After the input values are validated, the button changes to **View stack configurations**.

## Step 3. Validate and deploy the architecture
{: #deploy-validate}

1.  In your project, click the **Configurations** tab.

    If the first member configuration of the stack (`1 - Key management`) is not marked as **Ready to validate**, refresh the page in your browser.
1.  Click **Validate** in **Draft status** in the `1 - Key management` row.

    ![validate button](images/ccs_validate.png)
1.  Approve the configuration and click **Deploy** after validation successfully completes.
1.  After you deploy the initial member configuration, you can validate and deploy the remaining member configuration at the same time. Repeat these deployment steps for each member configuration in the architecture.

The core security services deployable architecture is now deployed in the target account.

## Viewing resources created by the deployable architecture
{: #deploy-view-resources}

View the resources created by the deployable architecture.

1.  In the {{site.data.keyword.cloud_notm}} console, click the **Navigation menu** icon ![Navigation menu icon](../icons/icon_hamburger.svg "Menu") > **Resource list** in the target account.
1.  Choose the resource group and region where the infrastructure was deployed. The resource group name is based on the `prefix` and `resource_group_name` inputs of the deployable architecture configuration.

## Next steps
{: #next-steps}

- Share your deployable architecture with users in your account or other accounts by using a [private catalog](/docs/secure-enterprise?topic=secure-enterprise-catalog-enterprise-share&interface=ui). Sharing to a private catalog makes your deployable architecture available in a private {{site.data.keyword.cloud_notm}} catalog.

    Select the **Add to private catalog** option in the menu on the member configuration.
