## Computer networks

You might think that computers and networks always went hand in hand, but actually most computers pre-1970 were humming away all alone. However, as big computers began popping up everywhere, and low cost machines started to show up on people's desks, it became increasingly useful to share data and resources, and the first networks of computers appeared.

The first computer networks appeared in the 1950s and 60s. They were generally used within an organization - like a company or a research lab - to facilitate the exchange of information between different people and computers. This was faster and more reliable than the previous method of having someone walk a pile of punch cards, or a reel of magnetic tape, to a computer on the other side of a building - which was later budded a sneakernet. A second benefit of networks was the ability to share physical resources. For example, instead of each computer having its own printer, everyone could share one attached to the network. It was also common on early networks to have large, shared, storage drives, ones too expensive to have attached to every machine. These relatively small networks of close-by computers are called **local area networks** (LAN). A LAN could be as small as two machines in the same room, or as large as a university campus with thousands of computers. 

## Ethernet - shared carrier

Although many LAN technologies were developed and deployed, the most famous and successful was **Ethernet**, developed in the early 1970s at Xerox PARC, and still widely used today. In its simplest form, a series of computers are connected to a single, common Ethernet cable. When a computer wants to transmit data to another computer, it writes the data as an electrical signal, onto the cable. Of course, because the cable is shared, every computer plugged into the network sees the transmission, but doesn't know if data is intended for them or another computer. To solve this problem, Ethernet requires that each computer has a unique **media access control** address (MAC). The unique address is put into a header that prefixes any data sent over the network. So, computers simply listen to the Ethernet cable, and only process data when they see their address in the header. This works really well, every computer made today comes with its own unique MAC address for both Ethernet and WiFi. 

The general term for this approach is **carrier sense multiple access** (CSMA). The "carrier", in this case, is any shared transmission medium that carries data - copper wire in the case of Ethernet, and the air carrying radio waves for WiFi. 

Many computers can simultaneously sense the carrier, hence the "sense" and "multiple access", and the rate at which a carrier can transmit data is called its bandwidth.

## Shared carrier drawback

Unfortunately, using a shared carrier has one big drawback. When network traffic is light, computers can simply wait for silence on the carrier, and then transmit their data. But, as network traffic increases, the probability that two computers will attempt to write data at the same time also increases. This is called a collision, and the data gets all garbled up, like two people trying to talk on the phone at the same time. Fortunately, computers can detect these collisions by listening to the signal on the wire. The most obvious solution is for computers to stop transmitting, wait for silence, then try again. Problem is, the other computer is going to try that too, and other computers on the network that have been waiting for the carrier to go silent will try to jump in during any pause. This just leads to more and more collisions. Soon, everyone is talking over one another and has a backlog of things they need to say. Ethernet had a surprisingly simple and effective fix. When transmitting computers detect a collision, they wait for a brief period before attempting to re-transmit. As an example, let's say 1 second. Of course, this doesn't work if all the computers use the same wait duration - they'll just collide again one second later. So, a random period is added: one computer might wait 1.3 seconds, while another waits 1.6. With any luck, the computer that waited 1.3 seconds will wake up, find the carrier to be silent, and start transmitting. When the 1.6 second computer wakes up a moment later, it'll see that the carrier is in use, and will wait for the other computer to finish. This definitely helps, but doesn't totally solve the problem, so an extra trick is used. As I just explained, if a computer detects a collision while transmitting, it will wait 1 second, plus some random extra time. However, if it collides again, which suggests network congestion, instead of waiting another 1 second, this time it will wait 2 seconds. If it collides again, it'll wait 4 seconds, and then 8... and so on, until it's successful.

With the computers backing off, the rate of collisions goes down, and data starts moving again, freeing up the network. This "backing off" behavior using an exponentially growing wait time is called exponential backoff. Both Ethernet and WiFi use it, and so do many transmission protocols.

But even with clever tricks like exponential backoff, you could never have an entire university's worth of computers on one shared Ethernet cable. To reduce collisions and improve efficiency, we need to shrink the number of devices on any given shared carrier - what's called the collision domain.

## Network switch

Let's go back to our earlier Ethernet example, where we had six computers on one shared cable, aka one collision domain. To reduce the likelihood of collisions, we can break this network into two collision domains by using a **network switch**. It sits between our two smaller networks, and only passes data between them if necessary. It does this by keeping a list of what MAC addresses are on what side of the network.

