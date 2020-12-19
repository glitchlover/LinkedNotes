### Virtual Circuit Identifier
definition:: VCI is a identifier of data transfer. It has only switch scope

It is used by a frame between two switches. When a frame arrives at a switch, it has a VCI; when it leaves, it has a different VCI.
![](http://www.myreadingroom.co.in/images/stories/docs/dcn/Virtual%20Circuit%20Network_identifier.JPG)

#### Three Phases:

As in a circuit-switched network, a source and destination need to go through three phases in a virtual-circuit network: #card 
setup, data transfer, and teardown.  
- setup phase, the source and destination use their global addresses to help switches make table entries for the connection.
- In the teardown phase, the source and destination inform the switches to delete the corresponding entry.
- Data transfer occurs between these two phases.


#### Setup Phrase
In the setup phase, a switch creates an entry for a virtual circuit.
| setting up code                                                                                                                                                          | code is set                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| ![](https://2.bp.blogspot.com/-4jjw7rU8EnE/WHTH-soKoQI/AAAAAAAACis/wuLmQtqn8704L4o6DqU7aiUnfrUZd5LywCLcB/s1600/Setup%2Brequest%2Bin%2Ba%2Bvirtual-circuit%2Bnetwork.JPG) | ![](http://www.myreadingroom.co.in/images/stories/docs/dcn/Virtual%20Circuit%20Network_Data%20Transfer%20setup.JPG) |

