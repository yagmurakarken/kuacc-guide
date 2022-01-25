# squeue § kuacc-queue

After submitting jobs, user needs to monitor jobs to check resource usage.
**squeue:** views information about jobs located in the Slurm scheduling queue.<br>
`squeue –u username`<br>

**kuacc-queue:** Shows Jobs details on queue. It ıs detailed version of squeue command.<br>
`kuacc-queue|grep username`<br>
or<br>
`kuacc-queue|more`<br>

```
(base) [yakarken18@login02 ~]$ kuacc-queue
JOBID    PARTITION  NAME             USER            TIME_LEFT    TIME_LIMIT   START_TIME           ST  NODES  CPUS  NODELIST(REASON)
2579092  short      run_custom.sh    bbiner21        59:29        1:00:00      2021-12-07T12:43:32  CA  1      1     it01
2579094  short      run_custom.sh    bbiner21        1:00:00      1:00:00      2021-12-07T12:45:32  CD  1      1     it01
2579090  mid        bash             igenel19        23:59:36     1-00:00:00   2021-12-07T12:41:29  CD  1      2     buyukliman
2579034  long       Il-gas           phaslak         6-22:57:38   7-00:00:00   2021-12-07T11:44:06  CD  1      4     rk01
2577763  cosmos     test             hakdemir        4-22:26:02   5-00:00:00   2021-12-07T11:10:06  CD  1      1     ke01
2577644  cosmos     test             hakdemir        4-17:55:23   5-00:00:00   2021-12-07T06:39:24  CD  1      1     ke03
2577553  cosmos     test             hakdemir        4-09:57:50   5-00:00:00   2021-12-06T22:39:30  CD  1      1     ke04
2577892  cosmos     test             hakdemir        4-05:11:55   5-00:00:00   2021-12-06T17:57:04  CD  1      1     ke08
2576427  mid        hph_D119V        sefenti19       23:59:00     23:59:00     2021-12-15T05:43:42  PD  1      8     (Resources)
2576424  mid        hph_G120V        sefenti19       23:59:00     23:59:00     2021-12-10T13:42:41  PD  1      8     (ReqNodeNotAvail, UnavailableNodes:)
2577787  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Resources)
2577788  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577789  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577790  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577791  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577792  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577793  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577794  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577795  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577796  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577797  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577798  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577799  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577800  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577801  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577802  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577803  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577804  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577805  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577806  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577807  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577808  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577809  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577810  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577811  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577812  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577813  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577814  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577815  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577816  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577817  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577818  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577819  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577820  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577821  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577822  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577823  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577824  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577825  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
2577826  cosmos     test             hakdemir        5-00:00:00   5-00:00:00   2021-12-10T11:08:13  PD  1      1     (Priority)
```

Command output lists information about jobs.

## JOBID, PARTITION, NAME, USER, TIME_LEFT, TIME_LIMIT, START_TIME, ST, NODES, CPUS, NODELIST(REASON)
### ST:STATE

|State|	Code|	Meaning|
| ------| ------------ | ----- |
|PENDING|	PD|	Job is awaiting resource allocation.|
|RUNNING|	R|	Job currently has an allocation.|
|SUSPENDED|	S|	Job has an allocation, but execution has been suspended.|
|COMPLETING|	CG|	Job is in the process of completing. Some processes on some nodes may still be active.|
|COMPLETED|	CD|	Job has terminated all processes on all nodes.|
|CONFIGURING|	CF|	 Job has been allocated resources, but are waiting for them to become ready for use|
|CANCELED|	CA|	Job was explicitly cancelled by the user or system administrator.
The job may or may not have been initiated.|
|FAILED|	F|	Job terminated with non-zero exit code or other failure condition.|
|TIMEOUT|	TO|	Job terminated upon reaching its time limit.|
|PREEMPTED|	PR|	Job has been suspended by an higher priority job on the same ressource.|
|NODE_FAIL|	NF|	Job terminated due to failure of one or more allocated nodes.|

Note: Preempted state means that your job is killed and re-queued because of priority. Research groups donate compute nodes and they have priority on the nodes. If they submit a job and there is no resource on the node, jobs belonging to general user are killed and requeued. To avoid this, you may use IT nodes. IT (it01-it04) doesn’t have priority. Also, you can exclude nodes by exclude parameter in slurm.


###  NODELIST(REASON) 
This column lists nodes running jobs. Also, it gives the reason for Jobs state.

|Reason|	Meaning|
| ------| ------------ |
|InvalidQOS|	The job’s QOS is invalid.|
|Priority|	One or more higher priority jobs is in queue for running. Your job will eventually run.|
|Resources|	The job is waiting for resources to become available and will eventually run.|
|PartitionNodeLimit|	The number of nodes required by this job is outside of it’s partitions current limits. Can also indicate that required nodes are DOWN or DRAINED.|
|PartitionTimeLimit|	The job’s time limit exceeds it’s partition’s current time limit.|
|QOSJobLimit|	The job’s QOS has reached its maximum job count.|
|QOSResourceLimit|	The job’s QOS has reached some resource limit.|
|QOSTimeLimit|	The job’s QOS has reached its time limit.|
|QOSMaxCpuPerUserLimit|	Maximum number of cpus per user for your job’s QoS have been met; job will run eventually.|
|QOSGrpMaxJobsLimit|	Maximum number of jobs for your job’s QoS have been met; job will run eventually.|
|QOSGrpCpuLimit|	All CPUs assigned to your job’s specified QoS are in use; job will run eventually.|
|QOSGrpNodeLimit|	All nodes assigned to your job’s specified QoS are in use; job will run eventually.|
 
Check all Reasons codes in [following link](https://slurm.schedmd.com/squeue.html#lbAF).<br>
Note: Most often you encounter with Priority, Resources and QOSMaxCpuPerUserLimit.
