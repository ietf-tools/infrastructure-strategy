# Background
The current contract for IETF IT infrastructure services is a black box contract - we specify the systems to be maintained along with a very basic SLA, and the provider is responsible for the underlying infrastructure on which those systems operate, including the system administration strategy. The provider has always been much more accommodating than that in responding to requests for changes inside the black box, but these requests were for a long time piecemeal and not part of an overall strategy.

There have been regular complaints from the community that our infrastructure is more prone to failure, more difficult to upgrade and more difficult to accommodate new services, compared to a modern best practice infrastructure.  The IETF Administration LLC has consulted with the community via the tools-discuss list on the best way to address this and concluded that a new approach is required, which brings the community into the forefront of specifying an operational strategy for how the infrastructure should be operated.  This document sets out that new operational strategy.

The subject of who provides our IT infrastructure management, or what model that operates under, is out of scope and is left as a contract/sourcing decision for the IETF LLC. 

# Goals
The IETF IT infrastructure should be operated to meet the following goals, each of which is described in more depth in the sections below.  It is recognised that some of these goals overlap or are interdependent.

1. Fit-for-purpose service availability
2. Fit-for-purpose service performance
3. Separated, cloud-first services
4. Automated, transparent and accessible infrastructure management
5. Secure and enduring services and data
6. Comprehensive service monitoring

## Fit-for-purpose service availability
The IETF is a global community with an uneven geographic spread, and the community uses the IETF infrastructure 24x7x365.  During IETF meetings, both the triannual plenaries and the many interim meetings, demand on services is high and uninterrupted availability is expected. At other times, the activities are not so time critical that they cannot tolerate a delay of a few hours if planned and sufficient warning is given. 

The IETF requires its IT infrastructure to support a fit-for-purpose service availability, which means:
* Minimal unplanned downtime.
* Infrastructure designed to eliminate planned downtime, recognising that some of the applications may still require that. 
* Where planned downtime is required, then:
  * It must not be during or during the preparation phase of IETF meetings or other key events.
  * Should be able to be scheduled for any day of the week at any time, to meet IETF operational requirements.

## Fit-for-purpose service performance
The demands on IETF services varies considerably with particular peaks in and around IETF meetings.  Also, there are a number of services intended for users to pull large amounts of data (1-10 GB) in order to maintain local copies of large datasets. While service performance can be adversely affected by a bottleneck at a level of the stack above the IT infrastructure, the IT infrastructure should not become the bottleneck.

The IETF requires its IT infrastructure to provide a fit-for-purpose service performance, which means:
* Excellent infrastructure performance.
* All relevant and potentially relevant performance/utilisation data collected.
* An infrastructure that scales to match load, particularly during key events, with minimal manual intervention.
* An infrastructure that recognises the global nature of the IETF and ensures excellent performance to all end users.
* An evidence based approach used in setting all resource limits.
* A strategy for rapidly addressing performance bottlenecks.

## Separated, cloud-first services
The IETF has a wide variety of services, a high rate of change/growth in services, increasing integrations between services, significant fluctuations in usage with an underlying increase, and a wide variety of deployment models.

The IETF requires its IT infrastructure to operate cloud-first and support IaaS, PaaS and SaaS, which means:
* All services run in the cloud on public cloud platforms.
* All cloud platforms to support orchestration, including automated deployment, scaling and management, except where the application itself cannot support this.
* All OS-level services to be containerised so that they are entirely separated at the filesystem/package level and any one can have any supporting package upgraded without any other service being affected.
* Unless entirely unavoidable, it should be possible to upgrade, migrate, scale or otherwise radically change any service without affecting any other service.
* All services to support operation behind Web Application Firewalls, Content Delivery Networks and other front end services. 

## Automated, transparent and accessible infrastructure management
The IETF has an active community of volunteers contributing to its systems development efforts and its meetings’ NOC team, and it is likely that there will be a similar depth of community contribution to our IT infrastructure management, if this is enabled.  In addition, the IETF has a small and growing team of in-house developers and key development contractors, who like much of the development community, are increasingly adopting devops practices.

The IETF requires the management of its infrastructure to be automated, transparent and accessible, which means:
* All build and configuration managed through an automated configuration management and deployment platform (e.g. Ansible).
* Automation scripts in a public Git repository.
* Credentials and other secret information used in automation scripts to be properly protected.
* A full test environment with the expectation that wherever possible, deployment involves first deploying to test, validating efficacy of changes, and then deploy to production.
* Where reasonable, it should be possible for any member of the IETF community to build a replica of any IETF service, with placeholder information available to replace any confidential information.
* Active response to community contributions both on mailing lists and through a formal change management system (e.g. GitHub Pull Requests).

## Secure and enduring services and data
Secure and enduring services and data
The IETF is vulnerable to the same threats as any other organisation and needs to mitigate those at many levels. The threat model for the IETF is unusual with more of an emphasis on data integrity and preserving the accuracy and availability of historical data, than on protecting confidential information.  Where the IETF does collect highly confidential information, such as for the NomCom process, every effort is made to compartmentalise that.  Additionally, the IETF receives significant nuisance traffic (as a proportion of overall traffic).

The IETF requires its services and data to be secure and enduring, which means:
* An embedded risk-aware culture, with regular peer review and external audit of all strategies, processes and systems.
* A formal access control model with centralised observability.
* Clear compartmentalisation of confidential information.
* A patch management process that minimises the threat from unpatched systems.
* A backup and restore strategy that provides strong assurance of data integrity and high confidence of system rebuild.
* Active management of nuisance traffic.

## Comprehensive service monitoring
As the IETF services evolve, they are becoming more integrated and more interdependent making the task of identifying the source of problems a more complex task and ultimately reliant on good data. The tools used for capturing, processing, analysing and presenting data have developed rapidly in recent years and within any team that relies on data there will be a wide range of tools used. Also, as noted above, the number of data consumers is likely to grow significantly as the IETF community begins to contribute to our IT infrastructure.

The IETF requires comprehensive, standards-based service monitoring, which means:

* Every part of the infrastructure is instrumented.
* Centralised collection of monitoring data to enable cross-service analysis.
* Controlled publication of monitoring data that maintains operational security while providing maximum access to the IETF community.
* Where possible, standards based data collection and distribution, and where proprietary APIs need to be used then these must be open and documented APIs.
