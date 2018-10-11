## Parallel computing

No matter whether your high is performance or throughput, some
degree of _parallelism_ is implied.

Simplistically, a program is parallel if it decomposes a problem into
independently computable elements and computes multiple elements at
the same time on different processors.

This might be as simple as running M simulations, one per processor, at
the same time from N total, where there is no interdependence among the
individual simulations.  This is often called _embarassingly parallel_
or possibly loosely coupled.  Results are typically aggregated in a
separate step once the independent computations are done, as in Monte
Carlo simulation.

Do not be embarrassed by this situation.  Instead, consider yourself
lucky to have a nice problem that can be dealt with using regular
programming techniques.

You may, more properly, call this fortuitously parallel.

Other problems still decompose to independently computed blocks, but
the blocks must communicate with each other before the full computation
is complete because the result of one, independent computation is
needed to update another prior to the next step.  The communication
is typically frequent, and these are called tightly coupled parallel
programs.

Consider yourself unlucky to have to write this kind of software.

This can be done by sharing data in memory on one machine, where
multiple processes or threads are updating different segments in
real time. This is called the shared-memory model, and is, I hope
obviously, limited to the capacity of one machine.

This can also be done on multiple machines, where the processes
doing the work must communicate with another machine over the
network.  That is typically done using the message passing
interface (MPI).  This type of parallel computing is called
distributed memory.

The two types can also be combined into what is typically called
a hybrid model, where multiple nodes are communicating among
themselves but on any one node, the shared memory model is in
use on multiple processors.

## Do you believe in magic?

Of course not!  You're engineers (mostly).  So,

**Parallel capabilities must be written into your software**

That can be harder or easier, and only a software engineer
would call be assigned the easier of two problems embarrassing.
