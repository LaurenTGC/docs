## Threat Models

### Malice
A malicious attack only has a goal of disrupting the network, or a portion of the network.
It does not provide anything to the attacker. It is not feasible to stop all malicious
attacks, but the effort to launch a malicious attack must be proportional (or less)
the the damage it does, and must be kept below a target threshold.

#### Vandalism
Similar to a malicious attack, but allows the attacker to leave a signature. This can
be as simple as claiming credit or announcing an attack. Though claiming credit is
not proof, so it is of limited value to the attacker.

### Greed
Free loading can't be stopped, but it can be limited.

### Spam
Forcing content on users that they do not want.

### Spying
Collecting data on users that the users would prefer not be collected

#### Coerced Spying
Trading access to a service or information for personal information.

#### Covert Spying
A third party collecting data that is being freely shard, but that they
are not welcome to.

### Leverage
Not a type of attack but a component of one. Leverage is the factor by which an attack
can be amplified. For instance, simply sending a message through a full route requires
that the message be forwarded 6 times, a leverage of 6x. Linear factors should be kept
low and exponential factors should be avoided.