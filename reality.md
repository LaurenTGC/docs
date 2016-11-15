## Reality vs Design

The reality of Ribut.us should actually be much less hostile than the design.
There are many factors that I believe will be present in the real version that
should help aleiviate some of the more challanging issues. But it should be
designed assuming only the strictest axioms.

### Long-Lived Nodes
Users can track long-lived overlay nodes. Building a route from long-lived nodes
makes it more likely that it will last longer. This means that in reality,
dependable routes can built when necessary. And I believe that some users will
voulantarily provide reliable nodes. But for the design, we should assume short
lived routes whose dependability decays rapidly.

### File Cache
Another useful mechanism is a file cache. Users can provide medium-lived
storage, on the order of 24 hours. For things like email, this is a great way
to get around the anonymous-request problem. But these may not be relied upon.

### Trust Groups
Users can form trusted groups. These groups can have different characteristics
that trade security for convenience. But if the group is truely trustworhty,
there should be no real loss of security.

#### Open Meta-Data
Some types of meta-data can be revield with in a trust group. Alice can send a
message to Bob by giving it Carol. Alice doesn't mind if Carol knows she is
talking to Bob

#### Caching
Users can cache files for eachother with in trust groups.

### Persistant Nodes
Users can run nodes that will collect any data intended for them. If Alice wants
to send Bob a message, she can always send it to his Persistant Node.