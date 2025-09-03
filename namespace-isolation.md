---
copyright:
  years: 2025
lastupdated: "2025-09-03"

subcollection: pattern-intra-org-multitenancy
keywords:

---

{{site.data.keyword.attribute-definition-list}}
# Namespace based isolation

![Namespace based isolation reference](/images/namespace-isolation.svg){: caption="Namespace based isolation" caption-side="bottom"}

## Advantages
Leveraging shared infrastructure and minimizing operational overhead enhances **cost efficiency** across the environment. By managing a **single cluster** rather than multiple ones, organizations can significantly **reduce complexity**. This unified approach also enables **efficient scaling** and **resource allocation** based on demand,


## Challenges
Shared cluster-scoped resources can introduce a **single point of failure**, potentially impacting all business units. To mitigate this, deploying **multiple instances of the Ingress Controller** is recommended. For **Service Mesh**, it's important to evaluate whether a **shared instance** is acceptable based on tenant requirements. **Storage provisioning** also requires careful consideration—either through **dedicated storage clusters per tenant** or a **shared storage cluster**, depending on isolation needs.

**Application log isolation** and **monitoring-level metric separation** are crucial in platform scenarios to ensure tenant-specific visibility and control. Addressing the **"noisy neighbor"** issue involves implementing **fair sharing practices**. Deploying **multiple namespaces per tenant** supports better isolation and management.

**Chargeback mechanisms** should align with **global infrastructure auto-scaling** to ensure accurate cost attribution. Clear **SLA agreements** must be established for each environment, especially when **privileged pods** are involved. Lastly, **updates to the platform** can affect all tenants, so **change management and communication strategies** must be robust.


## Best practices
**Access Control** is essential in multi-tenant environments. Use policies such as **Role-Based Access Control (RBAC)** to ensure tenants can only access resources they are authorized to.

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
When evaluating a multi-tenant architecture, it's important to assess whether the **ISV has the operational expertise** required to manage **namespace isolation** effectively. Key considerations include whether **namespaces, quotas, and policies** can provide **sufficient isolation** for sensitive environments such as banking. **Security and compliance risks** must be carefully weighed to determine if they are within acceptable limits. Additionally, it's crucial to ensure that **workload performance** remains unaffected by **shared cluster-scoped resources**. Finally, the potential **cost efficiency** gained by sharing compute resources across tenants should be evaluated to determine if it delivers meaningful benefits without compromising performance or security.
