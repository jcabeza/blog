---
layout: post
title: Hello from my blog
categories: [Azure]
tags: [Azure]
comments: false
---

- [How to calculate the number of IP addresses?](#how-to-calculate-the-number-of-ip-addresses)
- [Azure Resource Graph](##azure-resource-graph)

**UPDATE - 22/05/2023**

When you view your Azure Virtual Network and Subnet(s) in the Azure Portal you can see how many IP addresses are still available in that Subnet.

# How to calculate the number of IP addresses?

In Azure we need to distract 3 more addresses, so in total 5 addresses cannot be used from the total of 256 IP addresses. 

## Azure Resource Graph

First, we'll need to open up Azure Resource Graph Explorer and run a query against the Azure Resource Graph. The query will look something like this:

```sql
| extend numberOfIpAddresses = trim_end(".0",tostring(pow(2, 32 - prefixLength) - 5))
```

I hope you learned something new and useful.
