---
copyright:
  years: 2025
lastupdated: "2025-08-25"

subcollection: pattern-intra-org-multitenancy

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Current guidance for Independent Software Vendors (ISV)
{: #guidance}

To ensure secure and efficient workload deployment, each Business Unit (BU) should operate within its own isolated Virtual Private Cloud (VPC). This isolation allows for tailored configurations and prevents cross-tenant interference. While workloads are separated, management and edge components can be shared across environments to optimize resource usage. Each BU benefits from a dedicated workload environment while leveraging shared infrastructure for centralized control and scalability.

IBM Cloud services that handle non-tenant data—such as SIEM, Monitoring, AT Routing, and Cloud Logs—can be shared across BUs to streamline operations and reduce redundancy. Similarly, the Cloud Internet Services (CIS) can be configured to route traffic appropriately to each BU, maintaining logical separation while benefiting from shared capabilities. For tenant-specific data, however, it’s crucial to provision separate instances, such as IBM Cloud Databases (ICD), to ensure data privacy and compliance.

Encryption services like Hyper Protect Crypto Services (HPCS) can be shared using Keyrings, allowing secure key management across BUs. Each VPC should maintain its own set of Virtual Private Endpoints (VPEs) to control access and traffic flow. DNS services can be shared between VPCs to simplify name resolution, but care must be taken to prevent unintended exposure. Non-critical environments like QA or UAT should be treated as separate BUs to maintain consistency in governance and isolation.

To support secure connectivity and avoid conflicts, subnet ranges within each VPC must be non-overlapping, especially when using Transit Gateway (TGW) for interconnectivity. Access Control Lists (ACLs) and Security Groups (SGs) should be configured to prevent inter-tenant communication, reinforcing isolation and minimizing risk. These measures collectively ensure a robust, scalable, and secure multi-tenant architecture on IBM Cloud.


![basic deployment diagram for VPC based environments](/images/current-guidance.jpg){: caption="Basic deployment diagram for VPC based environments" caption-side="bottom"}
