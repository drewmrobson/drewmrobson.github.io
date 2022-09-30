---
layout: post
title:  "Optus should hire me to fix their APIs"
date:   2022-10-01 00:00:00 +1000
categories: security
excerpt_separator: <!--more-->
---
After the [recent Optus customer identity data breach](https://blog.drewrobson.consulting/security/2022/09/27/the-optus-breach.html), Optus should absolutely hire me to fix their API security. Let's talk about fixing the breach at the technical level.

<!--more-->

The attacker simply consumed an unsecured API designed to read from a customer identity database. As explained in my post above, Optus was required to store this data and should have treated it with the seriousness it deserves. Instead, poor process and implementation left a wide-open door for anyone to find.

Optus could have put these measures in place and still had the same breach...

- Data encryption in transit
- Data encryption at rest
- Limit the user accounts with access to the custom identity database

...because the API was designed to return custom identity data to the API consumer. Indeed, [Kelly Bayer Rosmarin](https://blog.drewrobson.consulting/security/2022/09/29/kelly-bayer-rosmarin.html) has claimed the data was encrypted which shows she has no understanding of the problem. The API was designed to return the encrypted data as plain text, as the attacker has confirmed.

What Optus should have done, and I do in my work:

1. Secure the API with at the minimum an API key, with a regular key rotation
2. For sensitive data such as PII, add an additional layer of authorized users via OAuth/JWT or client certificates
3. Isolate production databases from test environments, making it impossible for production data to be read from a test API.
4. Ensure separate Internal and Public API Gateways based on intended use of the system

The root cause is really a process issue. APIs should only be deployed after rigorous peer review in an automated and repeatable way with sensible defaults, making it impossible to deploy an insecured API and ensuring security standards are envforced in all environments.

This is all really basic stuff and Optus need to address their software development practices as well as their stewardship of Australian's identity data.