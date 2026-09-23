---
copyright:
  years: 2026
lastupdated: "2026-09-23"

subcollection: pattern-intra-org-multitenancy

keywords: multitenancy, VPC isolation, key management, HPCS, Transit Gateway, security groups, IBM Cloud

content-type: overview

---

{{site.data.keyword.attribute-definition-list}}

# Guidance for candidate tenants
{: #guidance}

Brush up on primary guidance for multitenancy in the cloud.
{: shortdesc}

## Isolating workloads and sharing infrastructure
{: #isolating-sharing}

To help ensure secure and efficient workload deployments, each business unit should operate within its own isolated Virtual Private Cloud (VPC). This isolation allows for tailored configurations and prevents cross-tenant interference. While workloads are separated, management and edge components can be shared across environments to optimize resource usage. Each business unit benefits from a dedicated workload environment and uses shared infrastructure for centralized control and scalability.

## Handling nontenant data
{: #hand-non-tenant}

IBM Cloud services that handle nontenant data such as security information and event management (SIEM), {{site.data.keyword.monitoringlong_notm}}, {{site.data.keyword.at_full_notm}}, and {{site.data.keyword.logs_full_notm}} can be shared across business units to streamline operations and reduce redundancy. Similarly, Cloud Internet Services (CIS) can be configured to route traffic to each business unit, maintaining logical separation and benefiting from shared capabilities. However, for tenant-specific data it's crucial to provision separate instances, such as {{site.data.keyword.cloud_notm}} Databases (ICD), to help ensure data privacy and compliance.

## Encrypting keys
{: #kms}

Encryption services like {{site.data.keyword.hscrypto_full_notm}} (HPCS) can be shared by using key rings, which allows secure key management across business units. Each VPC should maintain its own set of Virtual Private Endpoints (VPEs) to control access and traffic flow. DNS services can be shared between VPCs to simplify name resolution, but care must be taken to prevent unintended exposure. Noncritical environments like QA or UAT should be treated as separate business units to maintain consistency in governance and isolation.

## Connecting securely
{: #connect-secure}

To support secure connectivity and avoid conflicts, subnet ranges within each VPC must be nonoverlapping, especially when a Transit Gateway (TGW) is used for interconnectivity. Access Control Lists (ACLs) and Security Groups (SGs) should be configured to prevent inter-tenant communication, reinforcing isolation and minimizing risk. These guidelines collectively help ensure a robust, scalable, and secure multitenant architecture on {{site.data.keyword.cloud_notm}}.
