---
copyright:
  years: 2025
lastupdated: "2025-09-22"

subcollection: pattern-intra-org-multitenancy
keywords:

---

{{site.data.keyword.attribute-definition-list}}
# Namespace based isolation

![Namespace based isolation reference](/images/namespace-isolation.svg){: caption="Namespace based isolation" caption-side="bottom"}

## Advantages
- **Cost efficiency through shared infrastructure and operational overhead**
- **Reduces complexity by managing one cluster instead of multiple**
- **Facilitates efficient scaling and resource allocation based on demand without infrastructure duplication**
- **Standardized management processes, tools, and monitoring across a unified environment**



## Challenges
- **Shared cluster-scoped resources can cause single point of failure (All BU affected)?**
- **Ingress Controller** – Use multiple instances
- **Service Mesh** – Is shared instance acceptable?
- **Storage provider** – Dedicated storage clusters per tenant or shared storage cluster?
- **Isolation of Application Logs** – Platform scenario
- **Monitoring level Isolation of Metrics for customer** – Platform scenario
- **Noisy Neighbour** – See *Fair Sharing* in Best Practices
- **Multi Namespace Deployment** for each tenant
- **Chargeback** – Global infrastructure auto scaling
- **SLA Agreement** on the environments
- **Privileged pods**
- **Updates will affect all tenants**



## Best practices
- **Access Control - Use policies to ensure that tenants can access only what they should have access to (RBAC)**

**Fair Sharing** should be enforced by setting limits per tenant on:
- Resource Quotas
- Pod Priority
- Quality of Service
- Taints & Tolerations
- Pod Affinity / Anti-affinity

**Isolation** is critical to prevent tenants from accessing each other's workloads and secrets. Assign **different storage classes** to each tenant, ideally linked to their own **encryption keys**.

Use an **Admission Controller** to enforce which storage classes are allowed within specific namespaces. [Learn more about Kubernetes Admission Controllers](https://kubernetes.io/docs/reference/access-authn-authz/admission-controllersy. Use **separate COS/ICD instances** for each tenant.

Disable the **internal image registry** if COS is not encrypted. [IBM Cloud Registry Guidance](https://cloud.ibm.com/docs/openshift?

## Enhancement requests
- Implementation check
- ER for Workload Protection Operator
- SCC Multi tenant Profile

## Determine suitability
- **Does the ISV have operational expertise for managing namespace isolation?**
- **Can namespaces, quotas, and policies ensure enough isolation for the bank?**
- **Are security and compliance risks acceptable?**
- **Is workload performance unaffected by shared resources (Cluster scoped resources)?**
- **Is the cost efficiency by sharing compute resources across tenants beneficial?**
