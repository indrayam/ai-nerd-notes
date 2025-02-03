# nvidia-smi

## Useful Commands

```bash
# NVIDIA System Management Interface
nvidia-smi

# Display list of GPUs
nvidia-smi --list-gpus
nvidia-smi -L

# Target a specific GPU
nvidia-smi --id=GPU-dd4789e0-8c31-2d71-3461-a6cbe3413ffb

# Process Stats
# Process statistics are displayed in scrolling format per sampling interval. This tool lists the statistics for all the compute and graphics processes running on each device.
nvidia-smi pmon

# More detailed information
nvidia-smi --help
nvidia-smi --help-query-gpu
nvidia-smi --query-gpu=compute_cap --format=csv
nvidia-smi --query-gpu=driver_version
nvidia-smi --query-gpu=driver_version --format=csv
nvidia-smi --query-gpu=count --format=csv
nvidia-smi --query-gpu=name --format=csv
nvidia-smi --query-gpu=uuid --format=csv
nvidia-smi --query-gpu=display_mode --format=csv
nvidia-smi --query-gpu=index --format=csv
nvidia-smi --query-gpu=vbios_version --format=csv
nvidia-smi --query-gpu=memory.total --format=csv
nvidia-smi --query-gpu=memory.reserved --format=csv
nvidia-smi --query-gpu=temperature.gpu --format=csv
nvidia-smi --query-gpu=temperature.memory --format=csv
nvidia-smi --query-gpu=power.management --format=csv


```
