---

copyright:
  years: 2026
lastupdated: "2026-09-23"

subcollection: pattern-intra-org-multitenancy
keywords: multitenancy, multitenant, IBM Cloud, VPC isolation, namespace isolation, worker pool, application native

content-type: overview

---

{{site.data.keyword.attribute-definition-list}}

# Multitenant management in {{site.data.keyword.IBM_notm}}
{: #overview}

This pattern presents a set of architectural alternatives for delivering autonomy of individual business unit workloads while supporting centralized common services and operations. The result is an approach that treats the individual business units as multiple tenants within the enterprise cloud platform.
{: shortdesc}

As explained in [Organizing IBM Cloud accounts and resources](/docs/framework-financial-services?topic=framework-financial-services-shared-account-organization), each deployment of one of the reference architectures is single tenant, which means the deployment is intended for a single customer. However, there are some cases where you might need different business units in the same organization to be managed by the same operator.

## Approaches and recommendations
{: #approaches-recs}

What are the different approaches that you can use to help you deploy an application for multiple users within your organization? This pattern outlines the four following approaches:

VPC-based isolation
:   One of the recommended models for implementing multitenancy, isolating tenants by VPCs is a scalable approach with isolation benefits. For more information, see [Isolating VPCs](/docs/pattern-intra-org-multitenancy?topic=pattern-intra-org-multitenancy-VPC).

Application native multitenancy
:   Another recommended approach uses the application itself to handle tenant isolation. This approach is the most flexible but the most difficult to secure. Similar to VPC-based isolation, it's a scalable approach that's common in SaaS platforms that use shared backend services. For more information, see [Application native multitenancy](/docs/pattern-intra-org-multitenancy?topic=pattern-intra-org-multitenancy-app-native).

Namespace-based isolation
:   In this approach, tenants share a cluster but use namespaces for logical separation of resources between the tenants. This approach poses risks, such as single points of failure, noisy neighbor problems, and heightened demands for operational and security enforcement. For more information, see [Isolating namespaces](/docs/pattern-intra-org-multitenancy?topic=pattern-intra-org-multitenancy-namespace).

Worker pool isolation
:   Similar to isolating with namespaces, tenants in this approach share a cluster but use dedicated node pools, also known as worker pools, for isolation. This approach can be efficient for internal teams with different workload profiles, but doesn't provide any advantages over VPC-based isolation. For more information, see [Isolating worker pools](/docs/pattern-intra-org-multitenancy?topic=pattern-intra-org-multitenancy-worker-pool).

Other approaches that aren't outlined in detail in this pattern include account-based isolation, where each tenant has a separate account. While this approach includes the strongest isolation, adopting it can lead to increased operational complexity for your organization. And, similar to worker pool isolation, tenants can also share a VPC but run workloads in separate, dedicated Kubernetes clusters. This approach doesn't provide any significant advantages over VPC-based isolation.

The following image illustrates the breakdown of factors and data that was used to evaluate these multitenant strategies.

![Spider diagram showing evaluation factors for each multitenancy approach across five dimensions](images/spider.svg){: caption="Factors influencing decisions" caption-side="bottom"}
