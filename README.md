# hello-neural-networks
Repository to keep notebooks from Deep Learning A-Z 2024 course

## Setup
### Install Anaconda (Debian)
Refer: https://docs.anaconda.com/anaconda/install/linux/
1. Install dependent libraries
   ```sh
   apt-get install libgl1-mesa-glx libegl1-mesa libxrandr2 libxrandr2 libxss1 libxcursor1 libxcomposite1 libasound2 libxi6 libxtst6
   ```
2. To download the installer, open a terminal and use the following command, depending on your Linux architecture:
   ```sh
   # Replace <INSTALLER_VERSION> with the version of the installer file you want to download
   # For example, https://repo.anaconda.com/archive/Anaconda3-2023.09-0-Linux-x86_64.sh
   # All installers can be found at repo.anaconda.com/archive/
   curl -O https://repo.anaconda.com/archive/Anaconda3-<INSTALLER_VERSION>-Linux-x86_64.sh
   ```
3. To install, run the following command (Linux x86)
   ```sh
   # Include the bash command even if you aren't using the Bash shell
   # Replace ~/Downloads with the path to the installer file, if necessary
   # Replace <INSTALLER_VERSION> with the version of the installer file
   # For example, Anaconda3-2023.09-0-Linux-x86_64.sh
   bash ~/Downloads/Anaconda3-<INSTALLER_VERSION>-Linux-x86_64.sh
   ```
4. Initialize conda
   ```sh
   # Replace <PATH_TO_CONDA> with the path to your conda install
   source <PATH_TO_CONDA>/bin/activate
   conda init
   ```

### Setup Tenserflow environment in Anaconda
```sh
conda create -n tf-gpu tensorflow-gpu
conda activate tf-gpu
```

### Install dependent packages in Anaconda
_(tdqm is optional)_
```sh
pip install pandas matplotlib scikit-learn scipy tdqm
conda install -c conda-forge jupyterlab
```

## Run
### Activate Anaconda Tenserflow environment
```sh
conda activate tf-gpu
```
### Start Jupyter
```sh
jupyter notebook
```
