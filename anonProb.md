## The Anonymous Request Problem

Alice wants a resource (we'll assume a static resource), and Bob has that resource. How can both Alice and Bob stay anonymous while requesting, and sending, resources?

Also consider Eve, the system must be arranged in such a way that Eve cannot
reasonably infer that Bob has the resource, even with many requests. And she
cannot infer that Alice is the requester. // LC: what the what?

### Indexing
There are theoretically other methods of indexing Distributus could use, but we have focused on DHT. Bob would anonymously publish to a DHT that he has R (the static resource), then Alice would look up and then aquire R through the DHT.

####DHT Limitations

A DHT record has a size limit, and a lifespan. Increasing either will increase functionality of the DHT, but decrease reliability. If the size is too large or the lifespan too long,
the records are burdonsome to the node.
* __Size Limit:__ It could be useful to index key files that are most likely to be requested, but it is not useful to index the entire catalog if Bob has tens of thousands of resources. When Bob logs on, publishing and refreshing all resources would be substantial in this case.
* __Lifespan:__ Resources are considered less reliable as nodes leave the system, or when Bob logs off. Bob could potentially use a long-lived node to reduce the issue, but it's worth looking for an model based on the average time a node stays live. // LC: moar plz
  
"Fingerprinting" is also an issue if Bob logs on and adds all of his files in nearly real time. Eve could link the coincidence of Bob's overlay node and the index files to identify Bob.

### Request Publishing
Alice can anonymously publish the request. Anyone that can fulfill the request
can register a short-lived record with the DHT.

This requires some sort of propigation mechanism. If the request is for a rare
resource and it's propigated randomly, it will have to be propigated to large
percent of the network to have a good chance of getting a response. This
leaves a lot of network leverage for malicious attacks.

On the other hand, channels could be created by a number of means. Each channel
would have some semi-predictible probability of responding to a request. Now
Alice could only send the request to a few channels. But if the channel
populations are too small, Eve could deduce who has what resources.

So sending a request requires that many nodes see it, probably at least 500. And
there can be very limited control over how the request is passed along. This
still leaves a leverage factor of 500, which tempts malice.

This could be mitigated by grouping requests and passing them along at a steady
rate (1/s).

And there's the question of if nodes join a channel anonymously. If channels
have any "grouping" factor, anonymity would be preferable. But maintaining those
connections would require a lot of overhead bandwidth.

### Conclusion
There isn't a satisfactory answer yet.

The least-bad option is to have a channels mechanism built on top of the DHT.
Each overlay node will forward a request to all of it's DHT neighbors once a
second. Requests will be tracked so that a node doesn't re-forward a request
indefinitely.

Now Alice can anonymously send a request to a random DHT node. That node will
forward the request and it will rapidly propigate through the network.
Eventually, it should hit most of the nodes.

We hope a few brilliant people will help find a better solution.
