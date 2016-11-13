## The Anonymous Request Problem

There is a resource, R, that Alice wants. For simplicity, assume a static
resource. Bob has that resource. How can Alice request the resource in such a
way that Bob can fulfill the request and both of them stay anonymous. Also
consider Eve, the system must be arranged in such a way that Eve cannot
reasonably infer that Bob has the resource, even with many requests. And she
cannot infer that Alice is the requester.

### Indexing Bob could anonymously publish to a DHT that he has R. Alice could
aquire R by looking it up in the DHT.

Let's start by looking at DHT limitations. A DHT record will have a size limit
and a lifespan. As these increase, the functionality of the DHT increases, but
it's reliability decreases. If the size is too large or the lifespan too long,
the records become burdonsome to the node.

Even if Bob puts a route in the DHT, as nodes leave, that route becomes less
reliable. He could potentially use long-lived nodes for this. But then there's
still the problem that Bob will eventually log off. So we balance that the
longer the records live, the less reliable they are. Eventually, we may be able
to find an optimal model by looking at the average amount of time that a node
stays live.

At the other end, Bob may have 10's of thousands of resources. When he logs on,
the act of publishing them all would be substantial, as would keeping them
refreshed. And that's where indexing really falls down. It could be potentially
useful for a few key files that are likely to be requested, but not so useful
for the entire catalog.

There's also a "fingerprinting" issue. Lets suppose a system where Bob logs on
and adds all of his files to an index, but the index only shows anonymous
routes. If that system were near real-time, just the coincidence of Bob's
overlay node appear and the files in the index appear could be used to link Bob
to the files.

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
There is currently no satisfactory answer.

The least-bad option is to have a channels mechanism built on top of the DHT.
Each overlay node will forward a request to all of it's DHT neighbors once a
second. Requests will be tracked so that a node doesn't re-forward a request
indefinitely.

Now Alice can anonymously send a request to a random DHT node. That node will
forward the request and it will rapidly propigate through the network.
Eventually, it should hit most of the nodes.

Hopefully, someone smarter than me will find a better solution to this problem.