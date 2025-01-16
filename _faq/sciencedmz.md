---
layout: post
title: Science DMZ
feature-img: "assets/img/background-color.png"
date: November, 26 2024
---

The Science DZ is a network or a portion of network, designed to facilitate the transfer of  big science data.

Today’s general-purpose networks, also referred to as enterprise networks, are capable of efficiently transporting
basic data. These networks support multiple missions, including organizations’ operational services such as email,
procurement systems, and web browsing. However we may find some difficulties when transferring terabyte and
petabyte-scale science data.

<h2> Common Design goals of Science DMZ and Campus Enterprise Network </h2>

1) Serve a large number of users and platforms: desktops, laptops, mobile devices, supercomputers, tablets, etc. 

2) Support a variety of applications: email, browsing, voice, video, procurement systems, and others.

3) Provide security against the multiple threats that result from the large number of applications and platforms. 

4) Provide a level of Quality of Service (QoS) that satisﬁes user expectations. 

<h2>Science DMZ compared to a Campus Enterprise Network</h2>

Science DMZ connection to the WAN involves few network devices as possible,
to minimize the possibility of packet losses at intermediate devices.
The Science DMZ can also be considered as a security architecture, because
it limits the application types and corresponding ﬂows supported by end devices.
While ﬂows in Enterprise Networks are numerous and diverse, those in Science
DMZs are usually well-identiﬁed, enabling security policies to be tied to those ﬂows.

**Definition**: *A ﬂow is deﬁned as a set of IP packets passing an observation
point in the network during a certain time interval.*

<h2>Security-Related Differences Between Enterprise Networks and Science DMZs</h2>

<img src="/assets/img/projects/scienceDMZ/1.png" >

<h2>Inventory of the Science DMZ features</h2>

The main characteristics of a Science DMZ are the deployment of a friction-free
path between end devices across the WAN, the use of DTNs, the active performance
measurement and monitoring of the paths between the Science DMZ and the collaborator
networks, and the use of access-control lists (ACLs) and ofﬂine security appliances. 

<h3>1 . Friction-free network path</h3>

* The path has no devices that may add excessive delays or cause the packet to be
delivered out of order; e.g., ﬁrewall, IPS, NAT.
* The rationale for the Science DMZ design choice is to prevent any packet loss or retransmission which can trigger a decrease
in TCP throughput. 
* Data Transfer Nodes (DTNs) are connected to remote systems, such as collaborators’ networks, via the WAN.
* The high-latency path is composed of routers and switches which have large buffer sizes to absorb transitory packet bursts and prevent losses.

<h3>2 . Dedicated high-performance DTNs</h3>

