---

copyright:
  years: 2024
lastupdated: "2024-07-01"

keywords: security services, deployable architecture, IaC

subcollection: security-services

---

{{site.data.keyword.attribute-definition-list}}

# Release notes for the Core Security Services deployable architecture
{: #css-relnotes}

Use these release notes to learn about the latest updates to the core security services deployable architecture. The entries are grouped by date.
{: shortdesc}

## July 2024
{: #css-2024-07}

### 1 July 2024
{: #css-jul-0124}
{: release-note}

Version 1.1.1 of the Core Security Services deployable architecture is available
:   The Core Security Services deployable architecture version 1.1.1 [is released](/catalog#reference_architecture){: external}.

    - In this version, a {{site.data.keyword.secrets-manager_short}} event notification destination and topic are created in the {{site.data.keyword.en_short}} instance that is created by the deployable architecture. Email subscriptions are also configured for the new destination and topic from the list of emails that is passed in the `en_email_list` input.
    - The attachment that is created by the {{site.data.keyword.compliance_short}} member is updated to use the CIS IBM Cloud Foundations Benchmark v1.1.0 profile because version 1.0.0 is deprecated.

        You must update the profile attachment input value in the `4a - Security and Compliance Center` member configuration to `CIS IBM Cloud Foundations Benchmark v1.1.0` when you update. For more information, see [Updating to version 1.1.1](/docs/security-services?topic=security-services-known-issues#ki-update-profile) in Known issues.
        {: important}

## June 2024
{: #css-2024-06}

### 24 June 2024
{: #css-jun-2424}
{: release-note}

Introducing the Core Security Services deployable architecture
:   The Core Security Services deployable architecture [is released](/catalog#reference_architecture){: external}: The deployable architecture deploys the following core security services: {{site.data.keyword.keymanagementserviceshort}}, {{site.data.keyword.secrets-manager_short}}, {{site.data.keyword.compliance_short}}, and {{site.data.keyword.sysdigsecure_full_notm}}. The deployable architecture also deploys {{site.data.keyword.en_short}} and Observability.

    For more information about using deployable architectures with projects, see the blog posts [Projects and Cost Estimation: How IBM Cloud is Revolutionizing Complex Workloads for Enterprises](https://www.ibm.com/blog/announcement/projects-and-cost-estimation/) and [Turn Your Terraform Templates into Deployable Architectures](https://www.ibm.com/blog/turn-your-terraform-templates-into-deployable-architectures/).
