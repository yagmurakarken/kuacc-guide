# scontrol

This command also shows everything about a job. You can find job id by squeue and kuacc-queue commands.

`scontrol show jobid  job_id`

Note:You can access these information in more detail with kuacc-queue .

```
[root@login03 ~]# scontrol show jobid 2535745
JobId=2535745 JobName=JupiterNotebook
   UserId=xxxxx GroupId=domainusers(200513) MCS_label=N/A
   Priority=1669 Nice=0 Account=ai QOS=ai
   JobState=RUNNING Reason=None Dependency=(null)
   Requeue=1 Restarts=0 BatchFlag=1 Reboot=0 ExitCode=0:0
   RunTime=06:03:50 TimeLimit=5-00:00:00 TimeMin=N/A
   SubmitTime=2021-10-26T11:34:35 EligibleTime=2021-10-26T11:34:35
   StartTime=2021-10-26T11:34:40 EndTime=2021-10-31T11:34:40 Deadline=N/A
   PreemptTime=None SuspendTime=None SecsPreSuspend=0
   Partition=ai AllocNode:Sid=login02:19426
   ReqNodeList=(null) ExcNodeList=(null)
   NodeList=dy02
   BatchHost=dy02
   NumNodes=1 NumCPUs=2 NumTasks=2 CPUs/Task=1 ReqB:S:C:T=0:0:*:*
   TRES=cpu=2,mem=8G,node=1,gres/gpu:tesla_k80=1
   Socks/Node=* NtasksPerN:B:S:C=2:0:*:* CoreSpec=*
   MinCPUsNode=2 MinMemoryCPU=4G MinTmpDiskNode=0
   Features=(null) DelayBoot=00:00:00
   Gres=gpu:tesla_k80:1 Reservation=(null)
   OverSubscribe=OK Contiguous=0 Licenses=(null) Network=(null)
   Command=/scratch/users/xxxxx/myjupyter/jupyter_submit.sh
   WorkDir=/scratch/users/xxxxx
   StdErr=/scratch/users/xxxxxjupyter-%J.log
   StdIn=/dev/null
   StdOut=/scratch/users/xxxxx/jupyter-%J.log
   Power=
   ```

   Command output shows all details about job. Parameters can be checked in https://slurm.schedmd.com/scontrol.html