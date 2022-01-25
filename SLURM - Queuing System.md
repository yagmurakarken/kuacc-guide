# SLURM - Queuing System
KUACC uses SLURM (Simple Linux Utility for Resource Management) to manage resource (processors, RAM, gpu etc) and jobs on cluster. SLURM is an open source cluster management and job scheduling system. It is very popular within HPC world. More than 60% of the Top 500 super computers use slurm.

## Slurm Terminology:
Cluster
: is a collection of computers that work together for the purpose of high-performance computing (KUACC HPC cluster)\
Node
: server, computer (Example: ai01, ai02 etc)\
Partition
: is a set of compute nodes. A node can belong to more than one partition, and each partition can be configured to enforce different resource limits and policies. (Example: users, ai, ilac etc)\
Account
: is a slurm group used to enforce limits and priority. Users are associated with an slurm account.\
Qos
: is a mechanism for jobs to request certain features, scheduling priority, and limits. This is used for requeuing jobs. (Examples: users, ai, ilac etc)\
Task
: means process in Slurm. By default, 1 task uses 1 core.\
Job
: is a collection of tasks. Jobs have an ID number and a name. ID is assigned by slurm. Name can be assigned by user.

## Batch and Interactive jobs
All users must submit jobs to reserve resource and run their codes on cluster. There are two kinds of jobs which are called as interactive and batch jobs. See the batch and interactive jobs page for more information.

- [How do I Write and Submit a Jobscript?](https://github.com/yagmurakarken/kuacc-guide/blob/master/How%20do%20I%20Run%20My%20Job%3F/How%20do%20I%20Write%20and%20Submit%20a%20Jobscript%3F.md)
- [How do I Interact with Jobs in Real Time?](https://github.com/yagmurakarken/kuacc-guide/blob/master/How%20do%20I%20Run%20My%20Job%3F/How%20do%20I%20interact%20with%20Jobs%20in%20Real%20Time%3F.md)
