---
title: "KIZ GPU Cluster"
layout: cluster
sitemap: false
permalink: /cluster/
---

## The Cluster 

Our cluster is tailored to efficiently running Jobs on Nvidia GPUs. 
We do not offer very large numbers of CPU cores or very large amounts of main memory (RAM). 

All nodes within the cluster utilize Linux operating systems, operating exclusively in text-mode. 
Hence, a fundamental understanding of tasks such as file handling, scripting, editing, and similar operations is necessary.

## Apply for an Account

Cluster accounts are managed through our [Moodle course](https://elearning.ohmportal.de/course/view.php?id=372). 
Depending on the type of user, there are different steps that need to be taken:

- **For THN students:** You need access to our [Moodle course](https://elearning.ohmportal.de/course/view.php?id=372), complete the exercises and upload your SSH key there. First, get in touch with your thesis/project advisor and assess the computational requirements you are going to need for your thesis or project. Note that not all projects are necessarily well suited for our GPU cluster. Finally, request access to the Moodle course via e-mail to [kiz-slurm@th-nuernberg.de](mailto:kiz-slurm@th-nuernberg.de). Your account will be activated once you completed all exercises and uploaded your SSH key. 
- **For THN staff members:** Contact our cluster administrators at [kiz-slurm@th-nuernberg.de](mailto:kiz-slurm@th-nuernberg.de) to request access to our [Moodle course](https://elearning.ohmportal.de/course/view.php?id=372) and upload your SSH key. 
- **For all others:** Contact our cluster administrators at [kiz-slurm@th-nuernberg.de](mailto:kiz-slurm@th-nuernberg.de). 

## User Guide

Our detailed user guide can be found [here](/cluster/user-guide/). 

## Quickstart

### Connecting to the Cluster

Once your account is activated, you can establish an SSH connection to the login node of the cluster. 

```bash
ssh <username>@<hostname>
```
Usernames follow the THN standard scheme (e.g. mustermannma12345).

We highly recommend using tools like [Mosh](https://mosh.org) and [tmux](https://wiki.ubuntuusers.de/tmux/) 
to prevent issues with connection interruptions and to keep sessions alive even after logout.

### Data Storage

Various file systems are accessible across all nodes in the cluster. 
Choose the appropriate storage location for your data depending on size, required speed of access, and lifetime. 

These are some of the more important storage locations: 

- `/home/$USER`:
    - For source code and configuration files (*20GB Quota*)
- `/nfs/scratch/<students|staff>/$USER`:
    - For storing larger amounts of data (*200GB Quota*)
- `/nfs/data`:
    - Various datasets (read-only access)
- `/mnt/md0/$USER`:
    - Fast SSDs on the compute nodes (*100GB Quota*)
- `/net/ml[0-N]`:
    - Enables network access to the compute nodes' SSDs

- More information about data storage can be found in the [User Guide](cluster/user-guide.md#important-directories). 

### Transferring Data

On Linux and Mac machines, `scp` and `rsync` are the recommended methods for transferring data to and from a remote machine.

On Windows, users can utilize the Linux subsystem, use `scp` via PowerShell, or employ additional tools like [WinSCP](https://winscp.net/eng/index.php).

Alternatively, users can also mount remote file systems locally on their machines (refer to the section on [file synchronization](cluster/user-guide.md#file-synchronization) in the user guide).

For handling large volumes of data, we recommend using `scp` or `rsync` due to their typically faster transfer speeds compared to other protocols. 
Moreover, `rsync` offers additional functionalities that can expedite file transfers, such as skipping existing files or resuming interrupted transfers.

### Creating Jobs

- Jobs consist of two components:
    1. **Resource Requests**: Define, (among other tings) the required number of CPUs/GPUs, the expected duration of the job, or the required memory.
    2. **Job Steps**: Define the tasks to be performed (e.g., downloading files and then executing a script).

- There are two ways to create jobs:
    1. **Batch Jobs**:
        - Requires the creation of a *submission script* with `SBATCH` directives to parameterize the job.
    2. **Interactive Jobs**:
        - Reservation of resources for interactive use of compute nodes.

#### Batch Jobs

- The job is defined using a *submission script*.
- `SBATCH` directives must always be **at the beginning** of the script.
    - The only exception: *Hashbang* (e.g., `#!/bin/bash`) on the first line.

```bash
#!/bin/bash
#SBATCH --job-name=example # Job name
#SBATCH --partition=p0     # Partition name
#SBATCH --nodes=1          # Number of nodes
#SBATCH --ntasks=1         # Total number of tasks across all nodes
#SBATCH --cpus-per-task=2  # Number of CPU cores per task
#SBATCH --mem-per-cpu=1G   # Memory per CPU core
#SBATCH --time=00:10:00    # Runtime limit (Format HH:MM:SS)

##### Steps to be executed on the compute node #####
echo "Compute node $(hostname)"
sleep 5s
cat /etc/*rel*
```

#### Interactive Jobs

Interactive jobs are used to create shell sessions on a compute node, allowing users to freely navigate on the node.

```bash
# Start an interactive Bash session on the default partition:
srun --qos=interactive --pty bash -i
# srun accepts the same arguments as sbatch
srun --qos=interactive \
    --partition=p0 \
    --mem-per-cpu=1G \
    --cpus-per-task=2 \
    --time=00:10:00 \
    --pty bash -i
```

**Important note:** Interactive jobs can only be started in the QOS `--qos=interactive`. Hence, you always need to pass this argument explicitly.

#### Quality-of-Service

- Resource allocation is managed via the so-called **Quality of Service** (QOS). 
- Each QOS is tailored to a specific use case or user group. 
- The use of a specific QOS is controlled with `--qos=qos_name`.
- More details about the available QOS can be found in the [User Guide](cluster/user-guide.md#available-resources).

### Retrieve Information

```bash
# Overview and status for all partitions
sinfo

# List of jobs and their allocation to nodes/partitions
squeue

# Detailed information about the usage of compute nodes
scontrol show node <nodename>

# Detailed information about a job
scontrol show job <jobid>

# Quick overview of a job's resource consumption (efficiency report)
seff <jobid>

# Information about the assigned QOS
sacctmgr show assoc user=$USER format=user,qos%50
```

## Good Practices

- Regularly monitor your job results to prevent wasting resources.
- Manually terminate unnecessary jobs instead of relying on them to be killed when reaching the time limit.
- Optimize performance by running short test jobs before committing resources to longer tasks. 
- When using GPUs, make sure each GPU is properly utilized (a simple way to check is via the `nvidia-smi` command). 
- Minimize I/O operations on slow file systems like NFS. 
- Remember that this is a multi-user environment. Blocking resources without using them affects your colleagues and fellow students.
- For assistance, reach out to our administrators at [kiz-slurm@th-nuernberg.de](mailto:kiz-slurm@th-nuernberg.de). 