### 1 Introduction

Subnetting is the process of creating a subnetwork (also know as a subnet) within a network. Network interface and devices within a subnet can communicate with each other directly. Routers facilitate communication between different subnets.

This paper will touch on networking/subnetting terminology and network topologies. We will take a look at some common protocols, ports and their uses.

### 2 Types of Networking

There are different types of networking. Lets take a look at 4 of the most common ones.

#### 2.1 LAN

LAN - Local Area Network. This is a group of computers and devices interconnected within a limited area like an office, school campus or even a home. These network facilitate sharing of resources, data and applications among connected devices. They can be both wired and wireless (WLAN).

#### 2.2 WLAN

WLAN - Wireless Area Network. This is a type of network that uses wireless communication to connect devices on a local network (subnet). Mobile devices such as smartphones and laptops use WLAN connection to wirelessly connect to the router.

#### 2.4 MAN

MAN - Metropolitan Area Network. This is a type of computer network that spans across a metropolitan area or a large geographical area, typically covering a city or a region. It is designed to interconnect various LANs and WANs to enable communication and data exchange between different locations within the metropolitan area.

#### 2.3 WAN

WAN - Wide Area Network. This is a group of networks that cover wider geographical areas than LAN (Local Area Network) which is confined to a smaller geographical area. WAN connects LANs from around the world for global exchange of information and data. A WAN can be privately owned and managed, or leased from telecommunication service providers.

### 3 Terminology

Brief overview of abbreviations used in networking, their meaning and other terminology.

#### 3.1 CIDR

Classless Inter-Domain Routing. Is a method of allocating IP addresses and routing internet protocol packets in a more flexible and efficient way.

#### 3.2 VLAN

Virtual Local Area Network is a logical grouping of devices or users within a network, based on shared attributes or users within a network, based on shared attributes like location, department, or security requirements. VLANs play a crucial role in improving network security, enabling better resource allocation, and simplifying network management.

#### 3.3 DMZ

De-Militarized Zone is a specific part of a network that functions as a buffer or separation between an organization's internal, trusted network and the external, untrusted networks like the internet.

#### 3.4 ARP

Address Resolution Protocol used by the internet protocol (IP) to map IP address to a physical address, also known as a media access control (MAC) address. ARP is essential for routing data between devices in a local area network (LAN) as it allows for the translation of IP addresses to specific hardware on the network.

#### 3.5 NAT

Network Address Translation is a key element in modern network security. It acts as a middleman between devices on your local area network (LAN) and the external internet. NAT helps to conserve IP addresses and improve privacy and security bu translating IP addresses within private networks to public IP addresses for communication on the internet.

#### 3.6 IP

Internet Protocol, is a fundamental concept in networking that refers to the way data is transferred across networks, specifically the internet. It is a core component of the internet's architecture and serves as the primary building block for communication between deices connected to the network.

#### 3.7 DNS

Domain Name System is a key component in the internet infrastructure that translates human-friendly domain names into IP addresses. This translation process enables us to easily connect to websites and other online resources without having to remember complex numeric IP addresses.

#### 3.8 DHCP

Dynamic Host Configuration Protocol is a network protocol that enables automatic assignment of IP addresses to devices on a network. It is an essential component of IP networking and aims to simplify the process of configuring devices to communicate over an IP-based network.

#### 3.9 VPN

Virtual Private Network is a technology that provides secure and encrypted connections between devices over a public network, such as the internet. VPNs are primarily used to protect your internet activity and privacy from being accessed or monitored by external parties, such as hackers or government agencies.

#### 3.10 localhost

Localhost (also known as loopback address) is a term used to define a network address that is used by a device (usually a computer or a server) to refer to itself. In other words, it's a way for your device to establish a network connection to itself. The most commonly used IP address for localhost is `127.0.0.1`, which is reserved as loopback address in IPv4 network. For IPv6 networks, it's represented by `::1`.

#### 3.11 loopback

Loopback is an essential concept in IP terminology that refers to a test mechanism used to validate the operation of various network protocols, and software or hardware components. The primary function of the loopback feature is to enable a device to send a data packet to itself to verify if the device's network stack is functioning correctly.

#### 3.12 Subnet Mask

A subnet mask is a crucial component of internet protocol (IP) addressing, acting as a "mask" to separate the network portion of an IP address from the host portion. It is a 32-bit number representing a sequence of 1's followed by a sequence of 0's used o define the boundary of a subnet within a given IP address.

#### 3.13 Default Gateway

We now arrive at the topic of default gateway. Understanding the role and importance of the default gateway in a network is crucial for rasping the fundamentals of networking and data routing.

The default gateway is basically a device (usually a router) on a network which serves as an access point for data traffic to travel from the local network to other networks, such as the internet. This device acts as a "middleman" between your computer and external networks, and is often set up by your internet service provider (ISP) or during the configuration of your own router.