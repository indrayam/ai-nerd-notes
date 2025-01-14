# llm CLI

## Useful commands

```bash
llm version --help
llm models
llm models default
llm --help
llm aliases
llm plugins --help
llm plugins
llm install -U llm-gpt4all
llm install -U llm-gguf
llm install -U llm-ollama
llm install -U llm-gemini
# To update the model
llm install -U llm-gemini
llm install -U llm-claude-3
# To update the model
llm install -U llm-claude-3
llm install -U llm-clip
llm install -U llm-groq
llm keys
llm keys path
llm keys set gemini
llm keys set openai
llm keys set claude
llm keys set groq
cat '/Users/anasharm/Library/Application Support/io.datasette.llm/keys.json'
llm aliases list --json
llm aliases path
llm aliases set 2-flash-think gemini-2.0-flash-thinking-exp-1219
```

## AI Model Invocations

```bash
curl -s https://www.nytimes.com/ | strip-tags .story-wrapper | ttok -t 4000 | llm --system 'summary bullet points'
curl -s 'https://en.wikipedia.org/wiki/Hyperion_(Simmons_novel)' | strip-tags .mw-body-content | ttok -t 4000 | llm --system 'Write a brief summary of the content'
curl -s 'https://en.wikipedia.org/wiki/The_Matrix' | strip-tags .mw-body-content | ttok -t 4000 | llm --system 'Write a brief summary of the content'
curl -s 'https://en.wikipedia.org/wiki/Dune_(novel)' | strip-tags .mw-body-content | ttok -t 4000 | llm --system 'Write a brief summary of the content'
```

```bash
llm -m 2-flash describe -a https://static.simonwillison.net/static/2024/pelicans.jpg
```

```bash
llm -m gemini-2.0-flash-thinking-exp-1219 "Generate an SVG of a pelican riding a bicycle"
llm -m 2-flash -a https://arxiv.org/pdf/1902.08318 "a bullet point list of the most unusual ideas"
llm -m 2-flash -a https://arxiv.org/pdf/2501.06425 "a bullet point list of the most unusual ideas"

```

```bash
llm -m gemini-2.0-flash-thinking-exp-1219 -a https://storage.googleapis.com/generativeai-downloads/images/geometry.png "What's the area of the overlapping region?"
```

```bash
llm -m groq-llama-3.3-70b 'A sassy name for a pet sasquatch'
llm -m 4o "Ten absurd names for an IT team that delivers DevOps services in an org"
llm -m groq-llama-3.3-70b "Ten absurd names for an IT team that delivers DevOps services in an org"
```

## AI Embeddings

```bash
llm embed-models
llm embed-models default 3-small
llm embed -m ada -c "Hello World"
llm embed -m 3-small -c "Hello World"
# Storing in collections
llm collections list
llm collection path
llm embed play-small test1 -c 'Hello, World' --store
llm embed play-small test2 -c 'It is nice to say hello to the world!' --store
llm collections list
llm similar nerd-notes -c 'algebra' | jq .
datasette '/Users/anasharm/Library/Application Support/io.datasette.llm/embeddings.db'

```

## AI Command-line invocations

```bash
llm cmd use ffmpeg to convert file.aac to mp3
llm cmd undo last git commit
llm cmd use jq to generate a new JSON from GitHub Issues API
```

## LLM Plugins

```bash
llm install -U llm-gpt4all
llm install -U llm-gemini
llm install -U llm-ollama
llm install -U llm-claude
llm install -U llm-claude-3
llm install -U llm-groq
# Refer to the llm CLI Setup page for specific ways to install llm-sentence-transformers (https://llm.datasette.io/en/stable/setup.html)
llm install -U llm-sentence-transformers
llm install -U llm-cmd
llm install -U llm-clip
#llm install -U llm-bedrock-anthropic
#llm install -U llm-bedrock-meta
```

```json
[
  {
    "name": "llm-cmd",
    "hooks": [
      "register_commands"
    ],
    "version": "0.2a0"
  },
  {
    "name": "llm-gemini",
    "hooks": [
      "register_embedding_models",
      "register_models"
    ],
    "version": "0.8"
  },
  {
    "name": "llm-sentence-transformers",
    "hooks": [
      "register_commands",
      "register_embedding_models"
    ],
    "version": "0.2"
  },
  {
    "name": "llm-groq",
    "hooks": [
      "register_models"
    ],
    "version": "0.6"
  },
  {
    "name": "llm-claude",
    "hooks": [
      "register_models"
    ],
    "version": "0.4.2"
  },
  {
    "name": "llm-ollama",
    "hooks": [
      "register_commands",
      "register_embedding_models",
      "register_models"
    ],
    "version": "0.8.1"
  },
  {
    "name": "llm-python",
    "hooks": [
      "register_commands"
    ],
    "version": "0.1"
  }
]
```
