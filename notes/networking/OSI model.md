## What is the OSI model?

The **open systems interconnection** (OSI) model is a conceptual model created by the international organization for standardization which enables diverse communication systems to communicative using [standard protocols](common%20protocols). In plain English, the OSI provides a standard for different computer systems to be able to communicate with each other.

The OSI model can be seen as a universal language for computer networking. It is based on the concept of splitting up a communication system into seven abstract layers, each one stacked upon the last.

![[notes/networking/osi-model.png]]

Each layer of the OSI model handles a specific job and communicates with the layers above and below itself. DDoS attacks target specific layers of a network connection; Application layer attacks target layer 7 and protocol layer attacks target layer 3 and 4.

## Why does the OSI model matter?

Although the modern internet does not strictly follow the OSI model (it more closely follows the simpler internet protocol suite), the OSI model is still very useful for troubleshooting network problems. Whether it's one person who can't get their laptop on the internet, or a website being down for thousands of users, the OSI model can help to break down the problem and isolate the source of the trouble. If the problem can be narrowed down to one specific layer of the model, a lot of unnecessary work can be avoided.

## What are the 7 layers of the OSI model?

#### 7. The application layer

![[notes/networking/osi-model-layer-7.png]]

This is the only layer that directly interacts with the data from the user. Software application like web browsers and email clients rely on the application layer to initiate communications. But it should be made clear that client software applications are not part of the application layer; Rater the application layer is responsible for the protocols and data manipulation that the software relies on to present meaningful data to the user.

Application layer protocols include [HTTP](common%20protocols) as well as [SMTP](common%20protocols) (simple main transfer protocol is one of the protocols that enables email communications).

#### 6. The presentation layer

![[notes/networking/osi-model-layer-6.png]]

This layer is primarily responsible for preparing data so that it can be used by the application layer; in other words, layer 6 makes the data presentable for applications to consume. The presentation layer is responsible for translation, encryption, and compression of data.

Two communicating devices communicating may be using different encoding methods, so layer 6 is responsible for translating incoming data into a syntax that the application layer of the receiving device can understand.

If the devices are communicating over an encrypted connection, layer 6 is responsible for adding the encryption on the sender's end as well as decoding the encryption on the receiver's end so that it can be present the application layer with unencrypted, readable data.

Finally the presentation layer is also responsible for compressing data it receives from the application layer before delivering it to layer 5. This helps improve the speed and efficiency of communication by minimizing the amount of data that will be transferred. 

#### 5. The session layer

![[notes/networking/osi-model-layer-5.png]]

This is the layer responsible for opening and closing communication between the two devices. The time between when the communication is opened and closed is known as the session. The session layer ensures that the session stays open long enough to transfer all the data being exchanged, and then promptly closes the session in order to avoid wasting resources.

The session layer also synchronizes data transfer with checkpoints. For example, if a 100 megabyte file is being transferred, the session layer could set a checkpoint every 5 megabytes. In the case of a disconnect or a crash after 52 megabytes have been transferred, the session could be resumed from the last checkpoint, meaning only 50 more megabytes of data need to be transferred. Without the checkpoints, the entire transfer would have to begin again from scratch.

#### 4. The transport layer

![[notes/networking/osi-model-layer-4.png]]

Layer 4 is responsible for end-to-end communication between the two devices. This includes taking data from the session layer and breaking it up into chunks called segments before sending it to layer 3. The transport layer on the receiving device is responsible for reassembling the segments into data the session layer can consume.

The transport layer is also responsible for flow control and error control. Flow control determines an optimal speed of transmission to ensure that a sender with a fast connection does not overwhelm a receiver with a slow connection. The transport layer performs error control on the receiving end by ensuring that the data received is complete, and requesting a re-transmission if it isn't.

Transport layer protocols include the [transmission control protocol (TCP)](common%20protocols) and the [user datagram protocol (UDP)](common%20protocols).

#### 3. The network layer

![[notes/networking/osi-model-layer-3.png]]

The network layer is responsible for facilitating data transfer between two different networks. If the two devices communicating are on the same network, then the network layer is unnecessary. The network layer breaks up segments from the transport layer into smaller units, called [packets](notes/networking/network%20basics.md), on the sender's device, and reassembling these packets on the receiving device. The network layer also finds the best physical path for the data to reach its destination; This is known as [routing](notes/networking/network%20basics.md).

Network layer protocols include IP, the internet control message protocol (ICMP), the internet group message protocol (IGMP), and the IPsec suite.

#### 2. The data link layer

![[notes/networking/osi-model-layer-2.png]]

The data link layer is very similar to the network layer, except the data link layer facilitates data transfer between two devices on the same network. The data link layer takes packets from the network layer and breaks them into smaller pieces called frames. Like the network layer, the data link layer is also responsible for flow control and error control in inter-network communication (The transport layer only does flow control and error control for inter-network communications).

#### 1. The physical layer

![[notes/networking/osi-model-layer-1.png]]

This layer includes physical equipment involved in the data transfer, such as the cables and switches. This is also the layer where the data gets converted into a bit stream, which is a string of 1s and 0s. The physical layer of both devices must also agree on a signal convention so that the 1s can be distinguished from the 0s on both devices.

## How data flows through the OSI model

In order for human-readable information to be transferred over a network from one device to another, the data must travel down the seven layers of the OSI model on the sending device and then travel up the seven layers on the receiving end.

For example: Mr. Cooper wants to send Ms. Sophia an email. Mr. Cooper composes his message in an email application on his laptop and then hits "send". His email application will pass his email message over to the application layer, which will pick a protocol (SMTP) and pass the data along to the presentation layer. The presentation layer will compress the data and then it will hit the session layer, which will initialize the communication session.

The data will then hit the sender's transportation layer where it will be segmented, then those segments will be broken up into packets at the network layer, which will be broken down even further into frames at the data link layer. The data link layer will then deliver those frames to the physical layer, which will convert the data into a bit stream of 1s and 0s and send it through a physical medium, such as a cable.

Once Ms. Sophia's computer receives the bit stream through a physical medium (such as her WiFi), the data will flow through the same series of layers on her device, but in the opposite order. First the physical layer will convert the bit stream from 1s and 0s into frames that get passed to the data link layer. The data link layer will then reassemble the frames into packets for the network layer. The network layer will then make segments out of the packets for the transport layer, which will reassemble the segments into one piece of data.

The data will then flow into the receiver's session layer, which will pass the data along to the presentation layer and then end the communication session. The presentation layer will then remove the compression and pass the raw data up to the application layer. The application layer will then feed the human-readable data along to Ms. Sophia's email software, which will allow her to read Mr. Cooper's email on her laptop screen.