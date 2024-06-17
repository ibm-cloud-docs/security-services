---

copyright:
  years: 2024
lastupdated: "2024-06-17"

keywords: security services, deployable architecture, IaC

subcollection: security-services

---

{{site.data.keyword.attribute-definition-list}}

# Overview of Core Security Services Deployable Architecture (Stack)
{: #overview}

The Core Security Services Deployable Architecture is a preconfigured set of infrastructure as code (IaC) assets that are deployed and configured based on the recommended best practices. IBM Cloud's core security services are crucial for ensuring robust security and compliance for cloud-based applications and data. Primary goal is to provide framework for secure and compliant IBM Cloud Workloads.

This deployable architecture is designed to showcase a fully automated deployment of IBM Cloud Core Security Services and its dependencies through IBM Cloud Project, providing a flexible and customizable foundation for your own application deployments on IBM Cloud.

By leveraging this architecture, you can accelerate your deployment and tailor it to meet your unique business needs and enterprise goals.

By using this architecture, you can:

* **Establish Trust:** The architecture ensures trust by configuring the IBM Cloud account to align with compliance settings as defined in the [Financial Services](/docs/framework-financial-services?topic=framework-financial-services-about) framework.
* **Ensure Observability:** The architecture provides observability by deploying services such as {{site.data.keyword.la_full_notm}}, {{site.data.keyword.monitoringlong_notm}}, {{site.data.keyword.atracker_full_notm}}, and log retention through {{site.data.keyword.cos_full_notm}} buckets.
* **Implement Security:** The architecture ensures security by deploying IBM Key Protect and IBM Secrets Manager.
* **Achieve Regulatory Compliance:** The architecture ensures regulatory compliance by implementing centralize Key Management, centralize secrets management, and along with IBM Security Compliance Center and Workload Protection (SCC) for secure application lifecycle management.

This deployable architecture supports these features:

## Features and capabilities
{: #overview-features}

* Creates and configures an IBM Key Protect instance and creates root keys for IBM Cloud Object Storage, Event Notifications, and Secrets Manager.
* Creates and configures an IBM Secrets Manager instance.
* Creates and configures an IBM Security Compliance Center instance.
* Creates and configures an Security and Compliance Center with Workload Protection instance.
* Creates and configures an IBM Cloud Object Storage instance and multiple Object Storage buckets that is encrypted by Key Protect.
* Creates and configures service-to-service authorizations for the following services: KMS, Event Notifications, Object Storage, Secrets Manager, and Security and Compliance Center.
* Creates and configures IBM Observability components Activity Tracker Event Routing, IBM Cloub Monitoring, and IBM Log Analysis.
* Ensures compliance to CIS IBM Cloud Foundations [Benchmark profile](/docs/security-compliance?topic=security-compliance-cis-benchmark-profile) Specific controls:
  * Ensure Cloud Object Storage encryption is enabled with BYOK
  * Ensure Activity Tracker data is encrypted at rest
  * Ensure Activity Tracker trails are integrated with LogDNA Logs
  * Ensure IBM Key Protect has automated rotation for customer managed keys enabled
  * Ensure the IBM Key Protect service has high availability
