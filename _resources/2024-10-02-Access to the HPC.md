---
title: "GPU Node 50 Access and Configuration Guide"
date: 2024-01-01
categories: resources
tags: 
    - AI
    - Tutorials
    - GPU
    - Jupyter
    - SSH
---

# GPU Node Access and Configuration Guide

This guide outlines the steps to access a GPU node with 8 NVIDIA A30 GPUs and configure a personal environment for Jupyter Lab. It’s intended for graduate students working with Dr. Femiani or other projects involving the MU Robotics program that require GPU resources.

> **Note:** The node is currently reserved for specific use. In the future, it may be added to the RedHawk HPC Job Scheduler. This guide might not be updated at that time.

---

## 1. Establish SSH Connection with Port Forwarding

Set up an SSH connection with port forwarding to enable access to Jupyter Lab:

~~~bash
ssh -L 8888:localhost:8888 <userid>@mualhpcp50.hpc.miamioh.edu
~~~

- `8888:localhost:8888`: This forwards port 8888 on the remote server to your local machine.
- Replace `<userid>` with your actual username.

> **Tip:** Consider setting up SSH keys for passwordless login to enhance security and convenience.

---

## 2. Load Necessary Modules

Before running processes, load the required modules:

~~~bash
module load tmux-3.3a
module load anaconda-python3.10
~~~

To make sure these modules load automatically for future sessions, append them to your `.bashrc` file:

~~~bash
echo "module load tmux-3.3a" >> ~/.bashrc
echo "module load anaconda-python3.10" >> ~/.bashrc
~~~

> **Tip:** Use `source ~/.bashrc` to reload the configuration without logging out.

---

## 3. Using Tmux for Persistent Sessions

Tmux allows you to run commands that continue even if you disconnect from SSH.

Start a new tmux session:

~~~bash
tmux
~~~

To reattach to a disconnected session:

~~~bash
tmux attach
~~~

### Creating a New Tmux Tab for Jupyter

1. In tmux, create a new tab by pressing `Ctrl + B`, then `c`.
2. Name the tab by pressing `Ctrl + B`, followed by `,` and entering the name (e.g., "jupyter").

---

## 4. Launch Jupyter Lab

Within the tmux session, launch Jupyter Lab without opening a browser:

~~~bash
jupyter lab --no-browser
~~~

> **Tip:** You can also specify a different port (e.g., `--port=8889`) if needed to avoid conflicts.

---

## 5. Access Jupyter Lab

After launching Jupyter, control-click the provided URL to access Jupyter Lab locally, typically at:

~~~bash
localhost:8888
~~~

If you’re forwarded to a different port (e.g., `8889`), follow the steps in **Section 6**.

---

## 6. Resolve Port Conflicts

If port `8888` is occupied and Jupyter defaults to a new port (e.g., `8889`), set up a new SSH session with the updated port forwarding:

~~~bash
ssh -L 8889:localhost:8889 <userid>@mualhpcp50.hpc.miamioh.edu
~~~

Use this link to open Jupyter in your browser, or use `tmux attach` to find the session.

If the Jupyter link has scrolled out of view, create a new tmux tab and type:

~~~bash
jupyter notebook list
~~~

---

## 7. Set Up a Personal Conda Environment

You may want to use your own environment instead of the base conda environment. To create and clone an environment:

~~~bash
conda create --name myenv --clone base
~~~

Then, install your environment as a kernel for Jupyter Lab:

~~~bash
python -m ipykernel install --user --name myenv
~~~

---

## 8. Reconnect to SSH and Tmux Session

If disconnected, re-establish the SSH connection with port forwarding:

~~~bash
ssh -L 8888:localhost:8888 <userid>@mualhpcp50.hpc.miamioh.edu
~~~

Reattach to the tmux session:

~~~bash
tmux attach
~~~

---

## 9. Use the Web-based NX Client (Optional)

For interactive tasks such as downloading large datasets (e.g., from Google Drive), connect via the NX Web Client for a graphical desktop interface.

Instructions for setting up NX are available in the project Slack channel.
