# cuda/gpu

## Install Nvidia Drivers

```bash
sudo apt update
sudo apt upgrade
# Understand which version of Ubuntu you are running
cat /etc/os-release
# Understand what Nvidia card you have
lspci | grep -i nvidia
# Install Ubuntu Drivers Common
sudo apt install ubuntu-drivers-common
# Look to see which drivers are recommended for your Nvidia card
sudo ubuntu-drivers devices
# Check if you already have the recommended driver installed
dpkg -l | grep nvidia-driver-550
# If not, install the recommended driver
sudo apt install nvidia-driver-550
# Reboot
sudo sutdown -r now
```

## Install CUDA Toolkit

```bash
# Search for CUDA download in Google
# Select the OS version and the CUDA version
# Follow the instructions on the screen which should look like these
wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2404/x86_64/cuda-ubuntu2404.pin
sudo mv cuda-ubuntu2404.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/12.8.0/local_installers/cuda-repo-ubuntu2404-12-8-local_12.8.0-570.86.10-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu2404-12-8-local_12.8.0-570.86.10-1_amd64.deb
sudo cp /var/cuda-repo-ubuntu2404-12-8-local/cuda-47045A0D-keyring.gpg /usr/share/keyrings/
sudo apt-get update
sudo apt-get -y install cuda-toolkit-12-8
# Update .zshrc (or .bashrc) with the following
export PATH=/usr/local/cuda-12/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-12/lib64:$LD_LIBRARY_PATH
# Reboot for nvidia-smi to show the CUDA version
sudo shutdown -r now
```

## Useful Commands

```bash
# Displays information about an NVIDIA graphics card, including its usage
nvidia-smi

# Finds the GPU model
lspci | grep -i vga

# Finds the installed video card and the driver in use
lspci -k | grep -EA3 'VGA|3D|Display'

# Displays the version of CUDA installed on the system
nvcc --version

# Runs the nvidia-smi command every two seconds to provide updated GPU
# utilization and memory
watch -n 2 nvidia-smi --id=1

# You can also use the lshw command to list the hardware installed on a 
# Linux computer. It reports a variety of types, too---not just PCI
# hardware.

# To tell it to report on the graphics cards it finds, we'll use the -C
# (class) option and pass the "display" modifier.
sudo lshw -numeric -C display

```

## CUDA/MPS test

- CUDA Hello on Linux

```python
import torch
import torchaudio
import torchvision

print(torch.__version__)
print(torchvision.__version__)
print(torchaudio.__version__)
device = "cuda" if torch.cuda.is_available() else "cpu"
print(device)
```

- MPS Hello on Mac

```python
import torch

if torch.backends.mps.is_available():
    mps_device = torch.device("mps")
    x = torch.ones(1, device=mps_device)
    print(x)
else:
    print("MPS device not found.")
```