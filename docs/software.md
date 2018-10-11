# Software provided on the cluster

## The problem of multiple everything

Installing software onto a multiuser, multipurpose, long-lived system
introduces some inherent problems.

* Mutually incompatible software packages
* Mutually exclusive versions
* Conflicting configurations

## What happens when you install software

Simple software installation is simply copying one or more files
to the system marking it or them as executable, as needed.

Most software, however, also requires that you set up your environment,
which consists usually and mostly of setting the values of variables.

The problems mentioned above occur when there are two files of the same
name that do different things, and you need to use them both.  That
can happen when different versions of the same software is installed
or when a supporting library of the same name but different version
is included by two software packages.

## How to solve that

You can solve that manually by installing the necessary files, then
creating setup scripts to source for each. That is clunky and
inconvenient.  So, some clever people came up with the `module`
command &ndash; there are two versions of it, too, and we use
the Lmod version &ndash; which manipulates your environment
without you having to manage subshells or maintain separate login
shells, etc.

## Software modules

We solve this problem by using the Lmod software package to implement
&lsquo;modules&rsquo;.  To understand what modules are and why they
are useful, we should review what installing software means.

