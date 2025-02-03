# ollama

## Install


```bash
# On Linux
curl -fsSL https://ollama.com/install.sh | sh
# Use the same command to update

```

## Importing a Model

```bash
cd ~/src
hf download NousResearch/Hermes-3-Llama-3.1-8B --local-dir ./NousResearch_Hermes-3-Llama-3.1-8B
# ollama create hermes-3 --model ./NousResearch_Hermes-3-Llama-3.1-8B/ggml-model-q4_0.bin
# Create a Modelfile like the following
# FROM ./NousResearch_Hermes-3-Llama-3.1-8B

# TEMPLATE """{{ if .System }}<|im_start|>system
# {{ .System }}<|im_end|>{{ end }}
# <|im_start|>user
# {{ .Prompt }}<|im_end|>
# <|im_start|>assistant
# """

# PARAMETER stop <|start_header_id>|
# PARAMETER stop <|end_header_id>|
# PARAMETER stop <|eot_id>|
o create -f Modelfile NousResearch-Hermes-3-Llama-3.1-8B
o run --verbose NousResearch-Hermes-3-Llama-3.1-8B \
What would happen in a fight between a lion and a unicorn

# Quantize the model
o create -f Modelfile NousResearch-Hermes-3-Llama-3.1-8B:q4_0 --quantize q4_0
o run --verbose NousResearch-Hermes-3-Llama-3.1-8B:q4_0 \
What would happen in a fight between a lion and a unicorn
# Notice both the eval rate and the load duration is significantly faster than the full version
```

## Ollama Service

```bash
# If you need to look at the ollama service settings
sudo vim /etc/systemd/system/ollama.service

# You can add additional environment variables to the service file
# [Service]
# ExecStart=/usr/local/bin/ollama serve
# User=ollama
# Group=ollama
# Restart=always
# RestartSec=3
# Environment="OLLAMA_HOST=0.0.0.0"
# Environment="PATH=..."

sudo systemctl daemon-reload
sudo systemctl enable ollama
sudo systemctl stop ollama
sudo systemctl start ollama
sudo systemctl status ollama

```

## Download the Models

```bash
ollama --version
ollama --help
ollama list
ollama ls
ollama pull phi4
ollama pull mistral
ollama pull mistral-nemo
ollama pull llama3.2
ollama pull llama3.2-vision
ollama pull gemma
ollama pull llava
ollama show mistral
# ollama rm mistral
ollama list
ollama ps

```

## Run the models

```bash
ollama run llava
ollama run llava "What's in this image? /Users/anasharm/Downloads/cisco-catalyst.png"
ollama run llama3.2 "Create a very terse summary of this file: $(cat README.md)"
cd ~/.ollama/models/
```

## Invoke the API

```bash
curl -s http://localhost:11434/api/generate -d @generate-payload.json | jq .
curl -s http://localhost:11434/api/chat -d @chat-payload.json | jq .
# OR
curl -s http://localhost:11434/api/generate -d '{ "model": "llama3.2", "prompt": "Why is the sky blue?", "stream": false}' | jq .
```



