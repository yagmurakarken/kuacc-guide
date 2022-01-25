# GPUs on KUACC Cluster

GPUs on KUACC Cluster can be listed by “kuacc-nodes” command.

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

As in figure, first column(nodelist) lists node names and seventh column lists(GRES) gpu types. (Exp: #SBATCH --gres=gpu:tesla_t4:1)<br>
User can request using gres flag as listed in command output. <br>
User can use gres flag without GPU type. (Exp: #SBATCH --gres=gpu:1) Any gpu available will be reserved by slurm.<br>
User can use gres flag without GPU type, but adds feature with constraint flag and reserves a GPU with specific type. (Exp: #SBATCH --gres=gpu:1, #SBATCH --constraint=tesla_t4) A tesla T4 will be reserved for user as in first example ( #SBATCH --gres=gpu:tesla_t4:1)<br>

This is useful of gpu options. For example, following setup requests for 1 gpu tesla_t4 or tesla_k80
```
#SBATCH --gres=gpu:1
#SBATCH --constraint=tesla_t4|tesla_k80
```

## GPU Specifications:


|Type	|Internal Memory	|CUDA Cores	|Datasheet|	Node Names|
| ------| ------------ | ----- | -------- | ----------- |
|Gtx 1080ti|	11GB|	3584|	https://www.nvidia.com/en-sg/geforce/products/10series/geforce-gtx-1080-ti/	|ag01|
|Tesla k20m|	5GB|	2496|	https://www.nvidia.com/content/PDF/kepler/tesla-k20-active-bd-06499-001-v03.pdf	|be01-be11, da01-da04|
|Tesla k40m|	12GB|	2880|	https://www.nvidia.com/content/dam/en-zz/Solutions/Data-Center/tesla-product-literature/TeslaK80-datasheet.pdf|	sm01|
|Tesla k80|	12GB	|4992|	https://www.nvidia.com/content/dam/en-zz/Solutions/Data-Center/tesla-product-literature/TeslaK80-datasheet.pdf	|sm01, dy02, dy03|
|Tesla t4	|16GB|	2560|	https://www.nvidia.com/content/dam/en-zz/Solutions/Data-Center/tesla-t4/t4-tensor-core-datasheet.pdf|	Ai01-ai10|
|Tesla V100 PCIe |	32GB|	5120|	https://images.nvidia.com/content/technologies/volta/pdf/tesla-volta-v100-datasheet-letter-fnl-web.pdf|	It01-it04|
|Tesla V100-SXM2 (NVLink)|	32GB|	5120|	https://images.nvidia.com/content/technologies/volta/pdf/tesla-volta-v100-datasheet-letter-fnl-web.pdf|	Ai11-ai14|
|Quadro M2000|	4GB|	768|	https://www.nvidia.com/content/dam/en-zz/Solutions/design-visualization/documents/38111-DS-NV-Quadro-M2000-Feb16-US-NV-Fnl-HR.pdf|	Login02, login03|
|Tesla P4|	8GB|	2560|	https://images.nvidia.com/content/pdf/tesla/184457-Tesla-P4-Datasheet-NV-Final-Letter-Web.pdf	|Login02, login03|



**Monitoring GPUS while running jobs:**<br>
While running gpu jobs, You can ssh to compute node and use “nvidia-smi” command for monitoring GPUS. The command provides monitoring and management capabilities for each of NVIDIA’s GPUs. Please also check manuals by “man nvidia-smi”.

```
[root@it04 ~]# nvidia-smi
Wed Oct 27 09:14:33 2021
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 470.57.02    Driver Version: 470.57.02    CUDA Version: 11.4     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  Tesla V100-PCIE...  Off  | 00000000:3B:00.0 Off |                    0 |
| N/A   37C    P0    59W / 250W |    607MiB / 32510MiB |     24%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A    390761      C   namd2                             603MiB |
+-----------------------------------------------------------------------------
```

In command output, you can see GPU version and memory usage. Tesla V100-PCIE has 32GB internal memory and job is using only 603MiB. Tesla k20m would be enough for thıs job, but user reserves tesla V100. It is waste of resources. Please test your job script and find your resource needs. Then, choose GPU type according to your needs and submit your job. 

If there is more than one gpu on node, command output is:

```
(base) [yakarken18@login02 ~]$ nvidia-smi
Tue Dec  7 13:30:04 2021       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 470.57.02    Driver Version: 470.57.02    CUDA Version: 11.4     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  Quadro M2000        Off  | 00000000:08:00.0 Off |                  N/A |
| 56%   25C    P8    10W /  75W |   1546MiB /  4043MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
|   1  Tesla P4            Off  | 00000000:88:00.0 Off |                    0 |
| N/A   48C    P0    24W /  75W |   2383MiB /  7611MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================
|    0   N/A  N/A    168634      C   ...nvs/open-mmlab/bin/python     4673MiB |
|    2   N/A  N/A    198836      C   python                           2335MiB | 
+-----------------------------------------------------------------------------+
```

Command output shows processing at the bottom. You can find you GPU by using PID number.

```
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================
|    0   N/A  N/A    168634      C   ...nvs/open-mmlab/bin/python     4673MiB |
|    2   N/A  N/A    198836      C   python                           2335MiB | 
+-----------------------------------------------------------------------------+
```

**ps aux|grep PID**
```
[root@ai11~] # ps aux |grep 198836
username 198836 94.6 0.0 15394160 314304 pts/0 R1+ 16:07 78:48 p
10/MEFLOTONet-ResUNeyBN2C-f64-i0/Adam-Irle-3-b4/2021-11-18_
1 MEFLOTONet --feature_model ResUNetBN2C --conv1_kernel_size 7 --nu
2C-f64-i0/Adam-Irle-3-b4/2021-11-17_19-09-57/
```

By using command output, GPU 2 with “PID 198836” is used by username.
- Command output show users are running their jobs on Tesla V100 SXM2 gpus with max 6GB memory. These jobs can be run even on beXX servers. Please do not wate GPU resources. 
- There is another issue in this command output. There are 8 GPUs and only 3 Tesla V100 SXM2 gpus are being used. When queue is checked, six GPUs are reserved. That means 3 GPUs are reserved, but not used. These are jupyter notebook jobs. DO NOT reserve GPUs more than you need. If you finish your work with GPUs, scancel your jupyter notebook jobs.
