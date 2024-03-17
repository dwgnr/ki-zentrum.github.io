---
title: "KIZ GPU Cluster"
layout: cluster
sitemap: false
permalink: /cluster/
---

## The Cluster 

Our cluster is tailored to efficiently running Jobs on Nvidia GPUs. 
We do not offer extremely large numbers of CPU cores or extremely large amounts of main memory (RAM). 

All nodes within the cluster utilize Unix-based operating systems, running in text-mode only. 
Hence, a fundamental understanding of tasks such as file handling, scripting, editing, and similar operations in the Unix shell is necessary.

## Apply for an Account

Cluster accounts are managed through our [Moodle course](https://elearning.ohmportal.de/course/view.php?id=372). 
Depending on the type of user, there are different steps that need to be taken:

- **For THN students:** You need access to our [Moodle course](https://elearning.ohmportal.de/course/view.php?id=372), complete the exercises and upload your SSH key there. First, get in touch with your thesis/project advisor and assess the computational requirements you are going to need for your thesis or project. Note that not all projects are necessarily well suited for our GPU cluster. Finally, request access to the Moodle course via email to [kiz-slurm@th-nuernberg.de](mailto:kiz-slurm@th-nuernberg.de). Your account will be activated once you completed all exercises and uploaded your SSH key. 
    - Your email should include the following information: 
        - Name of your thesis/project advisor
        - Type of your project (e.g. bachelor's thesis)
- **For THN staff members:** Contact our cluster administrators at [kiz-slurm@th-nuernberg.de](mailto:kiz-slurm@th-nuernberg.de) to request access to our [Moodle course](https://elearning.ohmportal.de/course/view.php?id=372) and upload your SSH key. 
- **For all others:** Contact our cluster administrators at [kiz-slurm@th-nuernberg.de](mailto:kiz-slurm@th-nuernberg.de). 

## User Guide

Our detailed user guide can be found [here](user-guide). 

## Quickstart

### Connecting to the Cluster

Once your account is activated, you can establish an SSH connection to the Controlhost of the cluster. 

```bash
ssh <username>@<hostname>
```
Usernames follow the THN standard scheme (e.g. mustermannma12345). 
Information about the `<hostname>` of the Controlhost can be found in the [Moodle course](https://elearning.ohmportal.de/course/view.php?id=372). 

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

- More information about data storage can be found in the [User Guide](user-guide/#important-directories). 

### Transferring Data

On Linux and Mac machines, `scp` and `rsync` are the recommended methods for transferring data to and from a remote host.

On Windows, users can utilize the Linux subsystem, use `scp` via PowerShell, or employ additional tools like [WinSCP](https://winscp.net/eng/index.php).

Alternatively, users can also mount remote file systems locally on their machines. 
Refer to the section on [File Synchronization](user-guide/#file-synchronization) in the User Guide for more details.

For handling large volumes of data, we recommend using `scp` or `rsync` due to their typically faster transfer speeds compared to other protocols. 
Moreover, `rsync` offers additional functionalities that can expedite file transfers, such as skipping existing files or resuming interrupted transfers.

### Creating Jobs

- Jobs consist of two components:
    1. **Resource Requests**: Define the required number of CPUs/GPUs, the expected duration of the job, the required memory etc..
    2. **Job Steps**: Define the tasks to be performed (e.g., downloading files and then executing a script).

- There are two primary ways to create jobs:
    1. **Batch Jobs**: Requires the creation of a *submission script* with `SBATCH` directives to parameterize the job.
    2. **Interactive Jobs**: Reserve resources for interactive use of compute nodes.

#### Batch Jobs

- The job is defined using a *submission script* that is started with `sbatch submission_script.sh`
- `SBATCH` directives must always be **at the beginning** of the script.
    - The only exception: *Hashbang* (e.g., `#!/bin/bash`) on the first line.

This an example of a typical submission script for the KIZ HPC cluster: 

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
- More details about the available QOS can be found in the [User Guide](user-guide/#available-resources).

### Retrieve Information

These are some frequently used commands to obtain information about the cluster or your jobs:
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

- Monitor the results and behavior of your jobs on a regular basis to prevent wasting resources.
- Manually terminate unnecessary jobs instead of waiting until the time limit is reached.
- Optimize performance by running short test jobs before committing resources to longer tasks. We recommend using the `seff <jobid>` command on completed jobs to get a quick overview of your resource efficiency. 
- When using GPUs, make sure each GPU is properly utilized (a simple way to check is via the `nvidia-smi` command). 
- Minimize I/O operations on slow file systems like NFS. 
- Remember that this is a multi-user environment. Blocking resources without using them affects your colleagues and fellow students. 
- Before reaching out for assistance, read the [FAQs](#faqs) and [User Guide](user-guide) carefully. Many common problems are already discussed there. 
- In case you still need assistance, contact our administrators at [kiz-slurm@th-nuernberg.de](mailto:kiz-slurm@th-nuernberg.de). 
    - Note that we are a small team and can not provide comprehensive first-level support on topics that are not directly related to the cluster (e.g. your program throws some generic exception). 

## FAQs

### Access 

- **The SSH password prompt appears, but I do not have a password.**
    - Cluster accounts do not have a password. Authentication is done through SSH keys only.
    - The following steps are necessary before you can access the cluster: 
        - [Apply for an account](#apply-for-an-account).
        - Generate a SSH key pair, e.g. via `ssh-keygen -t ed25519 -f ~/.ssh/id_ed2559_thn_hpc`.
        - Upload your SSH public key to [Moodle](https://elearning.ohmportal.de/mod/assign/view.php?id=14861).
        - Configure your SSH connection to use the correct SSH keys for the cluster.
        - Wait until you receive an email notification that your account has been activated.
    - If you completed all the steps above and your SSH connection still doesn't work, refer to the [Troubleshooting SSH section](user-guide/#troubleshooting-ssh) of our User Guide. 
- **My SSH connection does not work.**
    - Refer to the [Troubleshooting SSH section](user-guide/#troubleshooting-ssh) of our User Guide for common connection problems. 
- **I am connected to eduroam and can't access the cluster.**
    - Please connect to the THN VPN.
    - Accessing the cluster from eduroam through a VPN tunnel may seem a bit counterintuitive, but it's currently the only option due to the way the routing is set up internally. 
- **I wish to access an application running on a cluster node via port forwarding.**
    - Certain applications hosted on cluster nodes offer web-based interfaces (e.g. Jupyter Notebooks). Direct access to these applications from your local browser requires port forwarding. 
    - Refer to the [Using Jupyter section](user-guide/#using-jupyter) in our User Guide for a step-by-step example.

### Slurm

- **How can I run a job on the cluster?**
    - All tasks must be submitted to the compute nodes through the Slurm workload manager, which handles resource allocation among users and jobs based on a priority scheme.
    - For comprehensive guidance on Slurm, please refer to our [User Guide](user-guide/#slurm-workload-manager).
    - An example script for a batch job can be found [here](user-guide/#job-template). 
- **How can I run an interactive job on the cluster?**
    - Interactive jobs can be requested by using `srun` with the `--qos=interactive` argument. 
    - Interactive jobs are useful for testing or debugging your application.
    - More information on interactive jobs is available [here](user-guide/#interactive-jobs).
- **I don't want to use Slurm for my work on the cluster.**
    - Unfortunately, this is **not possible**. All work on our compute nodes has to be submitted via Slurm. 
    - Using Slurm ensures a fair resource allocation across all cluster users. 
    - Note that we reserve the right to deactivate user accounts in case of violation. 
- **I have reached the maximum timelimit but my model training hasn't finished yet.**
    - Make sure to save your training states regularly (i.e., checkpointing) and load the most recent state when you start a new job. 
    - See the [Model section](user-guide/#saving-and-loading-machine-learning-models) of our User Guide for more information. 
- **The start of my Enroot container takes a very long time.**
    - This is expected for larger images (>1GB) due to the way the unpacking and caching procedures done by Enroot. 
    - Refer to the [Important Notes](user-guide/#important-notes) in the Container section of our User Guide for more information. 
- **My process was killed by the cgroup out-of-memory (OOM) handler.**
    - If you receive a message like `slurmstepd: error: Detected 47 oom-kill event(s) in StepId=1317540.batch. Some of your processes may have been killed by the cgroup out-of-memory handler.` in your logs, then the allocated main memory (`--mem`) was not sufficient for the job step to complete. 
    - To solve this problem, you can allocate more memory to the job, check for memory leaks in your code and fix them or try making your program more memory-efficient. 

### NFS

- **I have a large dataset that may be of use to others, and I would like to store it in a location accessible to everyone (e.g. `/nfs/data`).**
    - Send an email to [kiz-slurm@th-nuernberg.de](mailto:kiz-slurm@th-nuernberg.de). We will copy the data to for you.  
- **I received the message `Disk quota exceeded`.**
    - You have reached the maximum amount of space you are allowed to occupy on the file system.
    - Try deleting older data or storing your data on a different file system. You can check your quota status with the `quota -s` command to determine whether you are below the limit or not.
    - You can request a quota increase via email to [kiz-slurm@th-nuernberg.de](mailto:kiz-slurm@th-nuernberg.de). 
        - The email should contain the following: 
            - A reason why you need more disk space. 
            - The mount point of the file system you are requesting the quota increase for. 

### General

- **I need a special package/software that is currently not available on the cluster.**
    - You have several options to make the software available:
        - Try building the software from source.
        - Use [Enroot containers](user-guide/#container-with-enroot-and-pyxis).
        - Check if the software is available through [Spack](https://packages.spack.io/) and contact our [administrators](mailto:kiz-slurm@th-nuernberg.de) to get it installed.
- **I want to run a server to perform inference on large language models (LLMs).**
    - We strongly urge you to start such applications interactively (i.e., `--qos=interactive`). If there is truly no other option than submitting a batch job, please ensure that you either set a sufficiently short time limit or manually terminate the job to make the resources available to other users as quickly as possible.
    - Unfortunately, the operating mode and size of our cluster are not designed for jobs that run for days, blocking resources but effectively using them only for a fraction of the time. 
- **My application is not using the GPU even though it should.**
    - Your application/library and its dependencies need to be compiled on a system with CUDA support. A common error is that users setup their Python virtual environments on the Controlhost. The Controlhost does not have CUDA installed and therefore your library can not be built with CUDA enabled. 
    - Hence, make sure that you build your application and its dependencies on one of the compute nodes (e.g. as part of your submission script). 
    - If you are using PyTorch or TensorFlow, you may have chosen a CPU-only installation. 
        - See the official installation procedures of [PyTorch](https://pytorch.org/get-started/locally/) and [TensorFlow](https://www.tensorflow.org/install/pip) for the correct way of installing with GPU support.
    - In other cases, CUDA or CUDA-related libraries may be missing on the host. Ensure you have the required module(s) loaded in the correct version (e.g. CUDA, cuDNN, etc.).
- **I received an error message like `RuntimeError: CUDA Out of memory`.**
    - The error indicates that your allocated GPU does not have enough memory (VRAM) to execute the current task.
    - One of the most common causes of the `CUDA out of memory` error is using a batch size that's too large. Try reducing your batch size and see if that helps. 