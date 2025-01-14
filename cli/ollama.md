# ollama

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

