---

copyright:
  years: 2024
lastupdated: "2024-06-19"

keywords: security services, deployable architecture, IaC

subcollection: security-services

---

{{site.data.keyword.attribute-definition-list}}

# Deploying Core Security Services on {{site.data.keyword.cloud_notm}}
{: #deployment-guide}

The Core Security Services deployable architecture is a preconfigured set of infrastructure as code (IaC) assets that are deployed and configured based on the recommended best practices. {{site.data.keyword.cloud_notm}}'s core security services are crucial for ensuring robust security and compliance for cloud-based applications and data. The primary goal of this deployable architecture is to provide a framework for secure and compliant {{site.data.keyword.cloud_notm}} Workloads.

## Objectives and benefits
{: #deployment-guide-objectives}

This deployable architecture is designed to showcase a fully automated deployment of {{site.data.keyword.cloud_notm}} Core Security Services and its dependencies through {{site.data.keyword.cloud_notm}} Project, providing a flexible and customizable foundation for your own application deployments on {{site.data.keyword.cloud_notm}}.

By leveraging this architecture, you can accelerate your deployment and tailor it to meet your unique business needs and enterprise goals.

By using this architecture, you can:

- **Establish trust:** The architecture ensures trust by configuring the {{site.data.keyword.cloud_notm}} account to align with compliance settings as defined in the [Financial Services](/docs/framework-financial-services?topic=framework-financial-services-about) framework.
- **Ensure observability:** The architecture provides observability by deploying services such as {{site.data.keyword.la_full_notm}}, {{site.data.keyword.monitoringlong_notm}}, {{site.data.keyword.atracker_full_notm}}, and log retention through {{site.data.keyword.cos_full_notm}} buckets.
- **Implement security:** The architecture ensures security by deploying IBM {{site.data.keyword.keymanagementservicelong_notm}} and {{site.data.keyword.secrets-manager_full_notm}}.
- **Achieve regulatory compliance:** The architecture ensures regulatory compliance by implementing centralized key management, centralized secrets management, and along with {{site.data.keyword.sysdigsecure_full_notm}}, secure application lifecycle management.


## Deployment details
{: #deployment-guide-details}

To deploy this architecture, follow these steps.

Before deploying the stack, make sure you check out the [Prerequisites](/docs/security-services?topic=security-services-prereqs) first.

### 1. Deploy the stack in a new project from catalog
{: #deployment-guide-details-deploy}

- Locate the Core Security Services [tile](/catalog/7df1e4ca-d54c-4fd0-82ce-3d13247308cd/architecture/deploy-arch-ibm-core-security-svcs-0294f96e-7314-48d1-a710-c08a541b2119#about) for the Deployable Architecture in the {{site.data.keyword.cloud_notm}} catalog. It loads the Core Security Services panel. On this panel, you can review the product version, Variation, architecture overview, permissions, security and compliance, help, and pricing.
- Click **Add to project**.

    ![image](images/ccs_catalog_details.png)

- Select **Create new** and enter the following details:
    - Name and description (for example, `Core Security Services`).
    - Region and resource group for the project. For example, for evaluation purposes, you can select the region the closest to you, and the Default resource group. For more information about the recommended production topology, see the Enterprise account architecture central administration account [white paper](/docs/enterprise-account-architecture?topic=enterprise-account-architecture-admin-hub-account).
    - Configuration name (name of the automation in the project, for example, `ccs_cfg`, `ccs_dev`, or `ccs_prod`, ideally matching the deployment target, but this can be any name).

        ![project](images/ccs_add_to_project.png)

- Click **Add** (or **Create** if this is the first project in the account) at the lower right of the modal window to complete.

### 2. Set the input configuration for the stack
{: #deployment-guide-details-input}

After completing the previous step, you are directed to a page allowing you to enter the configuration for your deployment:

- Under **Security** > **Authentication**, enter the API key from the prereqs in the `api_key` field.
    ![inputs](images/ccs_add_api_key.png)

- Under Required, input a prefix. This prefix is appended to the name of most resources created by automation, ensuring uniqueness and avoiding clashes when provisioning names in the same account. **Note:** Prefixes can't contain underscores.
- Select the region and provide a resource group name where you would like the resources to be created.
- Under Optional, input the {{site.data.keyword.secrets-manager_short}} and security services center's plan field. While not necessary for deploying {{site.data.keyword.cloud_notm}} resources, it is recommended and required to enable the building and deployment of the sample app.

You can explore the other available inputs, such as the region and resource group name (under the required tab), leave them as is, or modify them as needed.

When you're ready, click **Save** at the top of the screen. After validating the input values from the earlier step, the button changes to **View stack configurations**.

### 3. Deploy the architecture
{: #deployment-guide-details-deploy-architecture}

Navigate to the project deployment view by clicking the project name in the breadcrumb menu.

![menu](images/ccs_project_deployment_view.png)


You are directed to a screen looking like:

![validate](images/ccs_project_configuration_stack.png)

If the first member of the stack is not be marked as **Ready to validate, refresh the page in your browser.

#### Deployment through the UI
{: #deployment-guide-details-deploy-architecture-ui}

1. Click **Validate**.

    ![validate button](images/ccs_validate.png)

1. Wait for validation.

    ![validation](images/ccs_waiting_for_validation.png)

1. Approve and click the **Deploy**.

    ![deploy](images/ccs_approve_and_deploy.png)

1. Wait for deployment.

1. Repeat step 1 for the next configuration in the architecture. Note that as you progress in deploying the initial kms configuration, you are given the option to validate and deploy multiple configurations in parallel.

    ![deployed](images/ccs_stack_deployed.png)

### 4. Post deployment steps
{: #deployment-guide-details-deploy-architecture-more-steps}

At this point, the infrastructure platform services have been successfully deployed in the target account.

#### Viewing core security services resources
{: #deployment-guide-details-deploy-architecture-more-steps-view}

To view the deployment of the resources related to core security services, follow these steps:
1. **Access the Resource list View**: Navigate to the Resource List Icon on [Left Navigation](https://cloud.ibm.com/resources) in the target account.

1. **Select the Resource Group and Region**: Choose the resource group and region where the infrastructure was deployed. The resource group name is based on the prefix and resource_group_name inputs of the deployable architecture.

    ![deployed_resources](images/ccs_deployed_resources.png)

## Customization options
{: #deployment-guide-customizations}

There are numerous customization possibilities available out of the box. This section explores some common scenarios, but is not exhaustive.

### Editing individual configurations
{: #deployment-guide-customizations-editing-config}

Each configuration in the deployed stack surfaces a large number of input parameters. You can directly edit each parameter to tailor your deployment by selecting the **Edit** option in the menu for the corresponding configuration on the right side.

![edit config](images/css_edit_configurations.png)

This approach enables you to:
- Use existing instances of {{site.data.keyword.keymanagementserviceshort}}, {{site.data.keyword.secrets-manager_short}}, and other services
- Deploy to an existing resource group
- Configure endpoint type private/public
- Reuse existing {{site.data.keyword.keymanagementserviceshort}} keys
- Tuning the parameters of individual services
- ...

### Removing configurations from the stack
{: #deployment-guide-customizations-removing-config}

It is not recommended to remove and component, however you can remove any configuration from the stack, provided there is no direct dependency in later configurations, by selecting the **Remove from Stack** option in the right side menu for the corresponding configuration.

This applies to the following configurations:
- Observability
- {{site.data.keyword.compliance_short}}
- {{site.data.keyword.secrets-manager_short}}

![edit config](images/ccs_remove_component.png)

### Managing stack-Level inputs and outputs
{: #deployment-guide-customizations-managing-inputs-outputs}

You can add or remove inputs and outputs surfaced at the stack level by following these steps:
1. Select the stack configuration

    ![stack definition](images/ccs_define_stack.png)
1. You are presented with a screen allowing you to promote any of the configuration inputs or outputs at the stack level

    ![stack definition](images/ccs_edit_stack_definition_config.png)

### Sharing modified stacks through a private {{site.data.keyword.cloud_notm}} catalog
{: #deployment-guide-customizations-sharing-stacks}

After you make modifications to your stack in the project, you can share it with others through a private {{site.data.keyword.cloud_notm}} catalog. To do so, follow these steps:
1. Deploy the stack at least once: You need to deploy the stack first to allow importing the stack definition to a private catalog.
1. Select the **Add to private catalog** option in the menu on the stack configuration.

This will allow you to share your modified stack with others through a private {{site.data.keyword.cloud_notm}} catalog.

## Undeploying the Stack, and all associated infrastructure resources
{: #deployment-guide-undeploy}

### Undeploying infrastructure
{: #deployment-guide-undeploy-infrastructure}

The deployable architecture can be deployed only with an API key associated with a user. It is not compatible with API keys associated with a service ID. Additionally, it cannot be deployed using the project trusted profile support.
{: tip}

You might see notifications in {{site.data.keyword.cloud_notm}} Project indicating that one or more configurations in the stack have new versions available. You can safely ignore these messages because they do not prevent you from deploying the stack. No specific action is required from you. These notifications are expected, as we are rapidly iterating on the development of the underlying components. As new stack versions become available, the versions of the underlying components will also be updated.
{: note}

To undeploy the infrastructure created by the automation, complete the following steps:

#### 1. Undeploy configurations in the project
{: #deployment-guide-undeploy-configs}

Undeploy each configuration in the project, one by one, through the UI, starting from the `4b - core-security-services-sm` and working your way up in the stack up to, and inclusive of `1 - core-security-services-kms`. Wait for full undeployment of a configuration before starting to undeploy the next configuration up in the stack.

#### 3. Delete reclamation claims
{: #deployment-guide-undeploy-reclamation}

Before undeploying the `1 - core-security-services-kms`, you need to delete the reclamation claims for the resources deleted from the previous steps. Reclamation allows you to restore deleted resources for up to one week. However, any reclamation that is still active prevents from deleting the resource group managed by the `1 - core-security-services-kms`:

- Log in to the target {{site.data.keyword.cloud_notm}} account with the CLI
- Run `ibmcloud resource reclamations` to view the full list of reclamation. You can identify the exact reclamations to delete as they are planned to be deleted in one week after the date for which the resource was deleted.
- For each reclamation, execute `ibmcloud resource reclamation-delete <reclamation-id>`. The reclamation-id is the ID provided in the results from ibmcloud resource reclamations listing.
- Run `ibmcloud resource reclamations` again to ensure the reclamations have been fully deleted

More details are available [here](/docs/account?topic=account-resource-reclamation&interface=cli).

#### 4. Undeploy `1 - core-security-services-kms`
{: #deployment-guide-undeploy-kms}

You can now undeploy `1 - core-security-services-kms` in the project.

#### 5. Delete project
{: #deployment-guide-undeploy-project}

After all configurations are undeployed, you can delete the project. You can also delete the project first to delete all configurations if you do not want to delete stacks one by one.
