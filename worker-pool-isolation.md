---
copyright:
  years: 2025
lastupdated: "2025-09-12"

subcollection: pattern-intra-org-multitenancy
keywords:

---

{{site.data.keyword.attribute-definition-list}}
# Worker Pool isolation
![Worker pool based isolation reference](/images/worker-pool-isolation.svg){: caption="Worker pool based isolation" caption-side="bottom"}

## Advantages
- **Easier for chargeback**

- **Noisy neighbor problem prevention**

- **Standardized management processes, tools, and monitoring across a unified environment**

- May **streamline updates and patches** by applying them once across a single cluster, reducing maintenance efforts and potential errors

- **Decreased administrative tasks** compared to cluster-based setups
- May **reduce complexity** by managing one cluster instead of multiple



## Challenges
- **Higher operational expenses**

- **Underutilized resources**

- **Increased administrative tasks**  
  _(Can be overcome with appropriate automations in place)_

- **Does not provide cost advantage** over cluster/VPC-based isolation

- **All tenants will be impacted** by cluster issues



## Determine suitability
- **Can the organization support the cost for running separate clusters for each environment?**

- **Does the workload require cluster-level isolation for strict regulatory compliance?**

- **Does the deployment need tenant-specific IAM & policies per environment?**

- **Is cross-tenant access prevention critical at the network level?**

- **Is separate VPN or Direct Link required for each tenant’s connectivity needs?**

- **Do different versions or configurations need to be maintained per tenant?**

- **Is there a requirement for better blast radius control?**

- **Do data residency regulations require physical data separation per tenant?**