```
A    B    C
|    |    |
+----+----+
     |
   Switch
     |
+----+----+
|    |    |
D    E    F
```

So if A wants to transmit to C, the switch doesn't forward the data to the other network - there's no need. This means if E wants to transmit to F at the same time, the network is wide open, and two transmissions can happen at once. But, if F wants to send data to A, then the switch passes it through, and the two networks are both briefly occupied. This is essentially how big computer networks are constructed, including the biggest one of all - **the internet** - which literally inter-connects a bunch of smaller networks, allowing inter-network communication.

What's interesting about these big networks, is that there's often multiple paths to get data from one location to another. And this brings us to another fundamental networking topic, routing.

## Routing

The simplest way to connect two distant computers or networks, is by allocating a communication line for their exclusive use. This is how early telephone systems worked. This approach is called a **circuit switching**, because you're literally switching whole circuits to route traffic to the correct destination. It works fine, but it's relatively inflexible and expensive, because there's often unused capacity.

On the upside, once you have a line to yourself - or if you have the money to buy one for your private use - you can use it to its full capacity, without having to share. For this reason the military, banks and other high importance operations still buy dedicated circuits to connect their data centers.

## Message switching

Another approach for getting data from one place to another is **message switching**, which is sort of like how the postal system works. Instead of a dedicated route from A to B, messages are passed through several stops.

So if George writes a letter to Nick, it might go from Tbilisi to Mtskheta, and then hop to Khashuri, then Borjomi, and then finally make it to Batumi. Each stop knows where to send it next because they keep at table of where to pass letters, given a destination address. What's neat about message switching is that it can use different routes, making communication more reliable and fault-tolerant. Sticking with our mail example, if there's a blizzard in Borjomi grinding things to a halt, the Bakuriani mail hub can decide to route the letter through Omaha instead. In our example. cities are acting like network routers. The number of hops a message takes along a route is called the hop count. Keeping track of the hop count is useful because it can help identify routing problems. For example, let's say Bakuriani thinks the fastest route to Batumi is through Borjomi but Borjomi thinks the fastest route is through Bakuriani. That's bad, because both cities are going to look at the destination address, Batumi, and end up passing the message back and forth between them, endlessly. Not only is this wasting bandwidth, but it's a routing error that needs to get fixed! This kind of error can be detected because the hop count is stored with the message and updated along its journey. If you start seeing messages with high hop counts, you can bet something has gone awry in the routing! This threshold is called the **hop limit**.

A downside to message switching is that messages are sometimes big. So, they can clog up the network, because the whole message has to be transmitted from one stop to the next before continuing on its way. While a big file is transferring, that whole link is tied up. Even if you have a tiny, one kilobyte email trying to get through, it either has to wait for the big file transfer to finish or take a less efficient route. That's bad. The solution is to chop up big transmission into many small pieces, called packets.

## Packets

Just like with message switching, each packet contains a destination address on the network, so routers know where to forward them. This format is defined by the **internet protocol** (IP), a standard created in the 1970s.

Every computer connected to a network gets an IP address. You've probably seen these as four, 8-bit numbers written with dots in between. For example, `172.217.169.110` is an IP address for one of Google's servers.

With millions of computers online, all exchanging data, bottlenecks can appear and disappear in milliseconds. Network routers and constantly trying to balance the load across whatever routes they know to ensure speedy reliable delivery, which is called **congestion control**. 

## Congestion control

Sometimes different packets from the same message take different routes through a network. This opens the possibility of packets arriving at their destination out of order, which is a problem for some applications. Fortunately, there are protocols that run on top of IP, like **TCP/IP**, that handle this issue.

## Packet switching

Chopping up data into small packets, and passing these along flexible routes with spare capacity, is so efficient and fault-tolerant, it's what the whole internet runs on today. This routing approach is called **packet switching**. It also has the nice property of being decentralized, with no central authority or single point of failure. In fact, the threat of nuclear attack is why packet switching was developed during the cold war.

Today, routers all over the globe work cooperatively to find efficient routings, exchanging information with each other using special protocols, like the **internet control message protocol** (ICMP) and the **border gateway protocol** (BGP). The world's first packet-switched network, and the ancestor to the modern internet, was the ARPANET, named after the US agency that funded it, the advanced research projects agency.

## References

[Computer Networks: Crash Course Computer Science](https://youtu.be/3QhU9jd03a0)