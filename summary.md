---
copyright:
  years: 2025
lastupdated: "2025-09-19"

subcollection: pattern-intra-org-multitenancy
keywords:

---

{{site.data.keyword.attribute-definition-list}}
# Summary

![Factors](/images/spider.svg){: caption="Factors influencing decisions" caption-side="bottom"}

## Summary options
VPC or Application Native models are recommended for implementing multitenancy due to their scalability and isolation benefits. While account isolation is not mandatory for ISVs, adopting it can lead to increased operational complexity. Namespace isolation, on the other hand, poses risks such as single points of failure, noisy neighbor issues, and heightened demands for operational and security enforcement. Additionally, using worker pools or multi-cluster setups does not offer significant advantages over the VPC model. For a detailed breakdown of the factors and data referenced in the chart, please refer to this diagram.
