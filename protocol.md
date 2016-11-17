## New Protocol Logic
This documents the logic behind building a new protocol rather that using an existing one (not and explaination of how the protocol works).

The core protocol lets two peers communicate securely. This
means it must handle common issues in network communication such as gracefully handling closed connections as well as dropped packets.

### Redundancy

It's important for (inheriently unreliable) connections to transmit messages with enough reliability, especially with the increase in wireless transmission. We will rely
on error correction and always send a few extra packets, rather than using packet labeling and resend requests.

### Security
Ribut will need a distributed trust model. A core principle of Ribut.us is decentralization, and hierarchical trust models do not meet this goal.

This specifically addresses "man-in-the-middle" attacks. The node seeking verification can check with several trustworthy peers to verify that a public key is associated with a node. 

In this case, trustworthy does not mean fully trusted, but a high degree of trust. If several nodes with a high (~90%) degreee of trust all agree that the key is associated with the node, it is safe to trust that key. Disagreement could indicate a man-in-the-middle attack.

### P2P
HTTP can be hostile to P2P traffic because of the nature of home routers. UDP tends
to work much better, which is one reason the protocol will be built
on UDP.
