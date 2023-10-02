# GPU Node Access and Configuration Guide

This guide outlines the steps to access a GPU node with 8 NVIDIA A30 GPUs, and set up a personal environment for Jupyter Lab.
It is intended for graduate students who are working with Dr. Femiani or other projects involving the MU Robotics program that need access to GPU's. 

Some things to note:
* This node is currently reserved for our use. In the future it may be added to the RedHawk HPC Job Scheduler.  I may not remmebr to come back and edit this post at that time. 



## 1. SSH Connection and Port Forwarding

Connect to the server and set up port forwarding:

```bash
ssh -L 8888:localhost:8888 <userid>@mualhpcp50.hpc.miamioh.edu
```

This command establishes an SSH connection to the server, and sets up port forwarding from your local port 8888 to the server's port 8888.

## 2. Module Loading

Load the necessary modules:

```bash
module load tmux-3.3a
module load anaconda-python3.10
```

Add the above lines to your `~/.bashrc` file to load these modules automatically in future sessions.

## 3. Tmux Session

Start a new tmux session:

```bash
tmux
```

Tmux allows processes to continue running even if the SSH connection is lost.

To reattach to a disconnected session:

```
tmux attach
```


### Creating a Tab for Jupyter

In tmux, create a new tab by pressing `Ctrl + B`, followed by `c`. 
You can name that tab "jupyter" or similar by pressing `Ctrl + B` followed by `,` and then entering a name. 

## 4. Launch Jupyter Lab

Within the tmux tab, launch Jupyter Lab without opening a browser:

```bash
jupyter lab --no-browser
```

## 5. Access Jupyter Lab

Control+Click on the provided link to `localhost:8888` (or copy and paste the link) to access Jupyter Lab on your local browser.

## 6. Port Conflict Resolution

If port 8888 is occupied, Jupyter will attempt using 8889. 
This would be a problem, since if you fiollowed my instructions you are forwarding port 8888. 
In such a case, leave the old session running but open a new SSH session with updated port numbers:

```bash
ssh -L 8889:localhost:8889 <userid>@mualhpcp50.hpc.miamioh.edu
```

Then go back and Control+Click on the link.
If you disconnected the original SSH session on accident, no worries, just use tmux to reattach in the new SSH window and try to find the link. 

IF it has scrolled out of view, you can also create a new tmux tab and type "jupyter notebook list"

## 7. Personal Conda Environment

Clone the base conda environment and install a new kernel for Jupyter Lab:

```bash
conda create --name myenv --clone base
python -m ipykernel install --user --name myenv
```

## 8. Reconnect to SSH and Tmux Session

If disconnected, re-establish SSH with port forwarding:

```bash
ssh -L 8888:localhost:8888 <userid>@mualhpcp50.hpc.miamioh.edu
```

Reattach to the tmux session to access running processes:

```bash
tmux attach
```

## 9. Web-based NX Client

Sometimes you may need to use an interactive desktop, e.g. to download data from Google drive. 
(They provide command line tools buyt rate limit them). 
In that case, you can connect to the NX Web Client. 
Instructions for that are in our slack channel. 
