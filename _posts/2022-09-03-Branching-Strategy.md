---
title: Branching Strategy 
date: 2022-09-03
category:
- standards
- branching
layout: post
---

JIRA Based
-------------

When a project is managed via JIRA, the mechanism that allows JIRA to track commits, pushes, and branches to a specific ticket or issue is a branch naming convention.

The branching convention appears to be:

```
JIRA Project Key + '-' + lower(Issue Number + '-' + Issue Title). 
```

For example, a project with JIRA Project Key of "XMPL", Issue Number of "1", and Issue Title of "Descriptive Title of a Functionality" will have a branch of:

`XMPL1-descriptive-title-of-a-functionality`

> ##### TIP: Branching
> 
> Do not create branches without a ticket or issue in JIRA
{: .block-tip }
