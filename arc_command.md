# HPC Commands (Short)

Replace `<cwl>` with your UBC CWL username and `<alloc-code>` with your allocation code. Run the "Laptop" commands on your own computer and the "Cluster" commands in a Jupyter terminal.

## 1. Transfer data

| Where | Command | What it does |
|---|---|---|
| Laptop | `tar -cf dataset.tar dataset_folder` | Packs the folder into one file. |
| Laptop | `sftp <cwl>@dtn.sockeye.arc.ubc.ca` | Opens a file-transfer session. |
| `sftp>` | `cd /arc/project/<alloc-code>` | Goes to your project storage. |
| `sftp>` | `mkdir my_project` | Creates a folder. |
| `sftp>` | `cd my_project` | Enters the folder. |
| `sftp>` | `put dataset.tar` | Uploads the file. |
| `sftp>` | `get <filename>` | Downloads the file to your computer (to the directory you open the terminal). |
| `sftp>` | `exit` | Closes the session. |

## 2. Unpack and show in JupyterLab

| Where | Command | What it does |
|---|---|---|
| Cluster | `cd /arc/project/<alloc-code>/my_project` | Goes to the uploaded folder. |
| Cluster | `tar -xf dataset.tar` | Unpacks the archive. |
| Cluster | `ls` | Confirms the files are there. |
| Cluster | `ln -s /arc/project/<alloc-code>/my_project ~/my_project` | Makes the folder appear in the JupyterLab file browser. |

## 3. Build the environment and kernel

| Where | Command | What it does |
|---|---|---|
| Cluster | `python --version` | Shows the Python version your environment must match. |
| Laptop | `ssh <cwl>@sockeye.arc.ubc.ca` | Logs in to the login node (not from a compute node). |
| Login node | `curl -sI https://pypi.org \| head -1` | Checks for internet access (an `HTTP` line means yes). |
| Login node | `python -m venv /arc/project/<alloc-code>/envs/myenv` | Creates the virtual environment. |
| Login node | `source /arc/project/<alloc-code>/envs/myenv/bin/activate` | Activates it. |
| Login node | `pip install --upgrade pip` | Updates pip. |
| Login node | `pip install --no-cache-dir <packages> ipykernel` | Installs your packages and the kernel helper. |
| Login node | `python -m ipykernel install --user --name myenv --display-name "Python (myenv)"` | Registers the Jupyter kernel. |

Then refresh JupyterLab and select **Python (myenv)** as the kernel.

## 4. Verify

| Where | Command | What it does |
|---|---|---|
| Notebook | `import sys; print(sys.executable)` | Should point into `envs/myenv`. |
