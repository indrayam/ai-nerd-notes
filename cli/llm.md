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
llm install llm-gpt4all
llm install llm-gguf
llm install llm-ollama
llm install llm-gemini
# To update the model
llm install -U llm-gemini
llm install llm-claude-3
# To update the model
llm install -U llm-claude-3
llm install llm-bedrock
llm install llm-groq
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
```

```bash
llm -m 2-flash describe -a https://static.simonwillison.net/static/2024/pelicans.jpg
```

```bash
llm -m gemini-2.0-flash-thinking-exp-1219 "Generate an SVG of a pelican riding a bicycle"
llm -m 2-flash -a https://arxiv.org/pdf/1902.08318 "a bullet point list of the most unusual ideas"
```

```bash
llm -m gemini-2.0-flash-thinking-exp-1219 -a https://storage.googleapis.com/generativeai-downloads/images/geometry.png "What's the area of the overlapping region?"
```

```bash
llm -m groq-llama-3.3-70b 'A sassy name for a pet sasquatch'
```

