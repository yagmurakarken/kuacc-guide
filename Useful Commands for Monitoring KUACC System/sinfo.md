# sinfo

Lists information about Slurm nodes and partitions. Command output has 6 columns.<br>
**Partition:** Slurm partitions<br>
**Avail:** Partition availability<br>
**Timelimit:** Partition max time limit<br>
**Nodes:** Nodes in requested partition<br>
**State:** State of nodes(mix, idle, down, draining, drained, mix, alloc)<br>
- idle:free
- down: node is down
- draining: issue about node and node is closed for new jobs. Node will be taken out of cluster after jobs are finished
- drained:node is closed to all jobs
- mix:some of resource on node is used
- alloc:resource on node is fully allocated(used). No resource available on node.

**Nodelist:** Nodes in partition
**sinfo** shows all partitions and nodes in cluster. For ai partition, you can use **“sinfo|grep ai”**

```
[root@login02 ~]# sinfo|grep ai
PARTITION   AVAIL  TIMELIMIT  NODES  STATE NODELIST
admin          up   infinite     30    mix ag01,ai[01,03-14],be[04,06-07],buyukliman,da[01-04],dy03,it[02-04],ke[02,04],rk01,sm01
admin          up   infinite      3   idle ai02,be[11-12]
short*         up    2:00:00     29    mix ag01,ai[01,03-14],be[04,06-07],buyukliman,da[01-04],dy03,it[01-04],rk01,sm01
short*         up    2:00:00      3   idle ai02,be[11-12]
mid            up 1-00:00:00     18    mix ai[05-11],be[04,06-07],buyukliman,da[03-04],dy03,it[03-04],rk01,sm01
long           up 7-00:00:00     19    mix ag01,ai[06-14],be[04,06-07],buyukliman,da04,dy03,it04,rk01,sm01
ai             up 7-00:00:00     14    mix ai[01,03-14],dy03
ai             up 7-00:00:00      1  alloc dy02
ai             up 7-00:00:00      1   idle ai02
```

In command output,<br>
Partition: ai<br>
Availibility: partition is upup<br>
Time limit: max 7days<br>
Nodes-State-Nodelist:<br>
- There are 14 nodes with mix state. It means that some of resources on these nodes(ai[01,03-14],dy03) are used. There is still resource.
- There is only one node(dy02) fully allocated.
- There is only one node(ai02) free. fully available

⚠️⚠️⚠️ sinfo command is useful for listing resources in a short version. However, there is another command(kuacc-info) which is more detailed and more useful.
