# cuda/gpu

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

## CUDA related additional software

```bash
# Installing collected packages: mpmath, threadpoolctl, sympy, scipy, safetensors, regex, Pillow, packaging, nvidia-nvtx-cu12, nvidia-nvjitlink-cu12, nvidia-nccl-cu12, nvidia-curand-cu12, nvidia-cufft-cu12, nvidia-cuda-runtime-cu12, nvidia-cuda-nvrtc-cu12, nvidia-cuda-cupti-cu12, nvidia-cublas-cu12, networkx, joblib, fsspec, filelock, scikit-learn, nvidia-cusparse-cu12, nvidia-cudnn-cu12, huggingface-hub, tokenizers, nvidia-cusolver-cu12, transformers, torch, sentence-transformers, llm-clip

# Successfully installed Pillow-11.1.0 filelock-3.16.1 fsspec-2024.12.0 huggingface-hub-0.27.1 joblib-1.4.2 llm-clip-0.1 mpmath-1.3.0 networkx-3.4.2 nvidia-cublas-cu12-12.4.5.8 nvidia-cuda-cupti-cu12-12.4.127 nvidia-cuda-nvrtc-cu12-12.4.127 nvidia-cuda-runtime-cu12-12.4.127 nvidia-cudnn-cu12-9.1.0.70 nvidia-cufft-cu12-11.2.1.3 nvidia-curand-cu12-10.3.5.147 nvidia-cusolver-cu12-11.6.1.9 nvidia-cusparse-cu12-12.3.1.170 nvidia-nccl-cu12-2.21.5 nvidia-nvjitlink-cu12-12.4.127 nvidia-nvtx-cu12-12.4.127 packaging-24.2 regex-2024.11.6 safetensors-0.5.2 scikit-learn-1.6.1 scipy-1.15.1 sentence-transformers-3.3.1 sympy-1.13.1 threadpoolctl-3.5.0 tokenizers-0.21.0 torch-2.5.1 transformers-4.48.0
```