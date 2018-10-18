# A PBS script template

```
#!/bin/bash            
####  PBS preamble
#PBS -N 

#PBS -M 
#PBS -m ea
#PBS -j oe

#PBS -A 
#PBS -q 

#PBS -l 
#PBS -V

####  End PBS preamble

# You may wish to note in comments here whether any software modules
# should be loaded prior to submitting this script, as a reminder to
# yourself and anyone else who may inherit this script.

if [ -s "$PBS_NODEFILE" ] ; then
    echo "Running on"
    uniq -c $PBS_NODEFILE
fi

if [ -d "$PBS_O_WORKDIR" ] ; then
    cd $PBS_O_WORKDIR
    echo "Running from $PBS_O_WORKDIR"
fi

# Put commands to run during the batch job below this line
```
