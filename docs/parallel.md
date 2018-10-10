## Parallel computing

Simplistically, a program is parallel if it decomposes a problem into
independently computable elements and computes multiple elements at
the same time on different processors.

This might be as simple as running M simulations, one per processor, at
the same time from N total.  This is often called _embarassingly parallel_
or possibly loosely coupled.

DO NOT BE EMBARASSED!  You are lucky, as this is relatively easy to
implement.  Rather, call this fortuitously parallel.

Other problems still decompose to independently computed blocks, but
the blocks must communicate with each other before the full computation
is complete because the result of one, independent computation is
needed to update another prior to the next step.

This can be done by sharing data in memory on one machine, in which
case this is a multicore or multiprocessor application.

It can also be done on multiple machines, where the blocks update
each other over the network.  This is typically implemented using
the message passing interface (MPI).

Software must be written specially to use parallel capabilities.
