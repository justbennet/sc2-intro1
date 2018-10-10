# The &lsquo;problem&rsquo; of software

Installing software onto a multiuser, multipurpose, long-lived system
introduces some inherent problems.

* Mutually incompatible software packages
* Mutually exclusive versions
* Conflicting configurations

We solve this problem by using the Lmod software package to implement
&lsquo;modules&rsquo;.

## What happens when you install software

Simple software installation is simply copying one or more files
to the system marking it or them as executable, as needed.

Most software, however, also requires that you set up your environment,
which consists usually and mostly of setting the values of variables.

The problems mentioned above occur when there are two files of the same
name that do different things, and you need to use them both.
