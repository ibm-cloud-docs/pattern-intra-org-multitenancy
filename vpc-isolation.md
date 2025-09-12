---
copyright:
  years: 2025
lastupdated: "2025-09-12"

subcollection: pattern-intra-org-multitenancy
keywords:

---

{{site.data.keyword.attribute-definition-list}}
# VPC isolation

![VPC based isolation reference](/images/current-guidance.drawio.svg){: caption="VPC based isolation" caption-side="bottom"}

## Advantages
- **Full isolation for security and performance**
- **Dedicated resources**, tailored configurations & operational independence (networking, storage)
- **Easier for chargeback**
- **Noisy neighbor problem prevention**
- **More predictable network performance**
- **Independent scaling for each tenant**
- **Better disaster recovery & fault isolation**
- **Updates are isolated** and hence do not impact all tenants
- Could provide **tenant-specific SCC scans** at infrastructure level


## Challenges
- **Higher operational expenses**
  _Solution: Automation via IaC_

- **Underutilized resources**

- **Increased administrative tasks**  
  _Solution: Automation via IaC_

- **IP address planning**


## Determine suitability
- **Can the organization support the cost for running separate clusters for each environment?**

- **Does the workload require cluster-level isolation for strict regulatory compliance?**

- **Does the deployment need tenant-specific IAM & policies per environment?**

- **Is cross-tenant access prevention critical at the network level?**

- **Is separate VPN or Direct Link required for each tenant’s connectivity needs?**

- **Do different versions or configurations need to be maintained per tenant?**

- **Is there a requirement for better blast radius control?**

- **Do data residency regulations require physical data separation per tenant?**
