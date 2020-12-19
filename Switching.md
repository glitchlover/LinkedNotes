---
cards-deck: Digital Communication::Swithching
---

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
