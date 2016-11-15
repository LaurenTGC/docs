## Security

### Heisenburg Anonymity
A user may have several active identities when logged into Ribut. They will
probably have one for each application. And their IP will be used to participate
in the overlay network. Apps must follow the Heisenburg Anonymity Rule - the
network can know and identity or a location (IP), never both.

Without this rule, the problem goes like this. Alice is connected to Speakeasy
and talks to Bob, which reveals a unique IP:Port address. Later Alice uses a
different application to search for a medical term. Since the services are all
p2p, her search goes out to many users. This wouldn't be problem, because none
of the nodes seeing the search should know that it's Alice doing the search. But
if Bob sees the search and the search also shows the IP address, Bob can
conclude that it is Alice doing the search.

If Heisenburg Anonymity is followed, Bob will never know Alice's IP address from
Speakeasy, and when Alice does her search, no one will be able to associate it
to her IP address, fully protecting her privacy without limiting her ability to
use the network.

### Functional Chaff
A common technique to provide privacy (particulary to hide meta-data) is to
flood the channel with chaff. However, this is a costly solution, it requires
that a channel be filled to capacity at all times.

All messages passed through dist-ribut-us are wrapped in onion routing. Even if
a message is being sent directly, it will still look like an onion routed
message. And many messages will be onion routed so that many of the messages
enter and leaving a given node, are not actually communicating with that node.
This normal functioning of the network should provide the a significant amount
of cover to users.

One technique for thwarting mix-net obfuscation is timing attacks. With some
small modifications, users seeking extra-anonymity can time their communication
to overlap with routing other users messages. They can also volunteer to serve
and high-traffic points to give them additional cover.

### Trust Webs not Heirarchies
Trust is core to any security. Binaries are signed, data is validated. But, for
simplicity, many security systems (such as TLS) rely on heirarchies.
Dist-ribut-us will use webs of trust. When nodes in that web are compromised,
they will not threaten their neighbors because plenty of connections will
remain. And this makes it easier for those compromised nodes to come back online
with new keys. 