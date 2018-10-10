# Using Flux

## Logging in

To use Flux, you must log into it.

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

You have now logged into the Flux cluster.  Just to make sure that
everyone is on the same page, we'll go like lightning through the
components of a typical cluster and Flux in particular.

## Where you should put things

Everyone has a home directory under `/home/uniqname`.  There is an
80 GB quota.

When you are added to a paid account, you will also get a directory
under it; for example, `/scratch/engin_flux/uniqname` if you are added
to the `engin_flux` account.

## Finding what has been installed on Flux

We will start with the most general search for software that has been
installed and has had a software module created for it.
