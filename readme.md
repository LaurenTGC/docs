## Ribut
The Ribut framework will be a set of protocols and services for building distributed applicaitons.

### Why
I started with the (hardly unique) goal of building a social networking platform that would not sell private information to advertisers and engage in aggressive advertising practices. This is a concern to me because I am already unhappy with the state of the industry and the trajectory indicates that it will only get worse.

This simple proposal when explored thoroughly produces some unexpected conclusions.

First; to protect privacy, this has to be the dominant social media platform. If a user has one profile with the proposed social network and one with a traditional network and use them evenly, the traditional network would still gather enough data on the user to undermine their privacy.

It seems almost unthinkable after nearly 2 decades of the status quo, but relationships should have the option to remain private. If someone is a friend in one context, that does not mean
they should be able to see all your friends in any context.

To avoid aggressive advertising, we will have to avoid advertising all together. 

To be a dominant social media platform, the service must be easy to use and it must scale.

The service must be p2p. This makes it possible to scale to any number of users without needing an infrastructure to support it. The peer nodes form the infrastructure.

If the service is p2p, securing the privacy of the content is trivial. But we must also secure the meta-data. Part of the high value of social networks is that advertising can be most effective by leveraging information from a social graph. Even if the content is hidden, if the network can observe who is talking to who, it could still construct a social graph and mine that data. This can be prevented with an onion routing protocol.

At this point, we can start to see the peer layer taking shape. We'll need a UDP protocol with tools for NAT traversal, a distributed hash table, an onion routing protocol. On their own, these are significant projects. Ribut is this collection, a foundation for building distributed, decentralized, secure p2p applications.

### Structure
This is the proposed architecture, but it is very much in flux

#### P2P
Direct communication between overlay nodes. Used by leapfrom to pass onion
messages or (when absolutely safe) for data that does not need the meta-data to
be private.

#### Leapfrog
The communication layer. This encompasses onion routing and NAT traversal.

#### Pond
Pond coordinates local services, applications and resources. As an extension of this, Pond also manages installation and upgrades.

#### Ributation
Uses the Eigentrust algorithm to estimate trust in information.

#### Storage
Protocol for storing data. Provides a common interface to store information in a secure manor. Data is always encrypted and can be replicated. One particularly interesting possiblitity to use the many services that offer free accounts for limited storage to save shards.

#### DHT
The protocol for communicating with the distributed hash table. The hash table is used to locate nodes and resources.

#### Speakeasy
The social media application

### Toy Example
Let's say Alice wants to send Bob a message.

Alice uses Leapfrog to traverse the DHT looking for Bob's Speakeasy ID. If Bob is logged in, she will find a record for him in the table. This will give her a Leap-route to send Bob the message.

If Bob is not online, one option is that Alice can simply queue the message, and the service will re-check occasionally. Another option is that if Alice and Bob have any trusted mutual friends, the message can be passed through these friends, increasing the probability that at least one message bearer will be logged in when Bob logs in. The mutual friends will not be able to read the message, but they will know that the communication is happening.

Though it may take quite a bit of overhead, this problem can be solved without these tricks. Alice and Bob can exchange a token ahead of time (some previous communication must have happened to exchange keys). Alice can label the message with that token and give is to several of her friends. When Bob logs on, if he does not see Alice, he can anonymously broadcast a request for the message (by token), one of Alices friends can anonymously post it to the DHT, allowing them to connect to Bob through Leapfrog (using a rendevoux node to protect both their anonymity).

I do not have a specific design for the broadcast mechanism. With no protections, it could be easily subject to DOS attacks. Users can be divided into channels so that Bob is not broadcasting to the entire network, but only to a few small sections that are likely to contains Alices friends. But if the sections are too small, a malicious entity may still be able to fingerprint a node.

### Heisenburn Anonymity
A user may have several active nodes when logged into Ribut. They will probably have one node for each application as well as one node for networking.

Apps must follow the Heisenburg Anonymity Rule - the network can know who a node is or where a node is, never both.

Without this rule, the problem goes like this. Alice is connected to Speakeasy and talks to Bob, which reveals a unique IP:Port address. Later Alice uses a different application to search for a medical term. Since the services are all p2p, her search goes out to many users. This wouldn't be problem, because none of the nodes seeing the search should know that it's Alice doing the search. But if Bob sees the search and the search also shows the IP address, Bob can conclude that it is Alice doing the search.

### Pool
Pool will let users install Ribut software. This will have a familiar feel, superficially represent the experience in any one of the walled-garden software stores. A user will see a list of applications that they can install, and simply by selecting one, the relevant details will be shown along with the option to install it. If the users chooses to install, the software will be installed and configured.

Under the hood, the process is very different. Applications and services are submitted for community review. They must be submitted as source code, not as a compiled application. Any community member that wishes to can review the software, the focus here is that the software is secure and does not violate a users privacy. The reviews are not descriptions, but simply tags.

When a source repo is determined to be sufficiently secure and functional, many users can compile it and see that they produce the same checksum. This checksum is signed and published, along with a reference to the repo and version it was compiled from.

When a user opens Pool to install software, Pool uses Eigentrust to check all published binaries. Those that have sufficient trust will be displayed. This protects users, even if they are not technically skilled, they can trust that any software installed this way is safe and secure.

### Long Lived Nodes
Nodes that either have been up for a long period of time or publish some guarentee to be up
for a longer period of time. This is a seoncdary feature, it's not required for the Ribut
to work, but a few volunteers to do this would really help smooth out the networks behavior.

The risk is if LLNs start making demands for their use. This is not acceptible and should be
made clear as part of the social contract.