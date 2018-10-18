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

We will now look at each, in the order they appear there.


<dl>
  <dt>-N</dt>
  <dd>The -N option specifies the job name. This will be displayed by, for example, the qstat command to see the job status.</dd>
</dl>


-A 	The -A option specifies the account to use; that is, how will the job be paid. Different types of Flux services have different suffixes. For example, a standard Flux account will end with _flux, whereas one that pays for use of the large-memory Flux service would end with _fluxm.
-q 	The -q option specifies which queue your job will be in. If the account ends in _flux, then -q must specify flux. If the account ends with some variation, say, default_fluxm, then the queue name must match, e.g., _fluxm.

-M 	The -M option specifies the e-mail address to which notice of events related to this job are sent. More than one address can be used, separated by commas (no spaces).
-m 	The -m option specifies the events for which you want notification. They are: abort, begin, and end.

-j oe 	Without the -j option, whatever the job prints to STDOUT will go in one file and whatever the job prints to STDERR will go in another.The -j option says to join the two and put everything into the job output file (not to be confused with output that your programs may write). If you specify -j eo the two will be joined and put into the
error file. Practically, these are the same except for the name of the file.
-V 	The -V option specifies that the environment at the time the job is submitted should be inherited by your job. So, you will load software modules and other system variables during your login session on the login node before you submit your job.You should always set up your environment prior to running qsub and use the -V option.