* Are typically Linux devices built and conﬁgured for receiving WAN transfers at high speed.
* They use optimized data transfer tools such as [Globus](https://www.globus.org/).
* General-purpose applications (e.g. email clients, document editors, media players) are not installed.
* Having a narrow and speciﬁc set of applications simpliﬁes the design and enforcement of security policies.

<h3>3 . Performance measurement and monitoring point</h3>
The tool most used for this is the [pefSONAR](https://www.perfsonar.net/) toolkit.
It provides an automated mechanism to actively measure end-to-end metrics
such as throughput, latency, and packet loss. Contributing factors are:
* A primary high-capacity path that connects the Science DMZ with the WAN.
* Maintain a healthy path by identifying and eliminating soft failures in the network.
* Soft failures occur with minimum impact on, basic connectivity but high
  throughput can no longer be achieved.
* Examples of soft failures include failing components and routers forwarding
  packets using the main CPU rather than the forwarding plane. 

<h3>4 . ACLs and ofﬂine security appliances</h3>

The primary method to protect a Science DMZ is via router’s Access Control Lists (ACLs).
ACLs are implemented in the forwarding plane of a router and do not compromise
the end-to-end throughput. Additional ofﬂine appliances include payload-based
and ﬂow-based intrusion detection systems (IDSs).  

<img src="/assets/img/projects/scienceDMZ/2.png" >

<h2>Characteristics of the Data Link Layer</h2>
<ul>
	<li>Enables data movement over a link from one device to another.</li>
	<li>Media access control.</li>
	<li>Packet addressing.</li>
	<li>Formatting the frame that is used to encapsulate data.</li>
	<li>Error notification on physical layer.</li>
	<li>It orders bits and packets to and from data segments. This ensuing result is called frame. They contain data that are set in an orderly manner.</li>
	<li>Ensure error-free communication between two devices by correct transmission of frames.</li>
</ul>

<h2>Characteristics of the Network Layer</h2>
<ul>
	<li>Establishes paths that are used for the transfer of data packets between network devices.</li>
	<li>Provide a raffic direction.</li>
	<li>Addressing; Service and logical network addresses.</li>
	<li>Routing.</li>
	<li>Packet switching.</li>
	<li>Controlling packet sequence.</li>
	<li>Complete error detection; from sender to receiver.</li>
	<li>Congestion control.</li>
	<li>Gateway services.</li>
</ul>

<h2>Characteristics of the Transport Layer</h2>
<ul>
	<li>Responsible for message delivery between the network hosts. Messages are fragmented and reassembled by this layer. It also controls the reliability of any given link.</li>
	<li>Guaranteed delivery of data.</li>
	<li>Name resolution.</li>
	<li>Flow control.</li>
	<li>Error detection and recovery.</li>
</ul>

<h2>Characteristics of the Application Layer</h2>
<ul>
	<li>It works as an interface between the software and the network protocol on the computer. It provides services that are necessary to support the applications.</li>
	<li>This layer provides interface for FTP applications.</li>
</ul>

<h2>Data link and Network Layers devices</h2>

The essential functions performed by a router are 

<ul>
	<li>Routing: determination of the route taken by packets.  </li>
	<li>Forwarding:switching of a packet from the input port to the appropriate output port. </li>
</ul>

Traditional routing approaches such as static and dynamic routing (Open Shortest
Path First (OSPF), BGP ) are used in the implementation of Science DMZs.

Routing events, such as routing table updates, occur at the millisecond, second, or minute
timescale, on the other hand  with transmission rates of 10 Gbps and above, the forwarding
operation occurs at the nanosecond timescale. 

Best practices used in regular enterprise networks are applicable to Science DMZs.

<h3>Switching</h3>

<img src="/assets/img/projects/scienceDMZ/3.png" >

The above image is a generic router architecture. Modern routers may have a
network processor (NP) and a table derived from the routing table in each port,
which is referred to as the forwarding table (FT) or forwarding information base (FIB). 

Router queues/buffers absorb trafﬁc ﬂuctuations. Even in the absence of congestion,
ﬂuctuations are present, resulting mostly from coincident trafﬁc bursts.

To avoid HOL blocking, many switches use output buffering, a mixture of internal and
output buffering, or techniques emulating output buffering such as Virtual Output  Queueing  (VOQ).

There are critical switching attributes that must be considered for a
well-designed Science DMZ. These attributes are related to the characteristics
of the science DMZ trafﬁc and the role of switches in mitigating packet losses.

**Traffic Profile**: 

At a switch, buffer size, forwarding or switching rate, and queues should be selected
based on the trafﬁc proﬁle to be supported by the network. Enterprise networks and
Science DMZs are subject to different trafﬁc proﬁles.

Enterprise ﬂows are less sensitive than Science DMZ ﬂows to packet loss and throughput
requirements. Typically, the size of ﬁles in enterprise applications is small. Even
though packet losses reduce the TCP throughput, from a user perspective this reduction
results in a modest increase of the data transfer time. On the other hand, Science DMZ
applications typically transfer terabyte-scale ﬁles. Hence, even a very small packet
loss rate can cause the TCP throughput to collapse below 1 Gbps, as a result, a
terabyte-scale data transfer requires many additional hours or days to complete. 

A well-designed Science DMZ is minimally sensitive to latency. One of the goals of
the Science DMZ is to prevent packet loss and thus to sustain high throughput over
high latency WANs. Hence, the Science DMZ uses dedicated DTNs and switches capable
of absorbing transient bursts. It also avoids inline security appliances that may
cause packets to be dropped or delivered out of order. By fulﬁlling these requirements,
the achievable throughput can approach the full network capacity.

**Maximum Transmission Unit** :
The MTU has a prominent impact on TCP throughput. 

<img src="/assets/img/projects/scienceDMZ/4.png" >

The throughput is directly proportional to the MSS. Congestion control algorithms
perform multiple probes to see how much the network can handle. With high speed
networks, using half a dozen or so small probes to see how the network responds
wastes a huge amount of bandwidth. Similarly, when a packet loss is detected,
the rate is decreased by a factor of two. TCP can only recover slowly from this
rate reduction. The speed at which the recovery occurs is proportional to the MTU.
Thus, for Science DMZs, it is recommended to use large frames. 

**Buffer size of output or transmission ports**: 

The buffer size of a router’s output port must be large enough, since packets from
coincident arrivals from different input ports may be forwarded to the same output port.
Additionally, buffers prevent packet losses when trafﬁc bursts occur. 

‘ buffer size = C · RTT ‘

It is also know as  bandwidth-delay product (BDP).

**Bufferbloat**:

While allocating sufﬁcient memory for buffering is desirable, it is also important
to note that the term RTT in the above equation depends upon the use case at hand.
Hence, allocating additional unneeded buffer space may result in more latency.
This undesirable latency phenomenon is known as bufferbloat and can be mitigated by
avoiding the over-allocation of buffers. 

**Routers and switches in a hierarchical network**: 

<img src="/assets/img/projects/scienceDMZ/5.png" >

Above is a hierarchical network, The access layer represents the network edge, where
trafﬁc enters or exits the network. In Science DMZs, usually DTNs, supercomputer, and
research labs have access to the network through access layer switches. The distribution
layer interfaces between the access layer and the core layer, aggregating trafﬁc from
the access layer. The core layer is the network backbone. Core routers forward trafﬁc
at very high speeds. In this simpliﬁed topology, the core is also the border router,
connecting the network to the WAN. 

Access-layer switches must support a range of trafﬁc capacity needs, sometimes starting
as low as 10 Mbps and reaching to as much as 100 Gbps. This wide mix can strain the choice
of buffers required, particularly on output switch ports connecting to the distribution
layer. Speciﬁcally, buffer sizes must be large enough to absorb bursts from the end devices
(DTNs, supercomputer, lab devices). 

Distribution- and core-layer switches must have as much buffer space as possible to handle
the bursts coming from the access-layer switches and from the WAN. Hence, attention must
be paid to bandwidth capacity changes (e.g. aggregation of multiple smaller input ports
into a larger output port). 

Switches manufactured for datacenters may not be a good choice for Science DMZs. They
often use fabrics based upon shared memory designs. In these designs, the size of the
output buffers may not be tunable, which may become a key performance limitation
during the transfer of large ﬂows.

<h2>Comparison of Transport-Layer Features in Enterprise Networks and Science DMZS</h2>

<img src="/assets/img/projects/scienceDMZ/6.png" >

<h3>Network layer issues</h3>

The table above shows a comparison between enterprise networks and Science DMZs, regarding
transport-layer features. Reliability is required for ﬁle and dataset transfers.
Thus, Science DMZ applications use TCP. TLS and SSL also offer reliable service and security
on top of TCP, they introduce additional overhead and a redundant service. Globus, a
well-known application-layer tool for transferring large ﬁles, offers conﬁdentiality,
integrity and authentication services.

The ﬂow control rate is managed by the TCP buffer size. For Science DMZ applications, the
buffer size must be greater than or equal to the bandwidth-delay product. With this buffer
size, TCP behaves as a pipelined protocol. On the other hand, general-purpose applications
often use a small buffer size, which produces a stop-and-wait behavior. 

If the TCP buffer size at DTNs is smaller than the bandwidth-delay product, the utilization
of the channel is lower than 100%. The sender must constantly wait for acknowledgement
segments before transmitting additional data segments. On the other hand, if the buffer size
is greater than or equal to the bandwidth-delay product, the path utilization approaches the
maximum capacity and many datasegments are allowed to be in transit while acknowledgement
segments are simultaneously received. For small and short-duration ﬂows, this may not be essential.
However, for large ﬂows, to achieve full performance, the buffer size must be at least equal
to the bandwidth-delay product. The MSS is perhaps one of the most important features in
high-throughput high-latency networks with packet losses. TCP pacing is a promising feature.
The challenge for its wide adoption is the complexity of developing a mechanism to discover
the bottleneck link and its capacity.

<h3>Application layer tools</h3>

The essential end devices inside a Science DMZ are the DTNs and the performance monitoring stations.
DTNs run a data transfer tool while monitoring stations run a performance monitoring application,
typically perfSONAR. Other useful tools at deployment and evaluation times are WAN emulation and
throughput measurement applications. These tools are convenient because they facilitate early
performance evaluation without a need of connecting the Science DMZ to a real WAN.

**File Transfer Applications for Science DMZs** :

The prevalent tool for science data transfers is Globus gridFTP. The following description corresponds
to Globus, many of its features apply to other applications recommended for Science DMZs. 

Other ﬁle transfer applications for big data are Multicore Aware Data Transfer Middleware FTP (mdtmFTP)
and Fast Data Transport (FDT). mdtmFTP is designed to efﬁciently use the multiple computing cores
(multicore CPUs) on a single chip that are common in modern computer systems. mdtmFTP also improves the
throughput in DTNs that use a non-uniform memory access(NUMA) model. In the traditional Uniform Memory
Access (UMA) model, the access to the RAM from any CPU or core takes the same amount of time. 

FDT is an application optimized for the transfer of a large number of ﬁles. Hence, thousands of ﬁles
can be sent continuously, without restarting the network transfer between ﬁles. However, FDT and mdtmFTP
have not been widely adopted despite encouraging performance results .

<h3>Virtual Machines and Science DMZs</h3>

The idea behind a virtual machine is to abstract the hardware of a computer into several execution
environments. As a physical resource, access to a NIC is also shared. 

<img src="/assets/img/projects/scienceDMZ/7.png" >

While virtual technologies have been widely adopted in enterprise networks, their use in Science DMZs
has been discouraged for several reasons.

* The hypervisor represents a software layer that adds processing overhead.
* The physical NIC is potentially shared among multiple virtual machines.
* Even if the virtual DTN is the only virtual machine running on a physical
  server, the CPU must be shared with the hypervisor and the virtual switch.
* Commercial vendors may not disclose important attributes of the virtual switch,
  such as buffer size and switching architecture. 

Taking the limitations stated above into consideration, virtualization is not recommended for Science
DMZs operating at speeds above 10 Gbps.

<h3>Monitoring and performance applications for science DMZs</h3>

<ul>
	<li>One of the essential elements of a Science DMZ is the performance measurement and monitoring point.</li>
	<li>The monitoring process in Science DMZs focuses on multi-domain end-to-end performance metrics.</li>
	<li> On the other hand, the monitoring process in enterprise networks focuses on single-domain performance metrics.</li>
</ul>

<img src="/assets/img/projects/scienceDMZ/8.png" >

<h3>perfSONAR application</h3>

* It helps locate network failures and maintain optimal end-to-end usage expectations.
* It offers several services, including automated bandwidth tests and diagnostic tools.
* One of its main feature is its cooperative nature by which an institution can measure several metrics (e.g., throughput, latency, packet loss) to different intermediary domains and to a destination network. 

Based on the below figure, campus network 1 can measure metrics from itself to campus network 2. Campus network 1 can also measure metrics to the service providers.

<img src="/assets/img/projects/scienceDMZ/9.png" >

Comparisons can be drawn between SNMP and perfSONAR

<img src="/assets/img/projects/scienceDMZ/10.png" >

