---
copyright:
  years: 2025
lastupdated: "2025-08-25"

subcollection: pattern-intra-org-multitenancy
keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Multi-Tenancy & Isolation Models in Cloud Environments
{: #options}

These models represent increasing levels of resource sharing and isolation across tenants (teams, applications, or customers):

## 1. Account-Based Isolation
{: #account-isolation}
- Each tenant has a separate cloud account.
- Strongest isolation; ideal for regulated environments.
- Resources like VPCs clusters and IAM policies are fully separated.

## 2. VPC-Based Isolation (Today)
{: #vpc-isolation}
- Each tenant operates within its own Virtual Private Cloud.
- Good network-level isolation.
- Common in enterprise setups where accounts are shared but VPCs are isolated.

## 3. Multiple Clusters in Same VPC
{: #cluster-isolation}
- Tenants share a VPC but run workloads in separate Kubernetes clusters.
- Offers cluster-level isolation while reducing VPC sprawl.
- Useful for managing cost and operational overhead.

## 4. Worker Pool-Based Isolation
{: #worker-isolation}
- Tenants share a cluster but use dedicated node pools (worker pools).
- Limits resource contention and improves fault isolation.
- Efficient for internal teams with different workload profiles.

## 5. Namespace-Based Isolation
{: #namespace-isolation}
- Tenants share a cluster and use namespaces for logical separation.
- Lightweight and cost-effective.
- Requires strict RBAC and network policies to ensure security.

## 6. Application-Native Multi-Tenancy
{: #app-isolation}
- The application itself handles tenant isolation (e.g. via tenant IDs scoped data access).
- Most flexible but hardest to secure.
- Common in SaaS platforms with shared backend services.
- IBM Cloud
