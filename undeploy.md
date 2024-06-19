---

copyright:
  years: 2024
lastupdated: "2024-06-19"

keywords: security services, deployable architecture, IaC

subcollection: security-services

---

{{site.data.keyword.attribute-definition-list}}

# Undeploying the deployable architecture
{: #undeploy}

Delete the stacked deployable architecture and all associated infrastructure resources.
{: shortdesc}

The deployable architecture can be deployed only with an API key associated with a user. It is not compatible with API keys associated with a service ID. Additionally, the deployable architecture can't be undeployed by using the project trusted profile support.

To undeploy the infrastructure created by the deployable architecture, complete the following steps:

You can also delete the project first to delete all member configurations if you do not want to delete stacks one by one.
{: tip}

1.  [Install or update](/docs/cli?topic=cli-getting-started) the {{site.data.keyword.cloud_notm}} CLI.
1.  From the project dashboard, select the **Configurations** tab.
1.  Undeploy the member configurations in the project:

    1.  Undeploy the `4b - Secrets Manager` configuration member. Wait for the undeploy to complete.
    1.  Undeploy the next member configuration. Wait for the undeploy to complete.
    1.  Continue to undeploy the configurations, but wait for each undeploy to complete before you undeploy the next.

        Stop after the `2 - Observability` member configuration.
1.  Delete the reclamation claims.

    Before you undeploy the `1 - Key management` member configuration, delete the reclamation claims for the resources that you deleted in the previous step. Any reclamation that is still active prevents you from deleting the resource group that is managed by the top member configuration. Through reclamation, you can restore deleted resources for up to one week from when you delete them.

    For more information, see [Using resource reclamations](/docs/account?topic=account-resource-reclamation&interface=cli).

    1.  Log in to the target {{site.data.keyword.cloud_notm}} account with the {{site.data.keyword.cloud_notm}} CLI.
    1.  Run the following command to view the list of reclamations and get the reclamation IDs:

        ```sh
        ibmcloud resource reclamations
        ```

    1.  Run the following command for each reclamation ID that you want to delete:

        ```sh
        ibmcloud resource reclamation-delete <reclamation-id>
        ```

    1.  Run the command to list the reclamations again to confirm that all are deleted:

        ```sh
        ibmcloud resource reclamations
        ```

1.  Undeploy the  `1 - Key management` member configuration.
1.  Delete your project.

    After all configurations are undeployed, you can delete the project.
