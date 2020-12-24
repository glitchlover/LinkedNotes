---
cards-deck: Digital Communication::Swithching
---
# Switched network
## Taxonomy of switched networks
Here is the classification of switching network #card 
![](https://storage.googleapis.com/polar-32b0f.appspot.com/image/12eXTdmNQGZVC33JAQe4bEUmitii6kfwk6rr2vXD.png)
^1608724062439

### Circuit-Switched Networks
- What does Circuit Switched network made off? #card 
	- A circuit-switched network is made of a set of switches connected by physical links, in which each link is divided into n channels.
^1608724062867

- What Mux does it use? #card 
	- FDM and TDM
^1608724063285

- How many Phase does it have? #card
	-  **Circuit Establishment** : In this phase, a dedicated circuit is established from the source to the destination through a number of intermediate switching centres. The sender and receiver transmits communication signals to request and acknowledge establishment of circuits.
	- **Data Transfer** : Once the circuit has been established, data and voice are transferred from the source to the destination. The dedicated connection remains as long as the end parties communicate.
	- **Circuit Disconnection** : When data transfer is complete, the connection is relinquished. The disconnection is initiated by any one of the user. Disconnection involves removal of all intermediate links from the sender to the receiver.
^1608724063701

- How does the delay in this network looks like? #card 
	- ![[Pasted image 20201223175202.png]]

- A trivial circuit-switched network #card 
	- ![]( https://storage.googleapis.com/polar-32b0f.appspot.com/image/12frXNQQsRpaoAe1fi4Zae6a7ns452r2LLfD76RX.png)
^1608724064086


### Datagram Networks
How datagram Network works? 

A trivial datagram network -
![[Pasted image 20201223175323.png]]

### Virtual-Circuit Networks
- What is virtual circuit network? #card 
	- A virtual-circuit network is a cross between a circuit-switched network and a datagram network
	- ![image](https://storage.googleapis.com/polar-32b0f.appspot.com/image/1yToWpGXUDS5MoLJwDQpNgr5tAFmRotNqJS7r5Kb.png)

-  How does delay in a circuit-switched network works? #card 
	- ![]( https://storage.googleapis.com/polar-32b0f.appspot.com/image/12TMMuJiQb7MvGnQtY4UR2vFyjWiJDc1NG4i9DGb.png)


- Switching at the physical layer in the traditional telephone network uses the circuit-switching approach.
- Routing table in a datagram network
- In a   packet-switched   network,   there      is   no resource  reservation;  resources  are  allocated  on demand.
- The destination address in the header of a packet in a datagram network remains the same during the entire journey of the packet.
- Switching in the Internet is done by using the datagram approach to packet switching at the network layer
- Delay in a virtual-circuit network
- ![image](https://storage.googleapis.com/polar-32b0f.appspot.com/image/1LKFLQMy5u8oJQxBKB3EFzZN9oKiqday9Qut5Df5.png)
- Switching at the data link layer in a switched WAN is normally implemented by using virtual- circuit techniques
^1608724064459


### Virtual Circuit Identifier
definition:: VCI is a identifier of data transfer. It has only switch scope
^1608374044648

It is used by a frame between two switches. When a frame arrives at a switch, it has a VCI; when it leaves, it has a different VCI.
![](http://www.myreadingroom.co.in/images/stories/docs/dcn/Virtual%20Circuit%20Network_identifier.JPG)

#### Three Phases:

As in a circuit-switched network, a source and destination need to go through three phases in a virtual-circuit network: #card 
setup, data transfer, and teardown.  
- **setup phase**, the source and destination use their global addresses to help switches make table entries for the connection.
- In **the teardown phase**, the source and destination inform the switches to delete the corresponding entry.
- **Data transfer** occurs between these two phases.
^1608374045376


#### Setup Phrase
In the setup phase, a switch creates an entry for a virtual circuit. The following picture describes it #card
| setting up code                                                                                                                                                          | code is set                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| ![](https://2.bp.blogspot.com/-4jjw7rU8EnE/WHTH-soKoQI/AAAAAAAACis/wuLmQtqn8704L4o6DqU7aiUnfrUZd5LywCLcB/s1600/Setup%2Brequest%2Bin%2Ba%2Bvirtual-circuit%2Bnetwork.JPG) | ![](http://www.myreadingroom.co.in/images/stories/docs/dcn/Virtual%20Circuit%20Network_Data%20Transfer%20setup.JPG) |
^1608374046117

#### Data transfer phrase #card 
![](https://3.bp.blogspot.com/-Tl-marV0JTM/WHTIUYrhPkI/AAAAAAAACi4/EWqR1cmsov4nbX9HM1JJHT_BeqRT2SKagCLcB/s1600/Source-to-destination%2Bdata%2Btransfer%2Bin%2Ba%2Bvirtual-circuit%2Bnetwork.JPG)
^1608374046621

#### Teardown phrase
What happens? #card
In this phase, source A, after sending all frames to B, sends a special frame called a teardown request. Destination B responds with a teardown confirmation frame. All switches delete the corresponding entry from their tables.^1608374047001
