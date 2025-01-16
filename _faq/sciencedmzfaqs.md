---
layout: post
title: Science DMZ FAQs
feature-img: "assets/img/background-color.png"
date: November, 26 2024
---
## General

What is the Science DMZ?
> It is a network or a portion of network, designed to facilitate the transfer of  big science data.

Where can I learn more about the Science DMZ?
> [The Energy Science Network](https://www.es.net/science-engagement/technical-and-consulting-services/the-science-dmz-architecture-and-security/) has more information on the Science DMZ.

## Technical

What are the minimum system requirements?
> Unless you have a high-performance workstation chances are your hardware is not immediately compatible with the Science DMZ. Users may need to upgrade their systems to include a disk system capable of transfer speeds over the standard 1 Gigabit per second. The 10GbE network enables speeds of up to 1.25 Gigabytes per second. Standard SATA hard drives see speeds of around 150 Megabytes per second, or about 1/10th of the available Science DMZ bandwidth.
> The following is a list of must-haves for your system:
> * A workstation with an available PCIe 2.0 x8 slot
> * 10GbE Network Card
> * Storage system capable of high bandwidth transfers
>   * Single SSD drive
>   * Array of SATA/SSD disks

What software is necessary to leverage the Science DMZ?
> Traditional file transfer protocols do not support the increased bandwidth available to users on the science DMZ.
> There are two programs commonly used to move large datasets over high-bandwidth networks:
> * [Globus](https://docs.globus.org/)
> * [bbcp](https://www.slac.stanford.edu/~abh/bbcp/)         
> Both your local workstation and the remote data source will need matching software.

How can I verify the Science DMZ speeds?
> Several network performance diagnostics tools will be available to test connectivity speeds.
> * [perfSONAR Dashboads](https://fasterdata.es.net/performance-testing/perfsonar/esnet-perfsonar-dashboard/community-perfsonar-dashboards/) perfSONAR is the **perf**ormance **S**ervice-*O*riented **N**etwork monitoring **AR**chitecture, a network measurement toolkit designed to provide federated coverage of paths and help to establish end-to-end usage expectations. 
> * [iPerf/iPerf3](https://iperf.fr) iPerf3 is a tool for active measurements of the maximum achievable bandwidth on IP networks. It supports tuning of various parameters related to timing, buffers and protocols (TCP, UDP, SCTP with IPv4 and IPv6). For each test, it reports the bandwidth, loss, and other parameters.
> * [One-Way Ping (OWAMP)](http://software.internet2.edu/owamp/) OWAMP is a command-line client application and a policy daemon used to determine one-way latencies between hosts.


Can I connect to the Science DMZ with an Apple computer?
> Yes. Apple computers can connect to the Science DMZ provided they have a Thunderbolt port and an [external network card](https://store.apple.com/us/product/HC294LL/A/atto-thunderlink-nt1102-thunderbolt-to-10-gbits-ethernet-desklink-device)
> Please review the minimum workstation system requirements to determine if a hardware upgrade will be required.

## Security

Can I access resources on the Science DMZ from outside the network?

> Yes, services within the Science DMZ can be available outside the network.

