---
title: "Creating Expressive System Diagrams in Draw.io and the Importance of System Design"
date: 2018-05-31T14:59:58-04:00
draft: false

featuredImage: "images/drawio/datamodel.jpg"
categories: ["software"]
tags: ["product design", "software development"]
author: "Nisarga Patel"
---

[Draw.io](https://draw.io) is an excellent free tool developed by Atlassian to allow developers and product managers to create expressive system designs. Draw.io supports the creation of [UML diagrams](https://www.uml-diagrams.org/), Entity Relationship diagrams, flow charts, and Business Process Modeling Notation (BPMN). In addition to this Draw.io supports a variety of icons in order to describe popular services contained within AWS, as well as other platforms.

##### Describing a simple microservice in Draw.io

<img src="/images/drawio/rules.png" width="300" />
<img src="/images/drawio/loadbalancing.png" width="300" />

Above is an example of simple rules microservice described with Draw.io. Much more complicated services and platforms can be designed via this software.

##### Never jump straight into the code!

Jumping into the code too early in the development process can lead to a lot of long term problems for development teams of any size. To prevent issues such as future technical debt, and integration errors, it is prudent to utilize tools such as Draw.io early in the development process.

##### Collaborating on UML Sequence Diagrams, and ER Diagrams

Draw.io also has support for sharing diagrams via Google Drive and support for designing UML sequence diagrams as well as entity relationship diagrams. For a recent Masters course in Software Engineering I recently used Draw.io to collaborate with a team of 4 to work on system architecture and ER diagrams for a semester long project in designing a websocket based board game.

##### Designing dummy services / throwaway prototypes early in the development process

After creating the system architecture design a development team may also choose (given they have enough time) to create dummy prototypes to mock up their system architecture. Tools such as [Apiary](https://apiary.io/) allow developers to mockup APIs. One can also quickly scaffold API services via an OpenAPI compliant RESTful API generator such as IBM's [loopback.io](http://loopback.io/). 

The more a development team can utilize diagraming software, code generation and boilerplates early in the development and design process the better grasp a team can get in regards to the final product. Creating expressive system architecture designs and prototype mockups are effective processes for early stage product development.

