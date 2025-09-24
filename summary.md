---
copyright:
  years: 2025
lastupdated: "2025-09-24"

subcollection: pattern-intra-org-multitenancy
keywords:

---

{{site.data.keyword.attribute-definition-list}}

# Summary
{: #summary}

VPC-based isolation or application native models are recommended for implementing multitenancy due to their scalability and isolation benefits. While account isolation is not mandatory for ISVs, adopting it can lead to increased operational complexity. Namespace isolation poses risks such as single points of failure, noisy neighbor issues, and heightened demands for operational and security enforcement. Additionally, using worker pools or multi-cluster setups does not offer significant advantages over the VPC model. For a detailed breakdown of the factors and data that is referenced in the chart, refer to the following image.
{: shortdesc}

![Factors](/images/spider.svg){: caption="Factors influencing decisions" caption-side="bottom"}
