## New Protocol Logic
This document is not meant to explain how the protocol works, but the logic behind building a new protocol rather that using an existing one.

The core protocol is meant to allow two peers to communicate securely. This also means that it needs to hanlde all the common issues in network communication; gracefully handling closed connections, dropped packets and so forth.

### Redundancy
With the increase in wireless transmission, it is important that an inheriently unreliable connection can be used to transmit a message with a desired level of reliability. Rather than using packet labeling and resend requests, we will rely on error correction, and always send a few extra packets.

### Security
One of the core principles of the Ribut project is decentralization. Heirarchical trust models do not fit with this goal. Ribut will instead need a distributed trust model.

This is specifically to address a "man-in-the-middle" attack. To verify that a public key is associated with a node, the node seeking verification can check with several trustworthy peers. In this case, trustworthy does not mean fully trusted, but a high degree of trust. If several nodes with a high (~90%) degreee of trust all agree that the key is associated with the node, it is safe to trust that. If there is disagreement, that may indicate a man-in-the-middle attack.

### P2P
Due to the nature of home routers, http can be hostile to p2p traffic. UDP tends to work much better. This is one of the reasons that the protocol will be built on udp.