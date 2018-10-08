# Introduction to HPC

What is high performance computing?

The answer to this will vary from person to person and institution to institution.

Generally, high performance computing implies parallel computing.  Parallel
computing may also be subject to some interpretation.

## Parallel computing

Simplistically, a program is parallel if it can decompose a problem into
independently computable elements that can be computed at the same time.

This might be as simple as running M simulations, one per processor, at
the same time from N total.  This is often called _embarassingly parallel_
or possibly loosely coupled.

DO NOT BE EMBARASSED!  You are lucky, as this is relatively easy to
implement.  Rather, call this fortuitously parallel.

Other problems still decompose to independently computed blocks, but
the blocks must communicate with each other because what happens in
one may have an impact on what's in another.

This can be done by sharing data in memory on one machine, in which
case this is a multicore or multiprocessor application.

It can also be done on multiple machines, where the blocks update
each other over the network.  This is typically implemented using
the message passing interface (MPI).

Software must be written specially to use parallel capabilities.

# What is high throughput computing?

High throughput computing (HTC, to some) is computing where there
is a large collection of indendent tasks that can be put in line
to be run..., whenever.  The SETI project lets people run some
parts of their computation on their own computer when they are not
working.

## High * computing at UM

Here at UM, we don't have separate facilities for HPC and HTC,
they are both done on one system.

Picture

![Generic HPC system structure](https://epcced.github.io/hpc-intro/fig/hpc_system_diagram.png)

more text.

What a computer looks like

![Generic node structure](https://epcced.github.io/hpc-intro/fig/node_diagram.png)

More text.
