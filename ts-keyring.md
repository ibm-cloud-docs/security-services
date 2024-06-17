---

copyright:
  years: 2024
lastupdated: "2024-06-17"

keywords:

subcollection: security-services

content-type: troubleshoot

---

{{site.data.keyword.attribute-definition-list}}

# Deployment fails due to a key ring error
{: #ts-deploy-key-ring}
{: troubleshoot}

Your deployment fails due to a key ring error.
{: shortdesc}

You receive the error: `ERROR` Error when creating resource instance: Please contact the Service Provider for this error. [500, Internal Server Error] Sysdig provision request return code: 500. Ensure the API Key used as "Editor" or "Administrator" permission for the Activity Tracker Event Routing service.
{: tsSymptoms}

* Key ring must have be between 2-100 characters with matching regular expression `^[a-zA-Z0-0-]*$`. Ensure the prefix used does not contain the invalid characters
{: tsCauses}

Update the prefix and revalidate the configuration.
{: tsResolve}
