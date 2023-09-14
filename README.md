# Architectural Katas - Fall 2023


This repository is our solution to the Fall 2023 [O'Reilly Architectural Katas Challenge](https://learning.oreilly.com/live-events/architectural-katas/0636920097101/0636920097100/).

The goal of the challenge is to enable Road Warrior, a startup aspiring to be a single source of truth for all things related to the trips of its users, to meet its objective.

The original requirements can be found [here](/requirements/original.pdf)

## Content
<center>
<table border="0">

 <tr style="vertical-align:top">
    <td>

**[1. About us](#about-us)**

**[2. Problem Statement](#problem-background)**
* [2.1. Hey, Blue! Vision](#hey-blue-vision)
* [2.2. Requirements](#requirements)
* [2.3. Actors Overview](#actors-overview)

**[3. Domain Design](#domain-design)**
* [3.1. Event Storming Process](#event-storming-process)
  * [3.1.1 Event Storming Detailed View](/eventstorming/event-storming.md)
* [3.2. Architecture Style](#architecture-style)
* [3.3. Domain capabilities](#domain-capabilities)
  * [3.3.1 Domain capabilities Overview](#capabilities-overview)
  * [3.3.2 Domain capabilities In-depth](#capabilities-in-depth)
      * [Connection Capability](domain/connection-capability.md)
      * [Reporting Capability](domain/reporting-capability.md)
      * [Order Capability](domain/order-capability.md)
      * [User Capability](domain/user-capability.md)
* [3.4. Legend](#legend)
    </td>
    <td>
**[4. System Architecture](#system-architecture)**
* [4.1. System Architecture Document](azure/resources/cloud-architecture.md)

**[5. Architecture Decision Records (ADR)](#architecture-decision-records-adr)**
* [2022-10-31 ADR01 Microservice Architecture](ADRs/2022-10-31_01-microservice-architecture.md)
* [2022-10-31 ADR02 Event-Driven Design](ADRs/2022-10-31_02-event-driven-design.md)
* [2022-10-31 ADR03 Points Redemption Framework](ADRs/2022-10-31_03-redeem-points.md)
* [2022-10-31 ADR04 Dispatcher Architecture](ADRs/2022-10-31_04-dispatcher-architecture.md)
* [2022-11-01 ADR05 Backend-for-Frontend Pattern](ADRs/2022-11-01_05-bff.md)
* [2022-11-06 ADR06 Read Replica Pattern](ADRs/2022-11-06_06-read-replica-pattern.md)
* [2022-11-08 ADR07 Azure as a Hyperscaler](ADRs/2022-11-08_07-azure-hyperscaler.md)
* [2022-11-08 ADR08 GDPR Compliance](ADRs/2022-11-08_08-GDPR-compliance.md)

**[6. Acknowledgements](#acknowledgements)**
    </td>
 </tr>
</table>
</center>

## About Us
Our team consists of [Apostolos Mantes](https://www.linkedin.com/in/mantesap), [George Lourakis](https://www.linkedin.com/in/georgios-lourakis-099b79197), [George Panagiotakis](https://www.linkedin.com/in/yiorgos-panayiotakis-71185a5b), [Konstantinos Polydorou](htts://www.linkedin.com/in/kpolyd) and [Spyros Economopoulos](https://www.linkedin.com/in/economopoulos). We are members of [Neurocom SA](https://www.neurocom.gr), a greek company focusing mainly on the telecommunication sector, located in Greece.


## Our understanding of the requirements  

### The Vision

Be the single source of truth for all things trip related.

### The Scope

At this stage focus on 
* flights
* hotels and 
* car rentals

Keep in mind the vision and consider how the platform will embrace trains, buses, attractions etc. etc.

### Requirements in scope

We grouped our understanding of the requirements for the **Road Warrior** platform into the following two sections.  
- [Functional requirements](requirements/functional-requirements.md)
- [Architecture Characteristics Drivers](requirements/drivers.md) 

### Things considered, but out of scope

For this iteration we decided to consider out of scope 
* the capabilities to allow Road Warrior to monetize its service and analytical data.
* security, which we considered as implicit in the solution
* deployment platform options


### Actors 

### Use Cases

### Quantums

We utilized the quantum concept (https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch07.html#sec-quantum-def) during our analysis to identify the different parts of the platform that serve different needs and demonstrate possibly different characteristics.

Our initial point was the following diagram(exploration/interactions.md):

* Email receiver
* External agent gateway
* Notification deduplicator
* Trip Monitor
* GUI serving APIs
* Web application 
* Mobile (native) application
* Social media gateway
* Trip access provider
* Reporting service
* Anaytics service


### Architecture Style (per Quantum)

We then focused on each quantum and discussed the characteristics that it should demonstrate. Here is what we came up with:

Note: Critical path 5 min - Availability + End to end performance

#### Email receiver
Top:
 Reliability:  Because we consider very important that the platform identifies reservations rather than the user creates them through the user interface.
 Availability: Because of possible API non-existence for some travel agents and possible interruptions in Sabre/Appolo. Email will be our last resort.
 Performance:  Because we have to process a lot more emails to identify the ones that are really relevant. Also we will need to process emails of all users, including inactive ones, at all times.
 Scalability:  Since we expect to go international - and we consider growth is a key metric for any startup - and email volume will be a multiple of user growth. 

Others considered:
 Fault tolerance: Not deemed important because 


#### External agent gateway
 Interoperability: Because we need to be able to interface with as many sources of relevant information as possible.
 Availability: Because we expect API notifications (especially from Sabre/Apollo) to arrive much faster than emails and be 100% accurate.
 Scalability: Because we will add additional data sources as time goes by. 

Others considered:


#### Notification Deduplicator
 Data Consistency: To provide accurate and up to date information to the user.
 Availability: Because it is the central component in the 'critical path' of the user's experience.

#### Trip Monitor
 Fault
 Configurability: To allow internationalization, different currencies etc. etc.

#### Gui service API's
 Deployability: Because we need to be able to perform A/B testing with different versions of
 Availability: Because the application must be available 
 Performance: 

#### 


### Architecture Style (overall)
Apart from quantume characteristics, the system must also demonstrate characteristics as a whole. We selected the following:

Top:
    Reliability: Because we do not want customers rushing to the airport due to a false alarm
    Scalability: To support future growth
    *Performance*????: To honour the required SLAs despite large number of moving parts with different characteristics

Others considered are:

Since we have several quantums with different performance characteristics, and considering the system as a whole, we decided to choose a distributed, event-driven architecture. 


























### Domain capabilities
Based on the output of the Event Storming, we defined the following capabilities for each of which we developed 
a microservice architecture: [Connection](domain/connection-capability.md), [Order](domain/order-capability.md), [User](domain/user-capability.md), [Report](domain/reporting-capability.md).

#### Capabilities Overview
The following diagram gives a high-level overview of how the capabilities interact with each other. An in-depth explanation of how each capability works internally
and what their responsibilities are, is shown in the section up next.
<p align="center">
<img width="900" src="domain/resources/hey-blue-capabilities-overview.drawio.svg">
</p>


### Legend
For all of the above, if not stated otherwise in the diagram at hand, the symbols reflect the meaning as described in the following legend.
<p align="center">
<img width="700" src="domain/resources/hey-blue-legend.drawio.svg">
</p>

## System Architecture

### Principles

The main principle we decided to adhere to 


### Approach
We used a [domain-driven approach](#domain-design) to define our [service landscape](#domain-capabilities) for the 
**Hey, Blue!** ecosystem. With those capabilities at hand, we finally propose a cloud-native software solution that can 
cope with the [requirements](#requirements) and is feasible to implement for an ambitious startup corporation. 
The design embraces [DevOps](https://en.wikipedia.org/wiki/DevOps), [GitOps](https://www.redhat.com/de/topics/devops/what-is-gitops) and 
[Zero Trust](https://en.wikipedia.org/wiki/Zero_trust_security_model) principles as first 
class citizens. As an exemplary cloud vendor we chose [Microsoft Azure](https://azure.microsoft.com/en-us/), however the solution
can easily be ported to other cloud platforms as described in [ADR07 Azure as a Hyperscaler](ADRs/2022-11-08_07-azure-hyperscaler.md).

Please refer the **[system architecture document](azure/resources/cloud-architecture.md)** for further explanations.


<p align="center">
<img width="1000" src="azure/resources/cloud_architecture-azure-overview-simple.drawio.png">
</p>

## Architecture Decision Records (ADR)
This summary provides an overview of the ADRs we refer to in the appropriate sections above. An ADR includes the context, i.e. the problem statement, a solution space, a decision, rationale and the decisions consequences.

- [2022-10-31 ADR01 Microservice Architecture](ADRs/2022-10-31_01-microservice-architecture.md)
- [2022-10-31 ADR02 Event-Driven Design](ADRs/2022-10-31_02-event-driven-design.md)
- [2022-10-31 ADR03 Points Redemption Framework](ADRs/2022-10-31_03-redeem-points.md)
- [2022-10-31 ADR04 Dispatcher Architecture](ADRs/2022-10-31_04-dispatcher-architecture.md)
- [2022-11-01 ADR05 Backend-for-Frontend Pattern](ADRs/2022-11-01_05-bff.md)
- [2022-11-06 ADR06 Read Replica Pattern](ADRs/2022-11-06_06-read-replica-pattern.md)
- [2022-11-08 ADR07 Azure as a Hyperscaler](ADRs/2022-11-08_07-azure-hyperscaler.md)
- [2022-11-08 ADR08 GDPR Compliance](ADRs/2022-11-08_08-GDPR-compliance.md)

## Acknowledgements
We would like to thank the team behind the O'Reilly Architectural Katas and the judges for their effort in making this instructive and fun event possible. Next, we would like to thank the team of Hey, Blue! for presenting such an interesting challenge with real-world usage and positive impact for society. Finally, we would like to thank our employer, Innovation Process Technology, for giving us the opportunity to participate in this challenge and working on our architectural skills. It's been one hell of a ride.

<p align="center">
<img width="600" src="context/resources/oreilly-archi-kata-fall-2022-team-ipt.svg">
</p>


<!--               NOTES                >


HTML IMG TEMPLATE FOR IMAGES

<p align="center">
<img width="800" src="relative/path/to">
</p>

-->
