---
copyright:
  years: 2025
lastupdated: "2025-09-24"

subcollection: pattern-intra-org-multitenancy

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Key considerations for evaluating multi-tenancy options
{: #considerations}

There are a set of key considerations and decisions that you might need to make as you evaluate multi-tenant options for your organization.
{: shortdesc}

Security and compliance
:   In multi-tenant cloud architectures, security and compliance are foundational. Organizations must adhere to regulations that govern data protection, encryption standards, and the handling of sensitive information. This practice includes helping ensure that tenant data is encrypted both in transit and at rest, and that access controls are strictly enforced to meet compliance requirements across jurisdictions.

Data separation
:   Data separation is critical to prevent co-mingling of data between tenants. Effective controls and processes must be in place to help ensure that each tenant’s data remains isolated, especially when shared infrastructure is used. This includes clear policies around key ownership and account management to maintain data boundaries and accountability.

Auditability
:   Given the shared nature of the environment, auditability becomes essential. Tenants can request detailed reports on activities that involve their data. Therefore, systems must be designed to support ad hoc audit reporting, which helps enable transparency and trust. This includes logging access and changes at a granular level and associating them with specific tenants.

Capacity and workload management
:   Capacity and workload management must be designed to meet the service-level agreements (SLAs) of all tenants, particularly during peak usage periods. Shared management planes and tools should be resilient and scalable, with mechanisms to prioritize workloads and prevent resource contention.

Mitigating security concerns
:   Security risks such as the propagation of vulnerabilities from a common management VPC to tenant environments must be mitigated. Isolation mechanisms and strict access controls should be in place to prevent lateral movement of threats. Similarly, if a management VPC is compromised, it might place multiple tenants at risk, so robust security measures that include monitoring, intrusion detection, and least-privilege access are essential.

Change management
:   Change management in a shared environment requires careful coordination. Updates to common tools or infrastructure must be communicated and tested to avoid unintended impacts on tenant workloads. This includes version control, rollback procedures, and tenant-specific validation.

Operational and financial efficiency
:   Operational and financial efficiency must be balanced. Performance needs and scalability should be addressed through elastic infrastructure and intelligent workload distribution. Monitoring, troubleshooting, and maintenance must be streamlined to support multiple tenants without degradation. And from a financial perspective, cost efficiency should be achieved through thoughtful tradeoffs between shared and dedicated resources, with mechanisms for chargeback or showback to help ensure transparency in billing.

Degree of consolidation
:   The degree of consolidation refers to how efficiently infrastructure can be shared across multiple deployments or tenants, with approaches higher in the stack generally supporting more tenants on the same infrastructure. Conversely, the degree of isolation improves as one moves lower in the stack, offering stronger security and performance boundaries between tenants. Provisioning ease is typically greater with logical isolation methods implemented higher up, allowing faster creation of new tenants and more flexible resource adjustments. However, the impact of failures, whether due to unplanned hardware issues or planned updates, tends to be broader with higher-stack approaches, potentially affecting multiple tenants. Whereas lower-stack methods can localize the impact to individual tenants.

![Consolidation vs isolation](/images/degree-diagram.svg){: caption="Consolidation vs isolation" caption-side="bottom"}
