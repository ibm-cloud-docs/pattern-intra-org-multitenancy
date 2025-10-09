---
copyright:
  years: 2025
lastupdated: "2025-10-09"

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

### Readiness checklist
{: #checklist}

Use the following checklist to determine whether your organization is ready to pursue worker pool Red Hat OpenShift multitenancy. 

| Task | Description |
|---|-------------|
| - [ ] **Strategic Alignment** | * Clear business case for worker pool-based multitenancy (e.g., performance isolation, compliance, workload segregation). \n * Defined tenant segmentation strategy (e.g., per customer, per team, per environment). \n * Stakeholder alignment across architecture, DevOps, security, and finance teams. |
| - [ ] **Cluster Architecture & Design** | * Understanding of OpenShift on IBM Cloud cluster and worker pool architecture. \n * Decision on single vs. multiple cluster strategy. \n * Worker pool isolation strategy (e.g., node selectors, taints and tolerations). \n * Resource allocation planning per worker pool. |
| - [ ] **Identity & Access Management** | * Role-Based Access Control (RBAC) configured per tenant. \n * Integration with enterprise identity providers (e.g., LDAP, OIDC). \n * Secure service account and secret management per tenant. |
| - [ ] **Security & Compliance** | * Workload isolation using dedicated worker pools. \n * Pod Security Admission (PSA) policies enforced per tenant. \n * NetworkPolicies applied to restrict inter-tenant communication. \n * Compliance mapping (e.g., PCI, HIPAA, GDPR) to OpenShift features. |
| - [ ] **Resource Management** | * Resource quotas and limits defined per tenant. \n * Monitoring and logging scoped to worker pools (e.g., Prometheus, Loki, OpenShift Logging). \n * Backup and disaster recovery strategy per tenant. |
| - [ ] **DevOps & Automation** | * CI/CD pipelines adapted for tenant-specific worker pools. \n * GitOps strategy for tenant deployments. \n * Automated provisioning of worker pools and associated resources. |
| - [ ] **Observability & Operations** | * Centralized monitoring with tenant-level granularity. \n * Logging and audit trails scoped to worker pools. \n * Alerts and dashboards tailored to tenant workloads. |
| - [ ] **Cost & Chargeback** | * Cost tracking per worker pool using labels or annotations. \n * Integration with IBM Cloud billing and metering tools. \n * Chargeback or showback models defined for internal or external tenants. |
| - [ ] **Support & Lifecycle Management** | * Tenant onboarding/offboarding workflows. \n * Worker pool lifecycle policies (e.g., scaling, retirement). \n * Defined SLAs and support tiers per tenant. |
| - [ ] **Governance & Policy** | * Policy enforcement using OpenShift. \n * Naming conventions and tagging standards for worker pools. \n * Regular audits and compliance checks. |
{: caption="Readiness checklist for worker pool Red Hat OpenShift multitenancy" caption-side="top"}
