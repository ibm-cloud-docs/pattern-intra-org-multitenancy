---
copyright:
  years: 2025
lastupdated: "2025-10-09"

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

### Readiness checklist
{: #checklist}

Use the following checklist to determine whether your organization is ready to pursue Virtual Private Cloud (VPC) multitenancy. 

| Task | Description |
|---|-------------|
| - [ ] **Strategic Alignment** | * Clear business case for multitenancy (e.g., cost optimization, scalability, tenant isolation). \n * Stakeholder buy-in across architecture, security, operations, and compliance teams. \n * Defined tenant models (e.g., per customer, per business unit, per environment). |
| - [ ] **Architecture & Design** | * Familiarity with IBM Cloud VPC architecture and components (subnets, routing tables, security groups, etc.). \n * Decision on tenancy model: **shared VPC** vs. **dedicated VPC per tenant**. \n * Blueprint for tenant isolation (network segmentation, IAM policies, resource tagging). \n * Plan for scalability and automation (e.g., Terraform, Schematics, IBM Cloud CLI). |
| - [ ] **Security & Compliance** | * Defined security boundaries between tenants (e.g., security groups, ACLs). \n * IAM roles and policies scoped per tenant. \n * Encryption strategy for data at rest and in transit. \n * Compliance requirements mapped to VPC capabilities (e.g., HIPAA, GDPR, SOC2). |
| - [ ] **Networking** | * IP address management strategy across tenants. \n * DNS and routing configuration per tenant. \n * VPN or Direct Link setup for hybrid connectivity if needed. \n * Firewall and traffic inspection policies. |
| - [ ] **Resource Management** | *  Resource tagging and naming conventions for tenant identification. \n * Quota and billing management per tenant. \n * Monitoring and logging strategy (e.g., LogDNA, Sysdig, Activity Tracker). \n * Backup and disaster recovery plans per tenant. |
| - [ ] **Automation & DevOps** | * Infrastructure as Code (IaC) templates for tenant provisioning. \n *  CI/CD pipelines adapted for multitenant deployments. \n * Tenant onboarding/offboarding workflows. |
| - [ ] **Operations & Support** | * Defined SLAs and support models per tenant. \n * Incident response and escalation procedures. \n * Tenant usage reporting and analytics. |
| - [ ] **Cost & Billing** | * Cost allocation strategy (e.g., resource tags, IBM Cloud billing reports). \n * Budgeting and forecasting tools in place. \n * Chargeback or showback models for internal or external tenants. |
{: caption="Readiness checklist for Virtual Private Cloud (VPC) multitenancy" caption-side="top"}
