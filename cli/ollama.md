# ollama

# Useful Commands

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

Run the models

```bash
ollama run llava
ollama run llava "What's in this image? /Users/anasharm/Downloads/cisco-catalyst.png"
ollama run llama3.2 "Summarize this file: $(cat jq.md)"
cd ~/.ollama/models/
```