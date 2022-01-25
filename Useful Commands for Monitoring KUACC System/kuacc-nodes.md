# kuacc-nodes

Lists cluster nodes with specifications (CPU types, GPU list,Memory, Features etc). it is detailed version of sinfo command.

```
(base) [yakarken18@login02 ~]$ kuacc-nodes
NODELIST        STATE       CPUS    S:C:T    MEMORY   TMP_DISK GRES                          AVAIL_FEATURES                                    
ai[01,04-06,09] mixed         40   2:20:1    503000          0 gpu:tesla_t4:8                ai,ib,compute,40cpu,gpu                                 
ai[11-14]       mixed         40   2:20:1    503000          0 gpu:tesla_v100:8              ai,ib,compute,40cpu,gpu                                          
buyukliman      mixed         72   2:18:2    250000          0 (null)                        hamsi,ib,compute,72cpu                                     
da[03-04]       mixed         20   2:10:1    250000          0 gpu:tesla_k20m:1              biyofiz,ib,compute,20cpu                                          
dy02            mixed         36   2:18:1    504000          0 gpu:tesla_k80:4               ai,ib,compute,36cpu,gpu                                         
dy03            mixed         24   2:12:1    450000          0 gpu:tesla_k80:8               ai,ib,compute,24cpu,gpu                                  
it[01-02]       mixed         40   2:20:1    500000          0 gpu:tesla_v100:1              IT,ib,compute,tesla_v100                                          
sm01            mixed         20   2:10:1     64000          0 gpu:tesla_k40m:2,gpu:tesla_k80:1 iui,ib,compute,20cpu                                      
ag01            allocated      8    2:4:1    124000          0 gpu:gtx_1080ti:2              cosbi,ib,compute,8cpu,gpu                                       
ai[02-03,07-08, allocated     40   2:20:1    503000          0 gpu:tesla_t4:8                ai,ib,compute,40cpu,gpu                                  
be[01-12]       allocated     12    2:6:1    126000          0 gpu:tesla_k20m:1              ilac,ib,compute,12cpu                                                 
da02            allocated     20   2:10:1    250000          0 gpu:tesla_k20m:1              biyofiz,ib,compute,20cpu                                         
it[03-04]       allocated     40   2:20:1    500000          0 gpu:tesla_v100:1              IT,ib,compute,tesla_v100                                          
rk01            allocated     72   2:18:2    504000          0 (null)                        kutem,ib,compute,72cpu,HT                                         
da01            idle          20   2:10:1    250000          0 gpu:tesla_k20m:1              biyofiz,ib,compute,20cpu                                         
ke[01-08]       allocated     36   2:18:1    504000          0 (null)                        cosmos,ib,compute,36cpu                                                   
============================================================================================================
KUACC NODES CPU LIST
============================================================================================================
login02-login03  |model name      : Intel(R) Xeon(R) CPU E5-2695 v4 @ 2.10GHz
ag01             |model name      : Intel(R) Xeon(R) CPU E5-2637 v4 @ 3.50GHz
be01 - be14      |model name      : Intel(R) Xeon(R) CPU E5-2640    @ 2.50GHz
buyukliman       |model name      : Intel(R) Xeon(R) CPU E5-2695 v4 @ 2.10GHz
da01 - da04      |model name      : Intel(R) Xeon(R) CPU E5-2670 v2 @ 2.50GHz
dy02             |model name      : Intel(R) Xeon(R) CPU E5-2695 v4 @ 2.10GHz
dy03             |model name      : Intel(R) Xeon(R) CPU E5-2695 v2 @ 2.10GHz
ke01 - ke08      |model name      : Intel(R) Xeon(R) CPU E5-2695 v4 @ 2.10GHz
rk01             |model name      : Intel(R) Xeon(R) CPU E5-2695 v4 @ 2.10GHz
sm01             |model name      : Intel(R) Xeon(R) CPU E5-2680 v2 @ 2.80GHz
it01 - it04      |model name      : Intel(R) Xeon(R) Gold 6148      @ 2.40GHz
ai01 - ai14      |model name      : Intel(R) Xeon(R) Gold 6248      @ 2.50GHz
============================================================================================================
```

