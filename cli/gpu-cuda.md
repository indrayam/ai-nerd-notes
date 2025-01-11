# gpu

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