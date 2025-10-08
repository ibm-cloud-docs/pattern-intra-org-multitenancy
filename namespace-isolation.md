---
copyright:
  years: 2025
lastupdated: "2025-10-08"

subcollection: pattern-intra-org-multitenancy
keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Isolating namespaces 
{: #namespace}

With namespace-based isolation, tenants share a cluster. Within that cluster, namespaces are used to logically separate each tenant's resources. 
{: shortdesc}


![Namespace based isolation reference](/images/namespace-isolation.svg){: caption="Namespace based isolation" caption-side="bottom"}

## Advantages
{: #advantages}

Namespace-based isolation provides the following advantages for your organization: 

- Cost efficiency by using shared infrastructure.
- Reduces complexity by managing one cluster instead of many clusters. 
- Facilitates efficient scaling and resource allocation based on demand without infrastructure duplication.
- Standardized management processes, tools, and monitoring across a unified environment.



## Challenges
{: #challenges}

Namespace-based isolation includes the following challenges for your organization: 

- Shared cluster-scoped resources can cause a single point of failure that might impact all tenants. 
- Updates impact all tenants. 
- Requires multiple instances of the Ingress Controller. 
- Requires a shared dedicated infrastructure layer, also known as a service mesh. 
- Storage provider decisions, such as using shared storage clusters versus dedicated storage clusters per tenant. 
- Isolated application logs. 
- Isolated metrics for customers. 
- The noisy neighbor problem can be mitigated by enforcing fair sharing per tenant. 
- Multi-namespace deployments for each tenant.
- Chargebacks are more challenging with global infrastructure auto scaling. 
- The SLA agreement must be accepted on the environments.
- Privileged pods.

### Mitigating challenges 
{: #mitigate-challenges}

Namespace-based isolation requires stringent access control and isolation for each tenant, reducing the odds of data breaches from tenant to tenant. 

Access control
:   Use policies to help ensure that tenants can access only what they require access to. 

Fair sharing
:   Enforce fair sharing by setting limits per tenant on the number of resources, pod priority, quality of service, taints and tolerations, and pod affinity or anti-affinity. 

Isolation
:   Isolation is critical to prevent tenants from accessing each other's workloads and secrets. Assign different storage classes to each tenant, ideally linked to their own encryption keys.

Admission controller 
:   Use an admission controller to enforce which storage classes are allowed within specific namespaces. [Learn more about Kubernetes admission controllers](https://kubernetes.io/docs/reference/access-authn-authz/admission-controllers/). And, use a separate COS/ICD instance for each tenant.

Internal image registry
:   Disable the internal image registry if Object Storage is not encrypted. For more information, go to [IBM Cloud Registry Guidance](https://cloud.ibm.com/docs/openshift?)



## Determine suitability
{: #suitability}

As you evaluate namespace-based isolation, consider the following questions:

- Does the ISV have operational expertise for managing namespace isolation?
- Can namespaces, quotas, and policies ensure enough isolation for the bank?
- Are security and compliance risks acceptable?
- Is workload performance unaffected by shared cluster-scoped resources?
- Is the cost efficiency by sharing compute resources across tenants beneficial?

### Readiness checklist
{: #checklist}

Use the following checklist to determine whether your organization is ready to pursue Namespace-Based Red Hat OpenShift Multitenancy. 


## 1. Strategic Alignment
- [ ] Clear business justification for namespace-based multitenancy (e.g., cost efficiency, faster onboarding, simplified operations).
- [ ] Agreement on tenant definition (e.g., per team, per application, per customer).
- [ ] Stakeholder alignment across architecture, DevOps, security, and compliance teams.

## 2. Cluster Architecture & Design
- [ ] Understanding of OpenShift cluster architecture on IBM Cloud.
- [ ] Decision on single vs. multiple cluster strategy.
- [ ] Namespace isolation strategy (e.g., RBAC, NetworkPolicies).
- [ ] Resource quotas and limit ranges defined per namespace.

## 3. Identity & Access Management
- [ ] Role-Based Access Control (RBAC) configured per tenant namespace.
- [ ] Integration with enterprise identity providers (e.g., LDAP, OIDC).
- [ ] Tenant-specific service accounts and secrets management.

## 4. Security & Compliance
- [ ] NetworkPolicies implemented to isolate tenant traffic.
- [ ] Pod Security Admission (PSA) policies enforced per namespace.
- [ ] Data encryption in transit and at rest.
- [ ] Compliance mapping (e.g., PCI, HIPAA, GDPR) to OpenShift features.

## 5. Resource Management
- [ ] Resource quotas and limits applied to control tenant usage.
- [ ] Namespace-level monitoring and logging (e.g., Prometheus, Loki, OpenShift Logging).
- [ ] Backup and disaster recovery strategy per namespace.

## 6. DevOps & Automation
- [ ] CI/CD pipelines scoped per tenant namespace.
- [ ] GitOps strategy (e.g., ArgoCD or Tekton) for tenant deployments.
- [ ] Namespace provisioning automated via templates or operators.

## 7. Observability & Operations
- [ ] Centralized monitoring with tenant-level granularity.
- [ ] Logging and audit trails per namespace.
- [ ] Alerts and dashboards scoped to tenant workloads.

## 8. Cost & Chargeback
- [ ] Cost tracking per namespace using labels or annotations.
- [ ] Integration with IBM Cloud billing and metering tools.
- [ ] Chargeback or showback models defined for internal or external tenants.

## 9. Support & Lifecycle Management
- [ ] Tenant onboarding/offboarding workflows.
- [ ] Namespace lifecycle policies (e.g., expiration, archival).
- [ ] Defined SLAs and support tiers per tenant.

## 10. Governance & Policy
- [ ] Policy enforcement using OpenShift Gatekeeper or Kyverno.
- [ ] Namespace naming conventions and tagging standards.
- [ ] Regular audits and compliance checks.
