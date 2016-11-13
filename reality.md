## Reality vs Design

The reality of Ribut.us should actually be much less hostile than the design.
There are many factors that I believe will be present in the real version that
should help aleiviate some of the more challanging issues. But it should be
designed assuming only the strictest axioms.

For instance, users can track long-lived overlay nodes. Building a route from
long-lived nodes makes it more likely that it will last longer. This means that
in reality, dependable routes can built when necessary. And I believe that some
users will voulantarily provide reliable nodes. But for the design, we should
assume short lived routes whose dependability decays rapidly.

### File Cache
Another useful mechanism is a file cache. Users can provide medium-lived
storage, on the order of 24 hours. For things like email, this is a great way
to get around the anonymous-request problem. But these may not be relied upon.