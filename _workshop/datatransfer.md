---
layout: post
title: Persistent Data Transfer over the Science DMZ
feature-img: "assets/img/background-color.png"
date: 26 November 2024
---
## Introduction
The Science DMZ as defined by [ESnet](https://fasterdata.es.net/science-dmz/)
is a portion of the network, built at or
near the campus or laboratory's local network perimeter
that is designed such that the equipment, configuration,
and security policies are optimized for high-performance
scientific applications rather than for general-purpose
business systems or “enterprise” computing.

Data is the object that connect scientists and instruments
within the Science DMZ. The design and set up of the Science
DMZ, limits the number of applications that exposes the  network
to the rest of the world. to this effect, Globus is the application
most in use.

### Why Use Globus?
Why Use the Globus Platform?

Globus provides scalable, secure solutions to the research community:

* It enables login using linked external identities; Globus federates
  identities from over 150 identity providers including InCommon, Google,
  XSEDE and Internet2.       
* It allows for the transfer of large datasets fast, securely, and reliably.    
* Improves collaboration among users using Globus-based access control to
  simplify data sharing within and beyond institutional boundaries.   
* New Globus application services can be set up and running in minutes.    
* Enable secure, scalable search using custom metadata.    
* It eliminates time wasted managing user identities and ACLs for sharing
  data with external users.   
* Use open RESTful APIs, with fine grained authorization.         
* Leverage the growing number of Globus endpoints at hundreds of
  institutions worldwide.

The Globus platform is built on widely adopted industry standards such as
OAuth and OpenID Connect for authentication/authorization, and uses trusted
protocols such as GridFTP and HTTPS. We are going to explore the use of Globus
for data transfer as follow:

### Globus Setup
* [Retrieve a Distinguished Name (DN)](https://gcrnet.github.io/howto/dn)
* [Install Globus Connect Personal](https://gcrnet.github.io/howto/globusconnectpersonal)
* [Set up Globus Connect Personal](https://gcrnet.github.io/howto/setupglobusconnect)

### Data Transfer with Globus App
* [Using Globus Connect Personal](https://gcrnet.github.io/howto/usingglobusconnectpersonal)
* [File transfer using Globus](https://gcrnet.github.io/tutorials/filetransfer.html)

### Advanced, Data Transfer with Globus
* [Using Globus at the Command Line](https://gcrnet.github.io/tutorials/globus_cli.html)
* [Access Globus from a Jupyter Notebook](https://gcrnet.github.io/tutorials/globus_in_jupyter-nbk.html)

### Extra Material
* [Automating Data Transfer with Globus](https://github.com/globus/automation-examples)
* [Subscribe to the Globus Mailing List](https://www.globus.org/mailing-lists)
* [Globus Office Hours](https://www.globus.org/events/globus-office-hours-4)
* [Globus Platform Services](https://www.globus.org/platform/services)
