# Introduction to HPC at UM for SC2

The purpose of this presentation is to provide a quick overview of what
HPC and HTC is, system components, and how to find software to run.  We
will use two Python scripts from a prior SC2 workshop to illustrate.

Before we proceed, you should log into the Flux cluster, on which all of
you who wish to follow along should have accounts.

Windows people should configure PuTTY to use the host

```
flux-login.arc-ts.umich.edu
```

Mac and Linux users should open a Terminal application and use

```
$ ssh flux-login.arc-ts.umich.edu
```

If you try to connect from off-campus, you will need to use the UMich
VPN client.

## What you connected to

You have now logged into the Flux cluster.  Just to make sure that
everyone is on the same page, we'll go like lightning through the
components of a typical cluster and Flux in particular.

## Nodes

We call specific physical machines _nodes_, and there are three types of
which you should be aware:  login, data transfer, and compute.  Nodes all
typically look like this.

![Generic node structure](./images/node_diagram.png)
