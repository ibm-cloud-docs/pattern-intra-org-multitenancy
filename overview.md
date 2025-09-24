---

copyright:
  years: 2025
lastupdated: "2025-09-24"

subcollection: pattern-intra-org-multitenancy
keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Multi-tenant management in {{site.data.keyword.IBM_notm}}
{: #overview}

Learn the basic principles to help you deploy an application to be used by multiple users within your organization.
{: shortdesc}

As explained in [Organizing IBM Cloud accounts and resources](/docs/framework-financial-services?topic=framework-financial-services-shared-account-organization), each deployment is intended for a single customer. However, there are some cases where you might need different business units in the same organization to be managed by the same operator.

This pattern presents a set of architectural alternatives for delivering autonomy of individual business unit workloads while supporting centralized common services and operations. The result is an approach that treats the individual business units as multiple tenants within the enterprise cloud platform.
