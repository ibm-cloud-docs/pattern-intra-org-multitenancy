---
copyright:
  years: 2025
lastupdated: "2025-08-21"

subcollection: pattern-intra-org-multitenancy

keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Considerations
{: #current}


# Key considerations for evaluating multi-tenancy options


In multi-tenant cloud architectures, **security and compliance** are foundational. Organizations must adhere to regulations governing data protection, encryption standards, and the handling of sensitive information. This includes ensuring that tenant data is encrypted both in transit and at rest, and that access controls are strictly enforced to meet compliance requirements across jurisdictions.

**Data segregation** is critical to prevent co-mingling of data between tenants. Effective controls and processes must be in place to ensure that each tenant’s data remains isolated, especially when shared infrastructure is used. This includes clear policies around key ownership and account management to maintain data boundaries and accountability.

Given the shared nature of the environment, **auditability** becomes essential. Tenants may request detailed reports on activities involving their data. Therefore, systems must be designed to support ad-hoc audit reporting, enabling transparency and trust. This includes logging access and changes at a granular level and associating them with specific tenants.

**Capacity and workload management** must be architected to meet the service-level agreements (SLAs) of all tenants, particularly during peak usage periods. Shared management planes and tools should be resilient and scalable, with mechanisms to prioritize workloads and prevent resource contention.

Security risks such as the **propagation of vulnerabilities** from a common management VPC to tenant environments must be mitigated. Isolation mechanisms and strict access controls should be in place to prevent lateral movement of threats. Similarly, the **compromise of the management VPC** could expose multiple tenants to risk, so robust security measures—including monitoring, intrusion detection, and least-privilege access—are essential.

**Change management** in a shared environment requires careful coordination. Updates to common tools or infrastructure must be communicated and tested to avoid unintended impacts on tenant workloads. This includes version control, rollback procedures, and tenant-specific validation.

Finally, **operational and financial efficiency** must be balanced. Performance needs and scalability should be addressed through elastic infrastructure and intelligent workload distribution. Monitoring, troubleshooting, and maintenance must be streamlined to support multiple tenants without degradation. And from a financial perspective, cost efficiency should be achieved through thoughtful trade-offs between shared and dedicated resources, with mechanisms for chargeback or showback to ensure transparency in billing.
