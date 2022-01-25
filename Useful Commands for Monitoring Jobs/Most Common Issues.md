# Most Common Issues

- Segmentation fault – This is the error when your code is trying to reach outside the allocated memory. Sometimes, increasing memory solves the issue.
- Slurmstepd error – shows exceeded memory limit. Not allocating enough memory(default memory/core: 4GB). Increasing memory with slurm mem parameters(mem,mem-per-cpu) solves the issue.
- Requesting much more resources than available and waiting in queue. Please test your code and find out cpu-memory needs. Do not request more resources than you need.
- Reserving much more resources than needed and causing other jobs queued.
- User installed software issues. Please use modules on Cluster first.
- Anaconda Virtual Environments would be tricky. Please search errors online and check the solutions shared by users who had same issue.

For any problem contact with hpc@support.ku.edu.tr .
