The batch manager will run your job, but only when told to do so.  On
the simplest cluster, the cluster manager types a command to run a job.
If there are more than a few jobs from a few people, it will get very
hard to figure out on which nodes to run new jobs, when to start them,
etc.  This is where the _scheduler_ software comes in.

<center>
![tetris](./images/tetris.jpg)

_What jobs look like to the scheduler_
</center>

Flux uses a scheduler called Moab, and it controls not only scheduling
but who has money in their piggy banks and can afford to run jobs.
