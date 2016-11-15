## Toy Example
Let's say Alice wants to send Bob a message.

Alice uses Leapfrog to traverse the DHT looking for Bob's Speakeasy ID. If Bob
is logged in, she will find a record for him in the table. This will give her a
Leap-route to send Bob the message.

If Bob is not online, one option is that Alice can simply queue the message, and
the service will re-check occasionally. Another option is that if Alice and Bob
have any trusted mutual friends, the message can be passed through these
friends, increasing the probability that at least one message bearer will be
logged in when Bob logs in. The mutual friends will not be able to read the
message, but they will know that the communication is happening.

Though it may take quite a bit of overhead, this problem can be solved without
these tricks. Alice and Bob can exchange a token ahead of time (some previous
communication must have happened to exchange keys). Alice can label the message
with that token and give is to several of her friends. When Bob logs on, if he
does not see Alice, he can anonymously broadcast a request for the message (by
token), one of Alices friends can anonymously post it to the DHT, allowing them
to connect to Bob through Leapfrog (using a rendevoux node to protect both their
anonymity).

I do not have a specific design for the broadcast mechanism. With no
protections, it could be easily subject to DOS attacks. Users can be divided
into channels so that Bob is not broadcasting to the entire network, but only to
a few small sections that are likely to contains Alices friends. But if the
sections are too small, a malicious entity may still be able to fingerprint a
node.