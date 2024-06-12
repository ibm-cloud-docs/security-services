---

copyright:
  years: 2024
lastupdated: "2024-06-12"

keywords: 

subcollection: security-services

---

{{site.data.keyword.attribute-definition-list}}

# My deployment failed, how do I proceed?
{: #ts-deploy}
{: troubleshoot}

Your deployment failed.
{: shortdesc}

You attempted to deploy an instance of a Core security services deployable architecture, but it failed.
{: tsSymptoms}

Several infrastructure layers and components are included in the deployment, and an issue in one of those pieces is causing the failure. 
{: tsCauses}

If the deployment process does not finish successfully, refer to the {{site.data.keyword.bplong_notm}} logs. These logs typically provide the information about the component that causes the issue.

If you can't deploy successfully, follow these steps:

1.  Check the values of the inputs.

    For example, from the **Configurations** tab in your project, click the name of your deployable architecture > **Edit**.
1.  Run the Schematics apply action again in {{site.data.keyword.bplong_notm}} by clicking **Apply plan** or by running the `ibmcloud schematics apply` command.

    1.  In the {{site.data.keyword.cloud_notm}} console, go to **Schematics** > **Workspaces** and select your instance of the deployable architecture.
    1.  Click **Apply plan**.

        This action resumes the job where it left off. In some cases, when the error occurs when creating a service, this second apply command is successful.

If the issue persists after the second apply, [open a case](/docs/security-services?topic=security-services-help-support#support-case-details) in the {{site.data.keyword.cloud_notm}} support center.
{: tsResolve}
