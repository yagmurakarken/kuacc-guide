# scontrol show node node_name

This command is used to check any information about compute nodes.

```
[root@login03 ~]# scontrol show node ai12
NodeName=ai12 Arch=x86_64 CoresPerSocket=20
   CPUAlloc=23 CPUErr=0 CPUTot=40 CPULoad=13.54
   AvailableFeatures=ai,ib,compute,40cpu,gpu,tesla_v100,6248,molpro,vnc
   ActiveFeatures=ai,ib,compute,40cpu,gpu,tesla_v100,6248,molpro,vnc
   Gres=gpu:tesla_v100:8
   NodeAddr=ai12 NodeHostName=ai12 Version=17.02
   OS=Linux RealMemory=503000 AllocMem=487188 FreeMem=109049 Sockets=2 Boards=1
   State=MIXED ThreadsPerCore=1 TmpDisk=0 Weight=90 Owner=N/A MCS_label=N/A
   Partitions=admin,short,mid,ai
   BootTime=2021-10-20T14:17:44 SlurmdStartTime=2021-10-25T21:10:44
   CfgTRES=cpu=40,mem=503000M,gres/gpu:tesla_v100=8
   AllocTRES=cpu=23,mem=487188M,gres/gpu:tesla_v100=3
   CapWatts=n/a
   CurrentWatts=0 LowestJoules=0 ConsumedJoules=0
   ExtSensorsJoules=n/s ExtSensorsWatts=0 ExtSensorsTemp=n/s
   ```

**Information: NodeName, Arch(architecture), CoresperSocket, CPUAlloc, CPUErr, CPUTot, CPULoad, AvailableFeatures, ActiveFeatures, Gres, NodeAddr, NodeHostName, Version, OS, RealMemory, AllocMem, FreeMem, Sockets, Boards, State, ThreadsPerCore, TmpDisk, Weight, Owner, MCS_label, Partitions, BootTime, SlurmdStartTime, CfgTRES, CapWatts, CurrentWatts, LowestJoules, ConsumedJoules..**<br>

**AvailableFeatures:** You can use kuacc-info and choose a node from list. Then, you can use scontrol show node node_name command and check its feature for constraint flag.<br>
**Gres:** shows gpu version on node<br>
**Partitions:** shows node’s partitions<br>
**CfgTRES:** Resources available on node<br>
**AllocTRES:** Resources allocated on node (This output has a bug. It only shows gpu usage with gpu version (gres=gpu:tesla_v100:x). If user submit job with –gres=gpu:1, it is not listed in command output.<br>


⚠️⚠️⚠️ You can check other parameters by manual command “man scontrol”