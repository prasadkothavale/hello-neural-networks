# hello-neural-networks
Repository to keep notebooks from Deep Learning A-Z 2024 course

## Setup with Anaconda
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
pip install pandas matplotlib scikit-learn scipy tdqm keras
conda install -c conda-forge jupyterlab
```

## Setup without Anaconda
### Install tenserflow (https://www.tensorflow.org/install/pip)

1. Verify gpu (or skip for cpu only)
   ```sh
   nvidia-smi
   ```

2. Create a virtual environment with venv
   ```sh
   python3 -m venv tf-gpu
   source tf-gpu/bin/activate
   ```

3. Install tensorflow (gpu)
   ```sh
   pip install --upgrade pip
   pip install tensorflow[and-cuda]
   ```
   or install tensorflow (cpu only)
   ```sh
   pip install tensorflow
   ```

4. Verify the installation
   - [cpu]
      ```sh
      python3 -c "import tensorflow as tf; print(tf.reduce_sum(tf.random.normal([1000, 1000])))"
      ```
   - [gpu]
      ```sh
      python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
      ```

5.  [GPU only] Virtual environment configuration
      
      Create symbolic links to NVIDIA shared libraries:
      ```sh
      pushd $(dirname $(python -c 'print(__import__("tensorflow").__file__)'))
      ln -svf ../nvidia/*/lib/*.so* .
      popd
      ```

      Create a symbolic link to ptxas:
      ```sh
      ln -sf $(find $(dirname $(dirname $(python -c "import nvidia.cuda_nvcc;         
      print(nvidia.cuda_nvcc.__file__)"))/*/bin/) -name ptxas -print -quit) $VIRTUAL_ENV/bin/ptxas
      ```

      Verify the GPU setup:
      ```sh
      python3 -c "import tensorflow as tf; print(tf.config.list_physical_devices('GPU'))"
      ```

### Install dependencies
```sh
pip install pandas matplotlib scikit-learn scipy tdqm keras
```
Either install Jupyter Lab or just Jupyter Notebook as per the requirement
```sh
pip install jupyterlab
```
or
```sh
pip install notebook
```

## Run with Anaconda
### Activate Anaconda Tenserflow environment
```sh
conda activate tf-gpu
```
### Start Jupyter Lab
```sh
jupyter lab
```
---
## Run without Anaconda
### Activate Tenserflow environment
```sh
source tf-gpu/bin/activate
```
### Start Jupyter Lab
```sh
jupyter lab
```
or
```sh
jupyter notebook
```