---

copyright:
  years: 2024
lastupdated: "2024-07-29"

keywords: security services, deployable architecture, IaC

subcollection: security-services

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for the {{site.data.keyword.name-da}} deployable architecture
{: #css-relnotes}

Use these release notes to learn about the latest updates to the {{site.data.keyword.name-da}} deployable architecture. The entries are grouped by date.
{: shortdesc}



## July 2024
{: #css-2024-07}

### 29 July 2024
{: #css-jul-2924}
{: release-note}

Version 1.2.1 of the {{site.data.keyword.name-da}} deployable architecture is available
:   The {{site.data.keyword.name-da}} deployable architecture version 1.2.1 [is released](/catalog#deployable_architecture){: external}.

     - When you upgrade, all deployable architectures members are updated to their latest versions.
     - A new `existing_kms_instance_crn` input variable adds support to use an existing key management service instance. By default, a new {{site.data.keyword.keymanagementserviceshort}} instance is created.
     - Fixes an issue in which activity tracking was not enabled for {{site.data.keyword.cos_full_notm}} buckets. By default, {{site.data.keyword.cos_short}} buckets that are created by the deployable architecture now have activity tracking enabled. When you upgrade, existing buckets are updated when you upgrade to this version.
     - Fixes an issue in which the {{site.data.keyword.en_short}} member created {{site.data.keyword.cos_short}} destinations instead of {{site.data.keyword.cos_short}} integrations that are needed to store failed events. When you upgrade, these destinations are destroyed.

### 1 July 2024
{: #css-jul-0124}
{: release-note}

Version 1.1.1 of the {{site.data.keyword.name-da}} deployable architecture is available
:   The {{site.data.keyword.name-da}} deployable architecture version 1.1.1 [is released](/catalog#deployable_architecture){: external}.

    - In this version, a {{site.data.keyword.secrets-manager_short}} event notification destination and topic are created in the {{site.data.keyword.en_short}} instance that is created by the deployable architecture. Email subscriptions are also configured for the new destination and topic from the list of emails that is passed in the `en_email_list` input.
    - The attachment that is created by the {{site.data.keyword.compliance_short}} member is updated to use the CIS IBM Cloud Foundations Benchmark v1.1.0 profile because version 1.0.0 is deprecated.

        You must update the profile attachment input value in the `4a - Security and Compliance Center` member configuration to `CIS IBM Cloud Foundations Benchmark v1.1.0` when you update. For more information, see [Updating to version 1.1.1](/docs/security-services?topic=security-services-known-issues#ki-update-profile) in Known issues.
        {: important}

## June 2024
{: #css-2024-06}

### 24 June 2024
{: #css-jun-2424}
{: release-note}

Introducing the {{site.data.keyword.name-da}} deployable architecture
:   The {{site.data.keyword.name-da}} deployable architecture [is released](/catalog#deployable_architecture){: external}: The deployable architecture deploys the following {{site.data.keyword.name-da}}: {{site.data.keyword.keymanagementserviceshort}}, {{site.data.keyword.secrets-manager_short}}, {{site.data.keyword.compliance_short}}, and {{site.data.keyword.sysdigsecure_full_notm}}. The deployable architecture also deploys {{site.data.keyword.en_short}} and Observability.

    For more information about using deployable architectures with projects, see the blog posts [Projects and Cost Estimation: How IBM Cloud is Revolutionizing Complex Workloads for Enterprises](https://www.ibm.com/blog/announcement/projects-and-cost-estimation/) and [Turn Your Terraform Templates into Deployable Architectures](https://www.ibm.com/blog/turn-your-terraform-templates-into-deployable-architectures/).
