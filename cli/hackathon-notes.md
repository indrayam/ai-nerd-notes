# Hackathon Demo Q2 2025 Edition

## Agenda
- Intro Using PowerPoint
- CLI
    - Locally Hosted Models
        - `ollama`
    - Cloud Hosted Models
        - `llm`
- 3 Concepts of Locally Hosted Models
    - Run it locally
        - Text to Text, Image to Text
    - Security and Privacy
        - No data leakage
    - Greater configurability
        - Custom Models
- 3 Concepts
    - Tokenization
    - Embeddings
        - Similarity tests
    - Language Models with multi-modality
        - Text to Text
        - Image to Text
- Interesting use cases
    - Semantic/Similarity Search
    - Sentiment Analysis
    - Summarize
    - Productivity boosts (Reduce toil)

## 1. Text Encoding

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

## 2. Embeddings

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

## 3. Models hosted locally (or LAN)

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

## 4. Models hosted in the Cloud

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
