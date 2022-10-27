---
title: Proposals - Timesaver YAGNI
date: 2022-09-20
category:
- standards
- proposals
layout: post
---

Git Hook
-------------

We propose utilization of Git Hooks for all developers, and on a per project language basis.

All file format should be processed with an automatic analyzer to check for errors.

### Pre-Commit

There is a (pre-commit)[https://pre-commit.com] tool that can help manage the pre-commit hook. While it can be useful for hooks created specifically for pre-commit, one losses the ability to have custom or project specific pre-commit check.

#### Work Around

To work-around lossing custom pre-commit the `.git/hook/` pre-commit has to be adjusted.

A directory will have to be created, 
```
.git/hook/pre-commit.d/
``` 
and the `.git/hook/pre-commit` will parse and execute the contents of the directory. 

