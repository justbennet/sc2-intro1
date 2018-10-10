# Cluster computing at the University of Michigan

## High performance computing

High Performance Computing most generally refers to the practice of
aggregating computing power in a way that delivers much higher performance
than one could get out of a typical desktop computer or workstation in
order to solve large problems in science, engineering, or business.

https://insidehpc.com/hpc-basic-training/what-is-hpc/

High-performance computing (HPC) is the use of parallel processing for
running advanced application programs efficiently, reliably and quickly.
The term applies especially to systems that function above a teraflop or
10^12 floating-point operations per second.

https://searchdatacenter.techtarget.com/definition/high-performance-computing-HPC

High-performance computing (HPC) is the use of super computers and parallel
processing techniques for solving complex computational problems. HPC
technology focuses on developing parallel processing algorithms and systems
by incorporating both administration and parallel computational techniques.

https://www.techopedia.com/definition/4595/high-performance-computing-hpc

## High throughput computing

High-throughput computing (HTC) is a computer science term to describe the
use of many computing resources over long periods of time to accomplish a
computational task.

As an alternative definition, the European Grid Infrastructure defines HTC
as “a computing paradigm that focuses on the efficient execution of a large
number of loosely-coupled tasks”,[2] while HPC systems tend to focus on
tightly coupled parallel jobs, and as such they must execute within a
particular site with low-latency interconnects. Conversely, HTC systems
are independent, sequential jobs that can be individually scheduled on
many different computing resources across multiple administrative
boundaries.

https://en.wikipedia.org/wiki/High-throughput_computing


It is not uncommon to find problems that require weeks or months of
computation to solve. Scientists and engineers engaged in this sort of
work need a computing environment that delivers large amounts of
computational power over a long period of time. Such an environment
is called a High-Throughput Computing (HTC) environment.

https://research.cs.wisc.edu/htcondor/manual/current/1_1High_Throughput_Computin.html

In contrast to HPC, high throughput computing does not aim to optimize
a single application but several users and applications. In this way,
many applications share a computing infrastructure at the same time
&ndash; in this way the overall throughput of several applications is
supposed to be maximized.

https://www.igi-global.com/chapter/high-throughput-data-analysis-proteomic/35696

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
