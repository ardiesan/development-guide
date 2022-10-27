---
title: Style and Formatting 
date: 2022-09-04
category:
- standards
- formatting
layout: post
lang: en
---

Formatter
-------------

According to your IDE, select a xml file from Formatter List.  

As for each features provided by xml files, refer to Formatter Feature List.


<div class="table-wrapper" markdown="block">

|IDE|Formatter|
|:-:|:-:|
|IntelliJ|[IntelliJ_Form_Scheme.xml](/assets/static/IntelliJ_Format_Scheme.xml)|
|Eclipse|[CodeiFormatter_v2.xml](/assets/static/CodeFormatter_v2.xml)|

</div>



Import Rules
-------------

To improve readability of code, here defines rules about importing libraries.
Avoid using wildcards (e.g. `java.util.*`). It makes it hard to find out which package a class belongs to (especially when you don't have help of IDE).

> ##### IMPORTANT
>
> Write import statements in specific order to facilitate finding one in many import statements. 
>
> Order from top: import static, java, javax, org (commons), com, 3rd party libs, then FS packages.  
{: .block-tip }



Static Code Analysis
-------------

Static code analysis tools can be used to detect and address bugs and security vulnerabilities in source code at an early stage of a project.

