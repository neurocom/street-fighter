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

**[2. Challenge Overview](#challenge-overview)**
* [2.1. Vision](#the-vision)
* [2.2. Scope](#the-scope)

**[3. Domain Design](#domain-design)**
* [3.1. Actors and Use Cases](#use-cases)
* [3.2. Quantum Identification](#)

**[4. System Architecture](#system-architecture)**
* [4.1. System-wide architecture characteristics](azure/resources/cloud-architecture.md)
* [4.2. Overall Architecture](azure/resources/cloud-architecture.md)
* ??????? OVERALL ARCHITECTURE ADR????????????
* [4.3. Per Quantum Architecture]
* [4.3.1. User Interaction Quantum]()
* [4.3.2 Travel Notification Receiver]()
* [4.3.4 Email Receiver]()
* [4.3.5 Reservation Orchestrator]()
* [4.3.6 Analytics Collector]()
* [4.3.7 Activity Summarizer]()


**[6. Acknowledgements](#acknowledgements)**
    </td>
 </tr>
</table>
</center>

## About Us
Our team consists of [Apostolos Mantes](https://www.linkedin.com/in/mantesap), [George Lourakis](https://www.linkedin.com/in/georgios-lourakis-099b79197), [George Panagiotakis](https://www.linkedin.com/in/yiorgos-panayiotakis-71185a5b), [Konstantinos Polydorou](htts://www.linkedin.com/in/kpolyd) and [Spyros Economopoulos](https://www.linkedin.com/in/economopoulos). We are members of [Neurocom SA](https://www.neurocom.gr), a greek company focusing mainly on the telecommunication sector, located in Greece.


## Challenge Overview

### The Vision

Be the single source of truth for all things trip related.

### The Scope

At this stage focus on 
* flights
* hotels and 
* car rentals

Keep in mind the vision and consider how the platform will embrace trains, buses, attractions etc. etc.

# Domain Design

## Actors and Use Cases

We grouped our understanding of the requirements for the **Road Warrior** platform into the following two sections.
- [Functional requirements](requirements/functional-requirements.md)
- [Architecture Characteristics Drivers](requirements/drivers.md)

## Quantum Identification

### Things considered, but out of scope

For this iteration we decided to consider out of scope
* the capabilities to allow Road Warrior to monetize its service and analytical data.
* Trip access provider
* deployment platform options


### Actors 

### Use Cases

### Quantums

We utilized the quantum concept (https://learning.oreilly.com/library/view/fundamentals-of-software/9781492043447/ch07.html#sec-quantum-def) during our analysis to identify the different parts of the platform that serve different needs and demonstrate possibly different characteristics.

Our initial point was the following diagram(exploration/interactions.md):

* Email receiver
* External agent gateway
* Event deduplicator
* Trip Ledger
* GUI serving APIs
* Web application 
* Mobile (native) application
* Social media gateway
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

Architectural Style: Event Driven (Pipeline?)

#### External agent gateway
 Interoperability: Because we need to be able to interface with as many sources of relevant information as possible.
 Availability: Because we expect API notifications (especially from Sabre/Apollo) to arrive much faster than emails and be 100% accurate.
 Scalability: Because we will add additional data sources as time goes by. 

Others considered:

Architectural Style: Microservices (Pipeline ???)

#### Event Deduplicator
 Data Consistency: To provide accurate and up to date information to the user.
 Availability: Because it is the central component in the 'critical path' of the user's experience.

Architectural Style: Service Oriented?

#### Trip Ledger
 Fault
 Configurability: To allow internationalization, different currencies etc. etc.

Architectural Style: Service Oriented

#### Gui service API's
 Deployability: Because we need to be able to perform A/B testing with different versions of
 Availability: Because the application must be available 
 Performance: 

Architectural Style: Service Oriented

### Architecture Style (overall)
Apart from quantume characteristics, the system must also demonstrate characteristics as a whole. We selected the following:

Top:
    Reliability: Because we do not want customers rushing to the airport due to a false alarm
    Scalability: To support future growth
    *Performance*????: To honour the required SLAs despite large number of moving parts with different characteristics

Others considered:
    Security, which we considered as implicit in the solution

Since we have several quantums with different performance characteristics, and considering the system as a whole, we decided to choose a distributed, event-driven architecture. 

## Acknowledgements
