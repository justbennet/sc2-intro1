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


<table>
  <tr>
    <td><code>-N</code></td>
    <td>The <code>-N</code> option specifies the job name. This will be displayed by,
    for example, the <code>qstat</code> command to see the job status.
    </td>
  </tr>

  <tr>
    <td><code>-l</code></td>
    <td>The <code>-l</code> (small 'ell') option specifies the resources the job
      needs.  By resources, we mean physical nodes, processor cores, memory, and
      the maximum time the job will run.<br>
      
      This typically looks like<br>
      
      <code>#PBS -l nodes=1:ppn=1,mem=1gb,walltime=1:00:00</code><br>
      
      or<br>
      
      <code>#PBS -l nodes=4:ppn=1,pmem=1gb,walltime=1:00:00</code><br>
      
      Nodes are physical machines; <code>ppn</code> means _processors per node_.
      When requesting memory for one node, use <code>mem</code>; when requesting
      more than one node, use instead <code>pmem</code> for _processor memory_.
      The total memory requested in the first case is 1gb; in the second it is
      4gb; if you request <code>nodes=1:ppn=4,mem=1gb</code>, there is 1gb total
      that can be used by all four of the processors combined.
    </td>
  </tr>

  <tr>
    <td><code>-A</code></td>
    <td>The <code>-A</code> option specifies the account to use; that is, how will the
      job be paid for. Different types of Flux services have different suffixes.
      For example, a standard Flux account will end with <code>_flux</code>, whereas one
      that pays for use of the large-memory Flux service would end with
      <code>_fluxm</code>.
  </td>
  </tr>

  <tr>
    <td><code>-q</code></td>
    <td>The <code>-q</code> option specifies which queue your job will be in. If the account
      ends in <code>_flux</code>, then <code>-q</code> must specify flux. If the account ends with some
      variation, say, <code>default_fluxm</code>, then the queue name must match,
      e.g., <code>fluxm</code>.
  </td>
  </tr>


  <tr>
    <td><code>-M</code></td>
    <td>The <code>-M</code> option specifies the e-mail address to which notice of events
      related to this job are sent. More than one address can be used, separated
      by commas (no spaces).
  </td>
  </tr>

  <tr>
    <td><code>-m</code></td>
    <td>The <code>-m</code> option specifies the events for which you want notification.
      They are: abort (<code>a</code>), begin (<code>b</code>), and end (<code>e</code>).  You can also specify
      none (<code>n</code>).
  </td>
  </tr>


  <tr>
    <td><code>-j</code></td>
    <td>Without the <code>-j</code> option, whatever the job prints to <code>STDOUT</code>
      will go in one file and whatever the job prints to <code>STDERR</code> will go in
      another. Most commonly, you will want to join the errors to the output with <code>oe</code>.
      The <code>-j</code> option says to join the two and put everything into the job
      output file (not to be confused with output that your programs may write).
      If you specify <code>-j eo</code> the two will be joined and put into the
      error file. Practically, these are the same except for the name of the
      file.
  </td>
  </tr>

  <tr>
    <td><code>-V</code></td>
    <td>The <code>-V</code> option specifies that the environment at the time the job is
      submitted should be inherited by your job. So, you will load software
      modules and other system variables during your login session on the
      login node before you submit your job.You should always set up your
      environment prior to running qsub and use the <code>-V</code> option.
  </td>
  </tr>
</table>

When you have completed your PBS script by filling in all the options appropriate for
your job, and adding a command at the bottom to actually run, you are ready to submit it.

You do this with

```
$ qsub template.pbs
```

Once submitted, you can see its status by using the `qstat` command.  See the
[example qstat output](http://cscar.research.umich.edu/wp-content/uploads/sites/5/2016/04/hpc101_qstat.pdf) for
what it looks like when your job is 1) in the queue (waiting to start), 2) running,
and 3) once it completes, either successfully or not.
