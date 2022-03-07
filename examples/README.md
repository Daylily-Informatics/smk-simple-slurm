# Examples

Each directory contains an example usage of the simple slurm profile. You can run
them on your cluster to confirm the expected behavior.

* `cluster-cancel` - Cancel all submitted jobs with `scancel` when the main
  Snakemake process is cancelled (requires Snakemake 7.0.0+)

* `dynamic-resources` - Increase memory for a rule on restart after each failed
  attempt

* `jobs-per-second` - Measures how many jobs Snakemake can submit to Slurm per
  second

* `out-of-memory` - Triggers an out-of-memory error. Snakemake can handle this
  by default

* `singularity` - Run a rule inside a singularity container

* `threads` - Increase the `threads` for a rule. It is responsive to `--jobs`.
  In other words, it will scale down the number of threads used if there aren't
  enough available (thus make sure to pass `{threads}` to the software you are
  running). This mainly applies when running the rules locally (i.e. without the
  profile). When submitting to the cluster, `--jobs` refers literally to jobs,
  not cores like in local mode

* `time-integer` - Specify `--time` as an integer (minutes)

* `time-string` - Specify the time as `"days-hours:minutes:seconds"`

* `timeout` - Triggers a timeout error. Snakemake requires the assistance of a
  custom script to `--cluster-status` to handle this error. Otherwise it just
  stalls indefinitely
