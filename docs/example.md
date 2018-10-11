# Am example

## Workflows and pipelines

Quite a lot of scientific computing takes multiple steps with multiple
packages.  Depending on your field, what part of the country you are
from, and idiosyncratic distaste for some noun forms, you might call
the collection of all the steps a _workflow_ or a pipeline (or something
you shouldn't say in front of small children).

I think that creating a pipeline is much like writing software.  Because
it is writing software. I construct them incrementally.

1. Find, install, and/or configure the needed software.
1. Make a subset of data so that test can be run quickly, or reduce.
   the number of iterations or the mesh size accordingly.
1. Figure out how to run your program interactively.
1. Figure out how to create a batch script for your task.
1. Test the batch script interactively.
1. Convert that to a script to be submitted to the system
1. Run the short version.
1. Adjust for real data, mesh size, and/or iterations.
1. Submit real task to cluster.
1. Get rich and famous.

We will go through steps 1&ndash5 today and return to steps 5&ndash;9
next week.  Step 10?  You&rsquo;re on your own.

## The examples

The SC2 had a workshop on machine learning.  We have modified versions
of two of the scripts from that.

Please create a `github` directory under your home directory, then clone
the previous workshop repository there.  Change to the repo directory,
then copy our slightly modified versions of

```
$ mkdir github
$ cd github
$ git clone https://github.com/UM-SC2/MLworkshopF17
```

We will use the two Python scripts, `digitDetectionKey.py` `spamFilterKey.py`
as test examples.

First we check to see if our software is there.

```
$ python --version
```

Oh, drat!  Version 2, and we want 3.  How do we find software? I heard
that Anaconda Python distribution has lots of libraries included....

```
$ module keyword anaconda
```

Well, `python-anaconda3` looks promising, but what are all the versions?

```
$ module spider python-anaconda3
. . . .
     Versions:
        python-anaconda3/latest
        python-anaconda3/latest-3.6
        python-anaconda3/201607
        python-anaconda3/201704
```

My advice if you care about getting the same results twice?  Use a
dated version. If you're just playing around, use `latest`. The
dated version is the default, which `module available
python-anaconda3` will show you.

```
$ module load python-anaconda3
```

We should make sure that we do _not_ start this on a huge data set!
Edit `digitDetectionKey.py` and make sure that `dataset_size = 1000`
and not some larger number, like 70000.

Now we have the correct version of Python, and we have a scaled
down dataset we can commence testing.

```
$ python digitDetectionKey.py
Coefficients: 
 [[ 0.  0.  0. ...,  0.  0.  0.]
 [ 0.  0.  0. ...,  0.  0.  0.]
 [ 0.  0.  0. ...,  0.  0.  0.]
 ..., 
 [ 0.  0.  0. ...,  0.  0.  0.]
 [ 0.  0.  0. ...,  0.  0.  0.]
 [ 0.  0.  0. ...,  0.  0.  0.]]
Non-zero Coefficients 
 (array([0, 0, 0, ..., 9, 9, 9]), array([ 36,  37,  38, ..., 768, 769, 770]))
Fraction correct: 
 0.865
```

We need to put that into a script that we could submit to the batch
system.  So, create a file called `digitDetect.sh` and put the Python
command into it.

```
$ cat digitDetect.sh 
#!/bin/bash

python digitDetectionKey.py
```

Now try to run it with `bash digitDetect.sh`.  Ah, ha.  Fix it so
that it saves its output to a file.

Now run it again.

We have completed steps 1&ndash;5.
