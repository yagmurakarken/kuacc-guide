# Job Log Files

When a job is submitted, an output file defined in job scripts logs all outputs related to job including errors.
In job scripts,

`#SBATCH --output=test-%j.out`

Please check log file if you have any issue with your jobs.