# Interactive Jobs

Batch jobs are submitted to slurm queuing system and runs when there is requested resource available. However, it can’t be used when user test and troubleshoot code in real time. Interactive jobs allow to interact with applications in real time. Users can then run graphical user interface (GUI) applications, execute scripts, or run other commands directly on a compute node.

## Using srun command:

srun will submit your resource request to the queue. When the resource is available, a new bash session starts on reserved compute node. Same slurm flags are used for srun command.
Example:<br>
`srun -N 1 -n 4 -A users -p short --qos=users --gres=gpu:1 --mem=64G --time 1:00:00 --constraint=tesla_v100 --pty bash`

By this command, slurm reserves 1 node, 4 cores, 64GB RAM, 1 gpu and constraint flag limits gpu type to tesla_v100 gpus with 1 hour time limit in short queue. Then, opens a terminal on compute node. If the terminal on compute node is closed, job is killed on queue.

## Using salloc command:
salloc works same as srun --pty bash.  It will submit your resource request to queue. When the resource is available, it opens a terminal on the login node. However, you will have permission to ssh to reserved node.
Example: Same as in srun<br>
`salloc -N 1 -n 4 -A users -p short --qos=users --gres=gpu:1 --mem=64G --time 1:00:00 --constraint=tesla_v100`

When resource is granted, need to find which node is reserved.
`squeue -u username` or `kuacc-queue|grep username`
 
`ssh username@computenode_name`

⚠️⚠️⚠️  Interactive jobs die when you disconnect from the login node either by choice or by internet connection problems. To keep a job alive you can use a terminal multiplexer like tmux,emacs,screen

## How to run a GUI by using interactive jobs?

If you want to run graphical user interface (GUI) applications (Matlab, Mathematica, Rstudio, Ansys), you need to connect to login nodes with X11 forwarding and submit an interactive job with x11 parameter.

### Procedure for GUI:

Connect to cluster with X11 forwarding enabled.

`ssh login.kuacc.ku.edu.tr –Xl username`

Note: If you are using Mac, you may need to use Y depending on your x11 forwarding settings. Also, you need to install [xquartz] (https://www.xquartz.org/)

Submit an interactive job with x11 parameter and reserve a compute node.

```
srun --x11 -N 1 -n 1 -p short --time=1:00:00 --pty bash
```
or
```
salloc --x11 -N 1 -n 1 -p short --time=1:00:00
```
then,
```
squeue -u username
ssh computenodename -Xl username
```
Then, you can load application module and start GUI on compute node.

Note: The user must leave the X11 forwarded login node session open where they submitted the job.

Note: GUI session would be slow due to network connection. If you are using VPN, it would be much slower. Also, it will be killed if there is any internet shortage. You can avoid all these issues by using VNC connection and run your GUI application on login nodes. 

## Software for Interactive Jobs:

There are multiple software you can use for your interactive job:
- If you use directly vi, vim check the [tmux page] (KUACC Guide/How do I Use Software Modules on Cluster?/Terminal Multiplexer(Tmux).md)
- For setup PyCharm see the [procedure] (https://drive.google.com/file/d/1UAEKGEo8NOLMohmlJ2fZ04kOl-sZGPu2/view?usp=sharing)
- or you can use Jupyter Notebook by submitting a Jupiter Notebook job. For Jupyter Notebook follow the [instructions] (https://drive.google.com/file/d/1AqxOrJLuIwkA-9TucEnh6cyjlBK6Hy9G/view?usp=sharing).



