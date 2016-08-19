# This one is an interesting project about multicast

We will consider two kind of multicasting here: casual ordering
and total ordering.

Scenario describes multiple users talking with each others.
First type of communication is casual ordering. When user A
wants to say something, he will broadcast his messages to
B, C, D. Suppose network is unreliable (using probability to
drop the packet), however, it still manages to send the message
to (at least) one of users. When user receive a message, it will also
multicast that messages to other people. The problem is that it has
to preserve the property:

If A multicast m1, then m2 to B, C, D. Somehow, C does not receive
m1; However, m2 comes to C queue. Then B send m1 to C. It has to respect
the casual ordering m1 -> m2. So m1 has to be delivered before m2.
The implemention uses vector clock.

Another scenario is that one of users randomly generate a message, he
then will multicast that message to the group and to sequencer. For whatever
message comes first to the sequencer, it will make all of user receives the
same order of message.

## Tool
- Python (Threading, Mutex)
- Rabbit MQ
