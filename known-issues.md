---

copyright:
  years: 2024
lastupdated: "2024-07-09"

keywords: security services, deployable architecture, IaC

subcollection: security-services

---

{{site.data.keyword.attribute-definition-list}}

# Known issues with {{site.data.keyword.name-da}} deployable architectures
{: #known-issues}

Because issues change frequently, check this list regularly.
{: shortdesc}

## Validation of 4a - Security and Compliance Center fails in version 1.0.0
{: #ki-scc-fail}

Because the CIS IBM Cloud Foundations Benchmark profile was renamed, validation fails for the `4a - Security and Compliance Center` member of the deployable architecture stack with the following error:

```hcl
 2024/06/29 17:43:41 Terraform apply | Error: Invalid function argument
 2024/06/29 17:43:41 Terraform apply |
 2024/06/29 17:43:41 Terraform apply |   on .terraform/modules/create_profile_attachment/modules/attachment/main.tf line 28, in locals:
 2024/06/29 17:43:41 Terraform apply |   28:   validate_profile = lookup(local.profile_map, var.profile_name, null) == null ? tobool("Could not find a valid profile name ${var.profile_name} and matching version ${var.profile_version}") : true
 2024/06/29 17:43:41 Terraform apply |     ├────────────────
 2024/06/29 17:43:41 Terraform apply |     │ while calling tobool(v)
 2024/06/29 17:43:41 Terraform apply |     │ var.profile_name is "CIS IBM Cloud Foundations Benchmark"
 2024/06/29 17:43:41 Terraform apply |     │ var.profile_version is "latest"
 2024/06/29 17:43:41 Terraform apply |
 2024/06/29 17:43:41 Terraform apply | Invalid value for "v" parameter: cannot convert "Could not find a valid
 2024/06/29 17:43:41 Terraform apply | profile name CIS IBM Cloud Foundations Benchmark and matching version latest"
 2024/06/29 17:43:41 Terraform apply | to bool; only the strings "true" or "false" are allowed.
 ```
{: screen}

To fix the error, follow these steps in [Updating to version 1.1.1](#ki-update-profile) to update to a later version. If you're not ready to update your deployable architecture, follow only the steps that update the **profile_attachments** input variable and validate the configuration.

## Updating to version 1.1.1
{: #ki-update-profile}

Because of an issue with projects, the value for the **profile_attachments** input in the `4a - Security and Compliance Center` member configuration is not updated when you update to version 1.1.1 of the {{site.data.keyword.name-da}} deployable architecture.

Follow these steps to update the profile attachment:

1.  In the {{site.data.keyword.cloud_notm}} console, click the **Navigation menu** icon ![Navigation menu icon](../icons/icon_hamburger.svg "Menu") > **Projects**.
1.  Click the project with the stacked deployable architecture that you want to update.
1.  Click the **Configurations** tab.
1.  In the row for the deployable architecture configuration, click the **Options** icon ![Options icon](../icons/action-menu-icon.svg "Options") for the stack and select **Edit**.
1.  Select the new version in the **Define details** section and click **Save**.
1.  In the row for the member configuration named `4a - Security and Compliance Center`, click the **Options** icon ![Options icon](../icons/action-menu-icon.svg "Options") and select **Edit**.
1.  Click the **Optional** tab in the **Configure** section.
1.  Find the **profile_attachments** input variable and click the **Edit** icon ![Edit icon](../icons/edit-tagging.svg "Edit").
1.  Replace the profile name in the array with the following value:

    ```json
    [
      "CIS IBM Cloud Foundations Benchmark v1.1.0"
    ]
    ```
    {: codeblock}

1.  Click **Save**.
1.  Follow the steps in [Step 3. Validate and deploy the architecture](/docs/security-services?topic=security-services-deploy-css#deploy-validate) to upgrade the deployable architecture stack to version.

## Object Storage buckets deployed without activity tracking
{: #ki-cos-no-at}

Because of a limitation with the IBM Terraform provider, activity tracking is not enabled for {{site.data.keyword.cos_full_notm}} buckets that are created by the {{site.data.keyword.name-da}} deployable architecture. After the provider supports the feature, a new version of the deployable architecture will be released.

## Error when you try to undeploy key management
{: #ki-kms-undeploy}

When you try to undeploy the key management member of the deployable architecture, you might see an error that's similar to the following error:

```hcl
"Result": {
  "details": "{\"status_code\":409,\"name\":\"ConflictError\",\"message\":{\"message\":\"CONTAINS_ACTIVE_KEYS: Remove all keys before de-provisioning: Instance contains 4 active keys\",\"name\":\"ConflictError\",\"status_code\":409,\"transaction_id\":\"\"},\"description\":\"CONTAINS_ACTIVE_KEYS: Remove all keys before de-provisioning: Instance contains 4 active keys\"}",
  "error_code": "RC-ServiceBrokerErrorResponse",
  "message": "Please contact the Service Provider for this error. [409, Conflict] CONTAINS_ACTIVE_KEYS: Remove all keys before de-provisioning: Instance contains 4 active keys",
  "status_code": 422,
  "transaction_id": "bss-bc223e693444d810"
}
```
{: screen}

To finish undeploying, wait for about 15 minutes and then retry.