NODELIST, STATE, CPUS, S:C:T(Socket:CorePerSocket:ThreadsPerCore), MEMORY, TMP_DISK (TEMPORARY_DISK), GRES, AVAIL_FEATURES

⚠️⚠️⚠️ This command lists specifications of all nodes in cluster. It is very useful when you need specific resource. For example, GRES column shows all gpu types in cluster. You can choose a specific gpu by using gres flag in your script with gres from this command output.

`#SBATCH --gres=gpu_tesla_k80`

⚠️⚠️⚠️ AVAIL_FEATURES column in command output lists all features of nodes. These Features are set by system admins and used for constraint flag in slurm job script.
For example,
```
(base) [yakarken18@login02 ~]$ kuacc-nodes |grep ai
ai[01,04-06,09] mixed         40   2:20:1    503000          0 gpu:tesla_t4:8   ai,ib,compute,40cpu,gpu,tesla_t4,6248,molpro,vnc 
ai[11-14]       mixed         40   2:20:1    503000          0 gpu:tesla_v100:8 ai,ib,compute,40cpu,gpu,tesla_v100,6248,molpro,vnc 
dy02            mixed         36   2:18:1    504000          0 gpu:tesla_k80:4  ai,ib,compute,36cpu,gpu,tesla_k80,e52695,e52695v4,
dy03            mixed         24   2:12:1    450000          0 gpu:tesla_k80:8  ai,ib,compute,24cpu,gpu,tesla_k80,e52695,e52695v2, 
ai[02-03,07-08, allocated     40   2:20:1    503000          0 gpu:tesla_t4:8   ai,ib,compute,40cpu,gpu,tesla_t4,6248,molpro,vnc 
ai01 - ai14      |model name      : Intel(R) Xeon(R) Gold 6248      @ 2.50GHz
```
```
ai[01-04,06-10] mixed 40 2:20:1 503000 0 gpu:tesla_t4:8                ai,ib,compute,40cpu,gpu,tesla_t4,6248,molpro,vnc
```

**Features for ai nodes:**<br>
**ai[01-10]:** Feature=ai,ib,compute,40cpu,gpu,tesla_t4,6248,molpro,vnc<br>
**ai[11-14]:** Feature= ai,ib,compute,40cpu,gpu,tesla_v100,6248,molpro,vnc<br>
**dy02:** Feature= ai,ib,compute,36cpu,gpu,tesla_k80,e52695,e52695v4,vnc<br>
**dy03:** Feature=ai,ib,compute,24cpu,gpu,tesla_k80,e52695,e52695v2,vnc<br>
**ai:** ai partition<br>
**ib:** node with infiniband network<br>

**compute: compute node**<br>
**24cpu:** node with 24cores<br>
**36cpu:** node with 36cores<br>
**40cpu:** node with 40cores<br>
**tesla_XX:** node with tesla_XX gpu<br>
**molpro:** node with 1TB local disk<br>
**6248:** node with Intel Gold 6248 cpu<br>
**e52695:** node with Intel e52695 cpu<br>

⚠️⚠️⚠️ Some users needs to run their jobs on specific node. For example, on Intel Gold 6248 cpus. User can use 6248 feature in constraint flag and user limits jobs to run on 6248 cpus.<br>
⚠️⚠️⚠️ Any feature can be added into node available feature list.

Examples:<br>
By using constraint and feature tesla_k80. You can request only tesla_k80 nodes.

`#SBATCH --constraint=tesla_k80`

Some applications create to many tmp files. This will cause on issue on file system. Therefore, they use server disk for scratch data. Servers with molpro feature have local disks over 1TB. There is tmp2 folder on these nodes which can be used as a scratch folder.<br>
By using constraint and feature molpro. tmp2 folder as stratch.
```
#SBATCH --constraint=molpro
export $TMP=/tmp2
```
At the end of job, scratch data should be cleaned.
