## Nice To Have
We don't know how to solve these problems, but solutions would help the network.

### Cyclic Cryptography
See (this)[https://www.reddit.com/r/crypto/comments/40hspu/help_encryption_algorithm_with_many_keys/]
discussion.

This would consist of two parts, a key generation and a transform function. Some
number of keys is requested from the generator. The transform function takes in
data and a key and produces a transformation of that data. When all the keys
have been applied, the final transformation will be the same as the original
data.

This would be great for onion routing. It would allow nodes to add additional
steps in the middle of routing. It would decrease the overhead for the sender
and receiver. It would eliminate rendezvoux nodes (that know they are
transition between a send and receive route).

### Anonymous Credits
There are many facets to this problem. The central theme is the ability to
extend credit for actions taken with in the network; storage, computation and
networking. But it's difficult to exchange credits efficiently while maintaining
anonymity.

If we had such a system, it may help balance resources.

#### Trade Cycles
It may be possible to setup trade cycles. Say I want something (a query
answered, to download a resource) I can send out a request. Someone with the
ability to fulfill it can answer. We can establish a trade opportunity. These
trade opportunities would form a directed graph. Whenever a cycle forms in that
graph, everyone would perform the action.

There's a lot of room for problems, but it may be worth looking into.