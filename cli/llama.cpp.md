# llama.cpp

## Installation

On Mac:

```bash
brew install llama.cpp
# Set the LLAMA_CACHE environment variable to a directory where you want to store the models
```

On Linux:
```bash
# No need to set LLAMA_CACHE on Linux
{
cd $HOME/src
rm -rf llama.cpp
sudo rm -rf /usr/local/llama.cpp
sudo apt install cmake
sudo apt install ninja-build
sudo apt-get install libcurl4-openssl-dev
sudo apt install libopenblas-dev libatlas-base-dev
git clone https://github.com/ggerganov/llama.cpp
cd llama.cpp
cmake -B build -DGGML_BLAS=ON -DGGML_BLAS_VENDOR=OpenBLAS -DGGML_CUDA=ON -DBUILD_SHARED_LIBS=OFF -DLLAMA_CURL=ON
cmake --build build --config Release -j 8
cd $HOME/src
sudo mv llama.cpp/ /usr/local/
}
```

## Running Models

Automatically Download the model from Huggingface:

```bash
# Non-interactive
llama-cli \
  --hf-repo "unsloth/DeepSeek-R1-Distill-Llama-8B-GGUF" \
  --hf-file DeepSeek-R1-Distill-Llama-8B-Q4_K_M.gguf \
  --threads 16 \
  --cache-type-k q8_0 \
  --prompt '<｜User｜>What is 1+1?<｜Assistant｜>' \
  -no-cnv


# Interactive
```bash
llama-cli --color -b 512 \
--ctx-size 8192 \
--temp 0 \
--top-k 40 \
--top-p 0.95 \
-hf unsloth/DeepSeek-R1-Distill-Qwen-7B-GGUF:Q4_K_M \
-cnv
```