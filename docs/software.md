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

## Using Lmod

Lmod is used to configure installed software for use.  To use it, you
need to know the name of the software module you wish to use.  So,
how do you find what is installed?

### Finding software

On the current Flux system, we chose not to use the
$lsquo;hierarchical$rsquo; module feature, which is arguably its
most desirable feature. However, the clusters that will be coming
online soon and will replace Flux do, so we will cover looking
for software as it will be and not as it is.

The most general search is by _keyword_. You specify some search
term, and Lmod will look through the names of modules, descriptions,
and categories (which are hidden). So, for example, to look
for machine learning software, use the following command,
where the quotes are required to make that on term instead of two.

```
$ module keyword "machine learning"
----------------------------------------------------------------------------

The following modules match your search criteria: "machine learning"
----------------------------------------------------------------------------

  caffe: caffe/160803, caffe/170407
    Caffe is a deep learning framework made with expression, speed, and
    modularity in mind.

  opencv: opencv/2.4.13, opencv/3.1.0, opencv/3.2.0
    OpenCV (Open Source Computer Vision Library) is an open source computer
    vision and machine learning software library.

  torch: torch/160726, torch/170802
    Torch is a scientific computing framework with wide support for machine
    learning algorithms.

----------------------------------------------------------------------------

To learn more about a package execute:

   $ module spider Foo

where "Foo" is the name of a module.

To find detailed information about a particular package you
must specify the version if there is more than one version:

   $ module spider Foo/11.1

----------------------------------------------------------------------------
```

The output lists three packages (as of the time of this writing): `caffe`,
`opencv`, and `torch`.  Here is a short guide to interpreting that
output.

Taking `opencv` as an example,

```
opencv: opencv/2.4.13, opencv/3.1.0, opencv/3.2.0
```
the _module_ name is to left of the colon.  To the right are the
module-slash-versions for which modules have been prepared. At
the bottom of the output are the commands you should use to get
addtional information about the package.

The first version of the `module spider` command will list the
description of the software, the versions available, and any
other modules it considers to be near-misses. It will also
suggest you include the version number to obtain more
information about the specific version.

So, you should run these two commands,

```
$ module spider opencv
$ module spider opencv/3.2.0
```
and compare the output.

To load a module, you use `module load`, as in

```
$ module load opencv/3.2.0
Lmod has detected the following error:  Cannot load module
"opencv/3.2.0" without these module(s) loaded:
   ffmpeg/3.2.4 image-libraries/170303

While processing the following module(s):
    Module fullname  Module Filename
    ---------------  ---------------
    opencv/3.2.0     /sw/coe/centos7/modulefiles/opencv/3.2.0.lua
```
Then you figure out what went wrong.

In this case, Lmod is telling you that two other modules must be loaded
first, `ffmpeg/3.2.4` and `image-libraries/170303`.  That line should
be copy and pastable, and you can add those before the module you really
want.

```
$ module load ffmpeg/3.2.4 image-libraries/170303 opencv/3.2.0
```
and that should silently succeed.

To see what is loaded, use

```
$ module list
```

To remove one module you `module unload` it, or you can clear the deck
with

```
$ module purge
```

Do that.

You may run across some really ugly names in our current setup.  For example,
```
gromacs/5.1.2/openmpi/1.10.2/gcc/5.4.0
```
There are two things to note about that.  One is that the _module name_ is
actually `gromacs/5.1.2/openmpi/1.10.2/gcc`, and the version is `5.4.0`.
The second is that the name is compound name, where all the requirements
are embedded in it.  Read off software name/version number pairs from
right to left, so `gcc/5.4.0` was used to make `openmpi/1.10.2`, which was
used to make `gromacs/5.1.2`.
