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

```
