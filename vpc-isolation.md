---
copyright:
  years: 2025
lastupdated: "2025-10-08"

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

## 1. Strategic Alignment
- [ ] Clear business case for multitenancy (e.g., cost optimization, scalability, tenant isolation).
- [ ] Stakeholder buy-in across architecture, security, operations, and compliance teams.
- [ ] Defined tenant models (e.g., per customer, per business unit, per environment).

## 2. Architecture & Design
- [ ] Familiarity with IBM Cloud VPC architecture and components (subnets, routing tables, security groups, etc.).
- [ ] Decision on tenancy model: **shared VPC** vs. **dedicated VPC per tenant**.
- [ ] Blueprint for tenant isolation (network segmentation, IAM policies, resource tagging).
- [ ] Plan for scalability and automation (e.g., Terraform, Schematics, IBM Cloud CLI).

## 3. Security & Compliance
- [ ] Defined security boundaries between tenants (e.g., security groups, ACLs).
- [ ] IAM roles and policies scoped per tenant.
- [ ] Encryption strategy for data at rest and in transit.
- [ ] Compliance requirements mapped to VPC capabilities (e.g., HIPAA, GDPR, SOC2).

## 4. Networking
- [ ] IP address management strategy across tenants.
- [ ] DNS and routing configuration per tenant.
- [ ] VPN or Direct Link setup for hybrid connectivity if needed.
- [ ] Firewall and traffic inspection policies.

## 5. Resource Management
- [ ] Resource tagging and naming conventions for tenant identification.
- [ ] Quota and billing management per tenant.
- [ ] Monitoring and logging strategy (e.g., LogDNA, Sysdig, Activity Tracker).
- [ ] Backup and disaster recovery plans per tenant.

## 6. Automation & DevOps
- [ ] Infrastructure as Code (IaC) templates for tenant provisioning.
- [ ] CI/CD pipelines adapted for multitenant deployments.
- [ ] Tenant onboarding/offboarding workflows.

## 7. Operations & Support
- [ ] Defined SLAs and support models per tenant.
- [ ] Incident response and escalation procedures.
- [ ] Tenant usage reporting and analytics.

## 8. Cost & Billing
- [ ] Cost allocation strategy (e.g., resource tags, IBM Cloud billing reports).
- [ ] Budgeting and forecasting tools in place.
- [ ] Chargeback or showback models for internal or external tenants.
