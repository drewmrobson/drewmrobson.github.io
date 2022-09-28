---
layout: post
title:  "Optus should hire me to fix their APIs"
date:   2022-10-01 00:00:00 +1000
categories: security
excerpt_separator: <!--more-->
---
After the [recent Optus customer identity data breach](https://blog.drewrobson.consulting/security/2022/09/27/the-optus-breach.html), Optus should absolutely hire me to fix their API security. Let's talk about the breach at the technical level.

<!--more-->

From what I can gather, the attacker simply consumed an unsecured API which was designed to read details from a customer identity database. As per the above breakdown, government regulations required Optus to store PII data in some form. While this isn't ideal, without better government we're stuck with the reality that a lot of companies will have your data.

Stuck with this reality, the goal now becomes limiting access to, and protection of, this valuable data.

1. Process, automation and sensible defaults are key. No APIs should be deployed outside of a managed process (peer code review, variable management, infrastructre as code,)
2. All APIs should be secured by an appopriately-scoped API key by default. The first hurdle an attacker would now face would be not having a valid API key.
3. As customer identity is so sensitive, the API should also be configured with a second layer of a Bearer token which is only issued when a valid 2FA challenge has been passed. This ensures only users with granted access to the API can proceed, and can confirm their identity with 2FA.
4. The Optus breach was through a test environment, and this can be fixed by isolating the production customer identity database on a separate virtual network from the test environment API Gateway.
5. Consider who needs access to this data. If it doesn't need to be public, consider only deploying the API to an internally-secured API Gateway.

[1](https://www.ultima.com/blog/discover-how-secure-your-azure-api-management-infrastructure)