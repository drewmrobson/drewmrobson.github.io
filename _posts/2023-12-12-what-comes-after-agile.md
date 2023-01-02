---
layout: post
title:  "What comes after Agile"
date:   2023-12-12 00:00:00 +1000
categories: agile
tags: agile
excerpt_separator: <!--more-->
---

??

<!--more-->

Straightforward / Minimalist Agile

Kanban board.
Column 1 - Backlog
Column 2 - In Progress
Column 3 - Done

WIP Limit per person - 3

Metrics
- Lead time
- Cycle time
- Estimate
- Actual
- Target date (From estimate)
- Target budget (From estimate)

Estimates in Days. 0.12 (1h), 0.5 (4h), 1

Example
- Update title text
-- Lead time = DateTime.Now - .CreatedDate
-- Cycle time = Done.Date - InProgress.Date
-- Estimate (user entered in days)
-- Actual ?
-- Target date = COALESCE(Estimate.Days) + Estimate.Days TODATE
-- Target budget = COALESCE(Estimate.Days) + Estimate.Days * UnitCost
-- Historical Velocity = Number of units completed in iteration??

We don't use historical velocity - we use how many SUM(Estimates) were included in the last release? How many SUM(Estimates) were included on average across all releases?


What information does this provide Project managers?
- Developers provide [estimates] on the [backlog].[items]
- Product managers prioritise the [backlog]
- Product managers can then see what will be done, and when it will be done
- Engineering managers can see when lead time, cycle time are growing


1. Cards can't move from Done back to InProgress. Instead a GAP must be raised.
2. Cards can't move from InProgress back to TODO. Instead a CANCEL event must be raised

Individuals and interactions over processes and tools
Working software over comprehensive documentation
Customer collaboration over contract negotiation
Responding to change over following a plan

Build projects around motivated individuals.
Give them the environment and support they need,
and trust them to get the job done.

Working software is the primary measure of progress.

The best architectures, requirements, and designs
emerge from self-organizing teams.

https://agilemanifesto.org/principles.html
