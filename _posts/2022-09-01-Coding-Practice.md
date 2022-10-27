---
title: Coding Standards
date: 2022-09-01
category:
- standards
- coding
layout: post
---

Style & Formatting
-------------

Refer to [Style and Formatting]({% post_url 2022-09-04-Style-and-Formatting %}).


---

Minimize Dependencies
-------------

> ##### IMPORTANT
> Avoid unnecessary dependency.
{: .block-info }

Too much dependency results in conflicts around .jar versions or regressions, to avoid complicated .jar handling.

If you find your business logic being referred to by multiple other classes, you probably misunderstand the usages of util and business logic, because such a case basically never happens.

* Util classes that are highly versatile are intended to be used by any packages, but only a minimum number of processes must be allowed to depend on business logics.
* This is a principle related to [Proximity Principle](#proximity-principle).
* Confirm you aren't making a class depend on a business logic instead of a util.
* Confirm a class that you want your class to depend on doesn't have any nouns specific to business logic.

> ##### TIP: Dependencies
> 
> Read about [Dependency Injection](https://en.wikipedia.org/wiki/Dependency_injection) Principle
{: .block-tip }


---

Proximity Principle 
-------------

* It makes your implementation highly readable to place your pieces of code close together with those of high relevancy.
* If you place it on a distant place, it consumes a lot of your time to investigate the influence of your code changes, because this will require wider area to search and make you anxious that you may make an oversight.


### Note the Following

* A class that is used only on one project must be placed in that project.
* A class that is used only on one package must be placed in that package.
* A class that is used only by one class must be placed in the latter class.
* Do not make a common class or an outer package which you are uncertain is used.
* Check the chapter [Package-Private](#package-private) too.

> ##### TIP: Proximity
>
> Place Definitions in Close Proximity
{: .block-tip }


---

Package-Private
-------------

A package must be closed in the unit of purpose and responsibilities, otherwise you can say that the design fails in object-oriented design.

The structure of package dependencies should be simplified to only depend on the parent package, and controlled so that at most only parent and child packages are dependent on each other. This is related to [Proximity Principle](#proximity-principle)


###  Note the Following

* Similar to class interdependencies, package interdependencies can be considered a failure in object-oriented design.
* Package dependencies should be avoided even within the same project.
* To avoid package dependencies, a hierarchical tree should be used, with the major meaning upstream of the package namespace, and subdivided toward child packages.
* The same level of packages should be placed in the same hierarchy of packages.
* If the dependencies between packages become too strong within a project, it will not be possible to move only that package to another project.


This is especially common in the last case, where a package is referenced in multiple projects, and it is no longer possible to create a common implementation by externalizing the package. 
As a result, such a project will have duplicate code scattered throughout the project, which will reduce readability, maintainability, and ultimately productivity.

> ##### TIP: Packages
>
> Read on [Single-Responsibility](https://en.wikipedia.org/wiki/Single-responsibility_principle) Principle.
{: .block-tip }


---

No Duplicate Codes
-------------

If the same process code is scattered in multiple classes, it is not object-oriented. If the same process code is scattered in multiple classes, it is not object oriented. If the same processing code is scattered in multiple classes, it is not object-oriented.


---

Remove Unused Codes
-------------

Only the person who made the modification knows the context and details of the revision. When the next person who does the modification comes across code that is no longer in use, he or she will initially assume that the remaining code and columns are meaningful. 

This results in a triple cost: investigating the impact of the unused code, confusion, and checking with the implementer.


---

YAGNI
-------------

Observe [YAGNI](https://en.wikipedia.org/wiki/You_aren't_gonna_need_it)

> ##### TIP
>
> If in doubt, leave it out!
{: .block-tip }


---

Implement Symmetrically
------------

Symmetric codes reduce bugs, reduce costs of study, raise readability and make themselves easier to search, in other words, are productive.

Codes conforming to a specific school help a programmer gain insight of "my new implementation should be in accordance with that process because they are broadly alike." and find a sample easily.


### Note the Following

* Unify the package structure with rules across projects.
* Use the same libraries across projects.
* Use the same class naming conventions across projects.
* Unify the order of fields and methods in classes and their names across projects.
* Imitate business logic writing style, content, and manner across projects. (This does not mean writing two pieces of business logic.)
* Use the same basic util and algorithm across projects.
* If you add new package dependencies, you may be breaking symmetry. Are you sure you are doing it right? Check again beforehand.
* Consider the package structure as part of the programming process. Arranging similar packages in a package hierarchy naturally improves symmetry. This is related to [Package Hierarchy](#package-hierarchy)

> ##### BENEFIT
>
> This allows us to complete a task quickly, and be more productive.
{: .block-tip }

---

Package Hierarchy
-----------

It is very important to have a consisten package heirarchy.
 
Let's start with an example, "com.example.tpas.service" and "com.example.tpas.sync". A sync is service, you should find "sync" in "service".

The more consistent the meaning of the package hierarchy, the easier it will be to achieve [Package-Private](#package-private) and [Implement Symmetrically](#implement-symmetrically). The result is better visibility and readability.


* You should make it a habit to think of package configuration as programming. The first step is to think of packages as clean.
* There are cases where it is impossible to align the hierarchy. In that case, it is ok to break the principle, but make sure that the way you break the principle is consistent across projects ([Implement Symmetrically](#implement-symmetrically)).


---

Do NOT Start Projects On Your Own
-----------

A project without thorough analysis, approval, and resource allocation will be less maintained, will likely not be kept up-to-date, and will be a breeding ground for bugs.

* Do not make a new project a common implementation or business logic for a specific process only. The project should have a larger role.
* If this is absolutely necessary, consult the project manager.

> ##### WARNING
>
> Do not start a project without permission
{: .block-warning }


---

Prohibit Direct DB Access
-----------

Services should only be accessed via their CRUD interfaces or API.

As much as possible, implementations should be a microservice. Traditional or direct DB access would system maintenance unwieldy and out of control, especially where RDBMS solved dependencies between them.


---

Object-Oriented Always
-----------

Violating the principles of Object-Oriented design results in spaghetti code.

It will take time to investigate, it will cause bugs, and take a lot of time to debug.

### Note the Following

* Is the design centered on processing? Is the design process-centered?
* Are the names of methods and fields consistent with the entities?
* Are the names of methods and fields consistent with the entities? In that case, take the plunge and review the class or package.
* Are you afraid to modify existing code? -> In the end, others will only take greater risks. Now you fix it.


---

OK IS NOT ENOUGH
-----------

> ##### BEWARE
>
> It is not OK that it works for the time being.
{: .block-warning  }

Is the code consistent with similar code in the relevant area? Make sure it's coherent to other codes of similar processes, because otherwise any of your possible errors will stay unnoticed for a long time.

The next person who modifies the same part of the code will create and release a module based on your code. If there is a logical error in the snippet of code you have written, you have did not notice it. It can take several years to find a logical error.

Another possible problem is, an engineer who will work on a module that is supposed to refer to your odd code may also furnish his or hers with irregular codes of "if" or "case" clauses to offset your original irregularity.

The issue will add up and worse compound to a unmanagable issue for everyone.

### Note the Following

* Be sure that the code is supposed to work, but be sure that the code is in order after it works.
* When modifying the code, do not start writing the relevant part of the code out of the blue, but rather, investigate the surrounding code thoroughly before starting to modify the code.
* The measures to be taken are basically the same as those in [symmetrical writing](#symmetrical writing), but be careful to be prepared for them.
* **If you can get quality code for a small delay in release, choose quality.**
* If you find disorganized code, take a risk and fix it too.


---

Naming Conventions
-----------

Highly readable code is essential to facilitate understanding of existing processes. The name is the most important clue.

### Note the Following

* Confirm that members, fields, methods, functions, and other with different meanings have different names.
* Does your method have a name reflecting the exact role of it?
* A business logic mustn't have any magic word in it, (ex. /tmp/normal/old/classic)
although util classes are recommended to have magic words conversely.
* Does your method/field have an English name natural to non-Japanese? Learn other language too.
* When a system revision alters the meanings of implementation, take the time to change the names of classes and packages to make them fit.


> ##### INFO 
> 
> Correct and closest possible naming of a method to how it works or what it is doing allows a developer to cut time investigating what it is actually doing.
{: .block-info }

---

Secure Coding
-----------

It is important to avoid vulnerable code as a security measure.  
If your code is released with a vulnerability, it may be attacked and your service may be shut down.     


### Java

Please refer to the following guidelines.  

https://www.jpcert.or.jp/java-rules/


---

Release Impact
-----------

It is not enough to simply take care of the immediate regressions of the normal processes. Attention to how it will affect the overall release
should be analyzed and attended to.

#### Note the Following

* Will it affect the processing speed after releasing the module?
* Is there maintenance work after releasing the module?
* Are there any additional dependencies after releasing the module? Does it have unnecessary dependencies?
* Is the module designed to withstand a failure of the module?
* Is it a Single Point of Failure (SPOF)?
* Is it designed to withstand the failure of the module?


---

Batch Jobs
-----------

#### Azkaban Must Fail On Errors

There are rare cases where an actual process fails while Azkaban reports that it is successful.


#### Java

In Java, an error is defined to be a case where "JobForm#getErrorCount() > 0" with JobForm(conf) created beforehand.

#### Shell

Confirm that the shell script returns 0 for a normal end, while 1 for an error.

#### Document Jobs

There are already a considerable number of batch jobs, and it is becoming difficult to understand the relationship and impact of each one.
In order to prevent the time-consuming investigation of the relationships and effects of the jobs, the job descriptions should be written as comments in the Azkaban job file.
