# Batch Jobs

Jobs are not run directly from the command line, the user needs to create a job script which specifies both resources, libraries and the job’s application that is to be run.
The script is submitted to SLURM (queueing system). If the requested resources are available on the system, the job will run. If not, it will be placed in a queue until such time as the resources do become available.
Users need to understand how to use the queueing system, how to create the job script, as well as need to check its progress or delete a job from the queueing system.
Before submitting a job script, be sure that you are using resources within limits. Check the [limitations for KUIS AI users](https://github.com/yagmurakarken/kuacc-guide/blob/master/What%20are%20the%20limitations%20for%20Users%20from%20KUIS%20AI%20Center%3F.md).

## Job Scripts:

You can find job scripts inside /kuacc/jobscripts folder. You need to copy one of these scripts into your home directory(/kuacc/users/username/) and modify it according to your needs.

This is an example job script for KUACC HPC cluster. Note that a jobscript should start with #!/bin/bash.

```
#!/bin/bash
#SBATCH --job-name=Test            
#SBATCH --nodes=1        
#SBATCH --ntasks-per-node=1    
#SBATCH --partition=short        
#SBATCH --qos=users        
#SBATCH --account=users    
#SBATCH --gres=gpu:tesla_t4:1    
#SBATCH --time=1:0:0        
#SBATCH --output=test-%j.out    
#SBATCH --mail-type=ALL
#SBATCH --mail-user=foo@bar.com     
module load python/3.6.1
moddule load cuda/11.4
module load 8.2.2/cuda-11.4     
python code.py
```

Jobscript can be divided into three sections:
- Requesting resources 
- Loading library and application modules 
- Running your codes

### Requesting Resource:

This section is where resources are requested and slurm parameters are configured. “#SBATCH” should always be used at the beginning of lines. Also, a flag is used for each request.

```
#SBATCH <flag>
#SBATCH --job-name=Test                                 #Setting a job name
#SBATCH --nodes=1                                       #Asking for only one node
#SBATCH --ntasks-per-node=1                             #Asking one core on each node, one core
#SBATCH --partition=short                               #Running on short queue(max 2hours)
#SBATCH --qos=users                                     #Running on users qos (rules and limits)
#SBATCH --account=users                                 #Running on users partitions(group of nodes)
#SBATCH --gres=gpu:tesla_t4:1                           #Asking a tesla_t4 GPU
#SBATCH --time=1:0:0                                    #Reserving for one hour time limit.
#SBATCH --output=test-%j.out                            #Setting a output file name.
#SBATCH --mail-type=ALL                                 #All types all emails (BEGIN, END, FAIL, ALL)
#SBATCH --mail-user=foo@bar.com                         #Where to send emails
```

Note that line can be omitted/commented by adding second # at the beginning. Same way, you can add comments by starting #.

Note that, KUACC HPC partitions are listed as below. You can see active partitions by **sinfo** command.


|Name	| MaxTimeLimit | Nodes | MaxJobs | MaxSubmitJob |
| ------| ------------ | ----- | -------- | ----------- |
|short	|2 hours|	50 nodes|	50|	300|
|mid	|1 days	|45 nodes|	35|	200|
|long	|7 days|	5 nodes	|25|	100|
|longer	|30 days|	3 nodes|	5|	50|
|ai	|7 days|	16 nodes|	8|	100|
|ilac	|Infinite|	12 nodes|	Infinite|	Infinite|
|cosmos	|Infinite|	8 nodes|	Infinite|	Infinite|
|biyofiz |	Infinite|	4 nodes	| Infinite|	Infinite|
|cosbi	|Infinite|	1 node|	Infinite|	Infinite|
|kutem	|Infinite|	1 node|	Infinite|	Infinite|
|iui	|Infinite|	1 node|	Infinite|	Infinite|
|hamsi	|Infinite|	1 node|	Infinite|	Infinite|
|lufer	|Infinite|	1 node|	Infinite|	Infinite|


Note that, following flags can be used in your job scripts.

|Resource|	Flag Syntax|	Description|	Notes|
| ------| ------------ | ----- | -------- | 
|partition|	--partition=short|	Partition is a queue for jobs.|	default on kuacc is short|
|qos|	--qos=users	|QOS is quality of service value (limits or priority boost)	|default on kuacc is users|
|time|	--time=01:00:00	|Time limit for the job.	|1 hour; default is 2 hours|
|odes|	--nodes=1	|Number of compute nodes for the job.|	default is 1|
|cpus/cores|	--ntasks-per-node=4|	Corresponds to number of cores on the compute node.	|default is 1|
|resource feature|	--gres=gpu:1|	Request use of GPUs on compute nodes|	default is no feature
|memory|	--mem=4096|	Memory limit per compute node for the  job.  Do not use with mem-per-cpu flag.|	default limit is 4096 MB per core|
|memory|	--mem-per-cpu=14000|	Per core memory limit.  Do not use the mem flag,|	default limit is 4096 MB per core|
|account|	--account=users	| Users may belong to groups or accounts.	|default is the user’s primary group.|
|job name|	--job-name=”hello_test”	|Name of job.|	default is the JobID|
|constraint|	--constraint=gpu|	kuacc-nodes	|AVAIL_FEATURES|
|output file|	--output=test.out	|Name of file for stdout.|	default is the JobID|
|email address|	--mail-user=username@ku.edu.tr|	User’s email address|	required|
|email notification	| --mail-type=ALL, --mail-type=END |When email is sent to user.	|omit for no email|

Note: –mem ve –mem-per-cpu flags:
mem-per-cpu: memory per core. If N core is reserved, Nxmem-per-cpu is reserved. Default units are megabytes.

```
#SBATCH --ntasks=5
#SBATCH –-mem-per-cpu=20000
```

Total 5×20000=100000MB is reserved. For GB requests, use only G. Exp: 20G
mem: total memory requested per node. If you request more than one node(N) Nxmem is reserved. Default units are megabytes.

### Loading library and application modules:

Users need to load application and library modules needed for his/her code. As in sample job script,

```
module load python/3.6.1
module load cuda/11.4
module load 8.2.2/cuda-11.4
```

For more information see the installing [software modules page](https://github.com/yagmurakarken/kuacc-guide/blob/master/How%20do%20I%20Use%20Software%20Modules%20on%20Cluster%3F/Environment%20Modules%20and%20Virtual%20Environment.md).

### Running Code:

In this section of job script, users need to run their code.

`python code.py`

After preparing job script, it is submitted by sbatch command.

`sbatch jobscript.sh`


|Command	|Description|
| ------| ------------ |
|sbatch<br><br>sbatch [script]|  Submit a batch job <br>Example:<br> $ sbatch job.sub|
|scancel<br><br>scancel [job_id]| Kill a running job or cancel queued one <br> Example:<br>$ scancel 123456|
|squeue<br><br>squeue| List running or pending jobs<br>Example:<br>$ squeue|
|squeue -u userid<br><br>squeue -u [userid]|List running or pending jobs<br>Example:<br>$ squeue -u john|
















