# Batch processing

As we said in the previous workshop, there are two components to running jobs
on the cluster.  Let us look at them more closely now.

## Batch manager

On the Flux cluster, the software that starts, stops, and monitors the jobs
is called Torque, and it provides the portable batch system (PBS).  When you
want to run a job on the cluster, you prepare a _submission script_ also
commonly referred to as a _PBS script_.

This is just a shell script that contains directives at the top that define
the characteristics of the job you would like to submit.  The directives to
PBS appear one per line, and the line begins with `#PBS` followed by the
directive and its value(s).  The PBS script is submitted using the `qsub`
command, and all the directives are avaialable as options to that command.

Here is a blank template you can use that contains the most commonly used
`#PBS` directives:  [PBS template](./pbs_template.html)




There are two 
