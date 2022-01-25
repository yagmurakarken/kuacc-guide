# df

Disk filesystem – is used to list a full summary of available and used disk space of file system.

`df -kh`

**k:** To display all file system information and usage in 1024-byte blocks
**h:** human readable

**Example usage:**

```
[root@login03 ~]# df -kh
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/centos-root       200G   70G  131G  35% /
devtmpfs                      252G     0  252G   0% /dev
tmpfs                         252G  5.3M  252G   1% /dev/shm
tmpfs                         252G  422M  252G   1% /run
tmpfs                         252G     0  252G   0% /sys/fs/cgroup
/dev/sda2                    1016M  247M  770M  25% /boot
/dev/sda1                     200M  9.8M  191M   5% /boot/efi
beegfs_home2                  219T  164T   55T  75% /home2
beegfs_scratch                175T   77T   99T  44% /scratch
172.20.239.200:/vol_home2      82T   72T   11T  88% /userfiles
172.20.239.202:/VOL_KUTTAM     49T   34T   16T  69% /kuttam
172.20.239.201:/vol_datasets   50T   45T  5.7T  89% /datasets
```

Disks mounted on:<br>
/ : server root disk<br>
/scratch : User home disk<br>
/datasets: General Datasets disk<br>
/userfiles: User Datasets disk<br>
/kuttam: Kuttam disk<br>
/home2 : System Disk<br>

useful link: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/s2-sysinfo-filesystems-df