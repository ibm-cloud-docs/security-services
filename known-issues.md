---

copyright:
  years: 2024
lastupdated: "2024-08-29"

keywords: security services, deployable architecture, IaC

subcollection: security-services

---

{{site.data.keyword.attribute-definition-list}}

# Known issues with {{site.data.keyword.name-da}} deployable architectures
{: #known-issues}

Because issues change frequently, check this list regularly.
{: shortdesc}

## Error when you try to deploy 4a - {{site.data.keyword.compliance_short}}
{: #ki-scc-attachments}

When you try to deploy the `4a - Security and Compliance Center` member of the deployable architecture, you get the following error:

> Error: CreateAttachmentWithContext failed. Necessary attachment parameters are not available to create or update attachment.

The error is caused by an issue with the {{site.data.keyword.cloud_notm}} Terraform provider.

As a temporary workaround, you can remove the attachment. After the provider issue is resolved and a new version of the deployable architecture is released, you can add back the profile attachment. The release notes for that version will include information about this process.

To deploy successfully, follow these steps to update the profile attachment to an empty list:

1.  In the {{site.data.keyword.cloud_notm}} console, click the **Navigation menu** icon ![Navigation menu icon](../icons/icon_hamburger.svg "Menu") > **Projects**.
1.  Click the project with the stacked deployable architecture that you want to update.
1.  Click the **Configurations** tab.
1.  In the row for the member configuration named `4a - Security and Compliance Center`, click the **Options** icon ![Options icon](../icons/action-menu-icon.svg "Options") and select **Edit**.
1.  Click the **Optional** tab in the **Configure** section.
1.  Find the **profile_attachments** input variable and click the **Edit** icon ![Edit icon](../icons/edit-tagging.svg "Edit").
1.  Replace the profile name in the array with the following value (an empty list):

    ```json
    [
    ]
    ```
    {: codeblock}

1.  Click **Save**.
1.  Follow the steps in [Step 3. Validate and deploy the architecture](/docs/security-services?topic=security-services-deploy-css#deploy-validate) to validate and deploy the updated deployable architecture.

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
