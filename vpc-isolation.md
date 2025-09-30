---
copyright:
  years: 2025
lastupdated: "2025-09-25"

subcollection: pattern-intra-org-multitenancy
keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Isolating VPCs
{: #VPC}

Isolating Virtual Private Clouds (VPC) is a multitenant strategy where each tenant operates within its own VPC.
{: shortdesc}

![VPC-based isolation reference](/images/current-guidance.svg){: caption="VPC-based isolation" caption-side="bottom"}

## Advantages
{: #advantages}

VPC-based isolation provides the following advantages for your organization:

- Full isolation for security and performance.
- Dedicated resources, tailored configurations, and operational independence (networking and storage).
- Easier to calculate chargebacks than other approaches.
- Prevents the noisy neighbor problem.
- More predictable network performance.
- Independent scaling for each tenant.
- Better disaster recovery and fault isolation than other approaches.
- Updates are isolated and do not impact all tenants.
- Might provide tenant-specific SCC scans at the infrastructure level.


## Challenges
{: #challenges}

VPC-based isolation includes the following challenges for your organization:

- Higher operational expenses and increased administrative tasks, both of which can be mitigated by using infrastructure-as-code automation.
- Underutilized resources.
- IP address planning.


## Determine suitability
{: #suitability}

As you evaluate VPC-based isolation, consider the following questions:

- Can your organization support the cost for running separate clusters for each environment?
- Does the workload require cluster-level isolation for strict regulatory compliance?
- Does the deployment need tenant-specific IAM policies per environment?
- Is cross-tenant access prevention critical at the network level?
- Is separate VPN or Direct Link required for each tenant’s connectivity needs?
- Do different versions or configurations need to be maintained per tenant?
- Is there a requirement for better blast radius control?
- Do data residency regulations require physical data separation per tenant?
