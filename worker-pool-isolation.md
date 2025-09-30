---
copyright:
  years: 2025
lastupdated: "2025-09-24"

subcollection: pattern-intra-org-multitenancy
keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Isolating worker pools 
{: #worker-pool}

Isolating tenants by using worker pools involves multiple tenants that share a cluster, but use dedicated node pools, also known as worker pools, in isolation from other tenants. 
{: shortdesc}

![Worker pool-based isolation reference](/images/worker-pool-isolation.svg){: caption="Worker pool based isolation" caption-side="bottom"}

## Advantages
{: #advantages}

Worker pool isolation as a strategy includes the following advantages: 

- Easier to calculate chargebacks than other approaches. 
- Prevents the noisy neighbor problem. 
- Standardized management processes, tools, and monitoring across a unified environment. 
- Can streamline updates and fixes by applying them one time across a single cluster, reducing maintenance efforts and potential errors. 
- Decreased administrative tasks compared to cluster-based setups. 
- Can reduce complexity by managing one cluster instead of many. 


## Challenges
{: #challenges}

Isolating worker pools includes the following challenges for teams: 

- Higher operational expenses. 
- Underutilized resources. 
- Increased administrative tasks, which can be mitigated by using infrastructure-as-code automation. 
- There is no cost advantage over cluster or VPC-based isolation. 
- All tenants are impacted by cluster issues. 


## Determine suitability
{: #suitability}

As you evaluate worker pool-based isolation, consider the following questions:

- Can the organization support the cost for running separate clusters for each environment?
- Does the workload require cluster-level isolation for strict regulatory compliance?
- Does the deployment need tenant-specific IAM policies per environment?
- Is cross-tenant access prevention critical at the network level?
- Is a separate VPN or Direct Link required for each tenant’s connectivity needs?
- Do different versions or configurations need to be maintained per tenant?
- Is there a requirement for better blast radius control?
- Do data residency regulations require physical data separation per tenant?
