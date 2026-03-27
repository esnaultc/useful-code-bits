## HPC slurm commands

I set those as aliases for simplicity.

Printing current running jobs with useful extra information such as non-truncated name of job, work directory and time remaining:

```bash
squeue -u $USER \
    # print columns    JOBID PARTITION  NAME  STATE  TIME  EXEC_HOST  TIME_LEFT  WORK_DIR
    --format "    %.10A  %.10P  %.15j  %.3t  %.8M  %.10B  %.10L  %Z" | \
    # clean up the work dir path
    sed "s@non_informative_long_path_prefix_to_remove@@g" | \
    # sort by work dir
    (sed -u 1q; sort -k 8)
```

Printing all jobs that failed, timed-out or ran out of memory in the last 24h:

```bash
sacct --state FAILED,TIMEOUT,OUT_OF_MEMORY \
    # print columns  JobID  JobName State  ExitCode  Start  End  WorkDir
    --format="JobID,JobName,State%-15,ExitCode%-8,Start%-22,End%-22,WorkDir%-150" \
    # show allocations
    -X \
    # set start time to 24h ago
    --starttime now-1days \
    # set end time to now
    --endtime now | \
    #  clean up the work dir path
    sed "s@non_informative_long_path_prefix_to_remove@@g"  | \
    # sort by workdir
    (sed -u 1q; sort -k 6)
```
