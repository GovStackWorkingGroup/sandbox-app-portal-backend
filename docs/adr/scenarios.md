# Portal

Portal is:

* showing infra
* showing scenarios
* showing analyzing, producing use cases.

[Confluence](https://govstack-global.atlassian.net/wiki/spaces/DEMO/pages/293109778/Scope+of+Portal#%3Aquestion_mark%3A-Open-Questions). 


Portal is a web resource responsible to show and provide access to the different use cases.

Heavy BBs like Mosip, Mifos "partially" require manual work to get up and running in the Kubernetes or in other words, they don't fully install and start automatically.

As an alternative we have light alternative = emulators.
They are easy to up and run, but they have a limited business logic. No error handling and design to only show use case.
They have a limited functionality and predefined data.

## Issue
How can multiple users use the same use case instance without stepping on each other's toes?

Base on that portal can be a [multi tenant](scenarios.md#multi-tenancy) or provide [separate use case for each user](scenarios.md#separate-instance-of-use-case-for-each-user).

## Multi tenancy
All users are using single instance of use case.

### Prose
Need to have less resources since need to have only one instance of BBs

###  Cons
* Scalability for each use case we should separately implement multi tenant logic in the orchestrator and emulators.
  Orchestrator and emulator have to have . For each use case we should implement
  Currently, we have only one up and running BB = information mediator
* Can be more difficult to up and run on demand. Most probably need to keep up and running use case.
* We have only information mediator BB up and running.

## Separate instance of use case for each user
Each user is using separate instance of use case.

### Prose
* Scalability. Creating new use case and providing separate use case for each user should be straight forward.
* Orchestrators and emulators can stay light and include only use case logic.
* Anyone can easily use this package on their own resources since this implementation provides such separate package that represent whole use case.
* No need to keep up and run all infrastructure constantly. Can be up and run on demand.
* More friendly for updates. Should be easier to have different versions of use case.

###  Cons
* Decoupling a use case instance for a new user can be tricky, and we can compromise a critical part of the portal.

## Questions:

* How do we deploy the different parts of a scenario?
  Use case is a [separate independent package](scenarios.md#separate-instance-of-use-case-for-each-user). 


Providing sandbox as infrastructure as code? 

Do we have auto procedure for all components of sandbox. Yes, we have 

What are benefits?
What is our target group?

Example 
https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/

Deliverable: 
* Public access 
* Multi tenancy
* ...