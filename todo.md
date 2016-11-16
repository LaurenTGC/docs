## To Do
Top level stuff to work on

### Liscense
Pick an opensource liscense.

### CI
Get a continuous integration server setup and connected to github. Run tests,
get code coverage, run lint.

### Docs
Get docs organized and get a format for breaking them down into smaller pieces.

### Website
I have the ribut.us domain, I'd like to (using the two above) get the docs to
render Markdown to HMTL and publish to that domain.

### Better coverage
The stuff that's already out there has pretty low test coverage. I'd like to get
it up around 70%.

### IPC
This is kind of a PITA. Unix sockets are great, but they don't work on Windows.
Everything could run through Pool and use stdIn/Out, but now pool ends up
relaying everything, when most things just need to talk directly to the ribut-
server.

### User Model
Just a sketch: a ribut-user is the lowest level access. You need a password to
unlock a key. That key can then be used to access all the account keys. There
will also be device level settings associated with the user. This user will
actually be associated with the Pool application.

### Local Storage
Bolt for configuration values, files for blobs. Also need to figure out how the
master key will work. Also multi-factor auth.

### Dev Resources
Build a list of resources on topics like P2P algorithms, crypto, Go and so on to
get potential devs upto speed on complex topics.

### Mobile
Start building and testing components on mobile via
https://godoc.org/golang.org/x/mobile/app

### NATT testing
Need to test NAT traversal on many devices.