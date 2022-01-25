# CPU and Memory Usage

After job is submitted, user is allowed to use ssh for connecting compute node on which job is running.

`ssh username@compute_node`

After ssh to compute node, user can use following commands to check memory and cpu usage of submitted job.
 
**ps:** lists all processes.

`ps -u username -o %cpu,rss,args`

this will give you instantaneous usage every time you run command. Memory usage is in kilobytes.
 
**top/htop:** runs interactively and show live usage statistics.

`htop -u username`

Note: https://gridpane.com/kb/how-to-use-the-top-command-to-monitor-system-processes-and-resource-usage/
https://gridpane.com/kb/how-to-use-the-htop-command-to-monitor-system-processes-and-resource-usage/
 
**nvidia-smi:** shows GPU parameters and GPU memory usage.
 
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

**607MiB / 32510MiB** is how much GPU you use, consider if you need this much GPU or not.