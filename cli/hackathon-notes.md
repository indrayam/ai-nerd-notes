# Hackathon Demo Q2 2025 Edition

## My Setup
- **Office Laptop:** 16" MacBook M1 Pro running Sequoia 15.1.1 with 16 GB RAM and 500 GB HDD
- **Homelab (aka The Beast):** Custom-built Tower with 13th Gen Intel i9-13900KF 24 Core Processor, Nvidia GeForce RTX 4090, 128 GB RAM, 4 TB HDD running Ubuntu 24.04.1 LTS
- **AI-centric CLI Tools:** 
    - `llm`
    - `ttok`
    - `ollama`
## Agenda
- [Intro PowerPoint Deck](https://cisco.sharepoint.com/:p:/r/sites/InternalEDaaS/Shared%20Documents/EDaaS%20Architecture/FY24/2025-01-17-EDaaS-Hackathon-Taming-AI-with-CLI/2025-01-16-Taming-17527-with-110817-Final.pptx?d=w3ec52dc4e38943649e2862b4acbbd29e&csf=1&web=1&e=JfCy7E)
- CLI
    - Locally Hosted Models
        - `ollama`
    - Cloud Hosted Models
        - `llm`
- 2 Key Concepts
    - Tokenization
    - Embeddings
- Locally Hosted Models
- Cloud Hosted Models
- Interesting use cases
    - Semantic/Similarity Search
    - Sentiment Analysis
    - Summarize
    - Productivity boosts (Reduce toil)

## Key Concept: Text Encoding

- CLI used: `ttok`

```bash
ttok Hello World -m gpt-4o
ttok Hello World -m gpt-4o --encode # Use it for decoding
ttok Hello World -m gpt-4o --tokens # Discuss the space
ttok 13225 5922 --decode -m gpt-4o # Use the PowerPoint number
ttok 175727 --decode # Oops
ttok 175727 --decode -m gpt-4o
ttok స్త్రీ
ttok స్త్రీ -m gpt2
ttok స్త్రీ -m gpt-4o
```

## Key Concept: Embeddings

- CLI used: `llm`

```bash
llm embed-models list
llm embed-models default
llm embed-models default mxbai-embed-large
llm embed -m 3-small -c "Hello World" #1536 dimensions
llm embed -c "Hello World" #1024 dimensions
# Storing in collections
llm collections list
llm collection path
llm embed play-small test1 -c 'Hello, World' --store
llm embed play-small test2 -c 'It is nice to say hello to the world!' --store
llm embed play-small test3 -c 'Not having a good day' --store
# Use select id, llm_embed_decode(embedding) from embeddings in datasette
llm similar play-small test1
llm similar play-small test3
```

## Models hosted locally (or LAN)

- CLI used: `ollama`

```bash
o ls
o run llama3.2 
# "What is your name?"
# What is the age of the Universe?
o run anand-llama 
# "What is your name?"
# What is the age of the Universe?
curl -s http://localhost:11434/api/generate -d @generate-payload.json | jq .
```

## Models hosted in the Cloud

- CLI used: `llm`

```bash
# Basic Text Generation
llm -m 4o "Ten absurd names for an IT team that delivers DevOps services in an org"

# Basic Image to text generation
llm -m 2-flash describe -a https://static.simonwillison.net/static/2024/pelicans.jpg
llm -m 4o "Can you help me better understand what the command shown in the image above does" -a https://us-east-1-anand-files.s3.us-east-1.amazonaws.com/play/mac-keyboard-settings.jpg

# Advanced Text Generation
## Summarize Nerdy Stuff
llm -m 2-flash -a https://arxiv.org/pdf/1902.08318 "a bullet point list of the most unusual ideas"
llm -m 2-flash -a https://arxiv.org/pdf/2501.06425 "a bullet point list of the most unusual ideas"
llm -m 2-flash -a https://arxiv.org/pdf/2501.00663 "a bullet point list of the most unusual ideas"
## Summarize Long Articles
curl -s 'https://en.wikipedia.org/wiki/Hyperion_(Simmons_novel)' | strip-tags .mw-body-content | ttok -t 4000 | llm --system 'Write a brief summary of the content'
curl -s 'https://en.wikipedia.org/wiki/The_Matrix' | strip-tags .mw-body-content | ttok -t 4000 | llm --system 'Write a brief summary of the content'
curl -s 'https://en.wikipedia.org/wiki/Dune_(novel)' | strip-tags .mw-body-content | ttok -t 4000 | llm --system 'Write a brief summary of the content'
# Unix Pipe magic to summarize NY Times
curl -s https://www.nytimes.com/ | strip-tags .story-wrapper | ttok -t 4000 | llm --system 'summary bullet points'

# Commands
llm cmd undo last git commit
llm cmd use ffmpeg to convert file.aac to mp3
curl -s https://api.github.com/repos/simonw/datasette/issues | llm jq 'count by user.login, top 3'
```
