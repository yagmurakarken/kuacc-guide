# Cancelling Jobs

User can cancel their job by scancel command.
```
scancel   job_id                           # kills job with given job_id
scancel -u username                        #kills user’s all jobs. User can only kill his/her own jobs
scancel -t pending -u username             #kills user’s all pending jobs.
scancel -t running -u username             #kills user’s all running jobs.
```

Job_id can be found by using:
```
squeue -u username
```
or
```
kuacc-queue|grep username
```