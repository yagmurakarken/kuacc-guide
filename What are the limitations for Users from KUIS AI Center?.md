# KUIS AI Center Limits

Please run your jobs inside these limits. If you need more resources, you will use public queues (short, mid, long, longer).

## AI Partition User Limits: 

**GPU Limit (max 8 GPU/user and max 8 jobs/user) :** Please use max 8 GPU while working in AI partition. Max job number is limited to 8 jobs with one GPU each.<br>
**CPU Limit (max 5cores/GPU, total max 40cores/user):** Please use max 5cores per GPU. Max core limit is 40cores per user.<br>
**Memory Limit (max 200GB/user):** Max memory limit is set to 200GB. If you need more than this limit, contact to hpc-support@ku.edu.tr.<br>
**Time Limit ( max 7days):** Max time limit is 7 days.<br>

**Important Notes:**

You can run your current script in public queues by just changing following parameters.


|Jobscript for AI Partition	|Jobscript for public queues|
| ------| ------------ |
| #SBATCH –qos=ai| #SBATCH –qos=users| 
| #SBATCH –account=ai| #SBATCH –qos=users | 
| #SBATCH –partition=ai| #SBATCH –partition=mid  | 
| #SBATCH –time=1-0|#SBATCH –time=1-0  | 


Please check sample job scripts(/kuacc/jobscripts) and kuacc documents.

Please define gpu type and partition in your jobscripts while working at public queues. Please check usage of **constraint** and **gres** parameters in KUACC documents.

For T4,
```
#SBATCH --gres=gpu:tesla_t4:1
```
or
```
#SBATCH --constraint=tesla_t4
```
For tesla_v100, (use both)
```
#SBATCH --gres=gpu:tesla_v100:1
#SBATCH --constraint=ai
```
Default memory in cluster was decreased to 4096MB. Please use mem or mem-per-cpu parameters if you need more memory instead of increasing core number.
```
#SBATCH --mem=100G
```
In public queues, your job will be requeued due to interruption privilege. While running jobs in public queues, please make sure your code saves it state regularly and starts from last saved state if it is restarted.<br>
There are 80 Tesla T4, 12 Tesla K80 and 32 Tesla V100 gpus. If your code can run on Tesla T4 or Tesla K80 gpus, please prefer these gpus and don’t run your code on Tesla V100 gpus.

 


 
