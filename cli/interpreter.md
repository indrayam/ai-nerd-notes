# Open Interpreter

- [Source](https://github.com/openinterpreter/open-interpreter)
Open Interpreter lets LLMs run code (Python, Javascript, Shell, and more) locally. You can chat with Open Interpreter through a ChatGPT-like interface in your terminal by running $ interpreter after installing.

This provides a natural-language interface to your computer's general-purpose capabilities:

Create and edit photos, videos, PDFs, etc.
Control a Chrome browser to perform research
Plot, clean, and analyze large datasets
...etc.

## Useful Commands

```bash 
# This command failed to install
uv tool install open-interpreter
# While this one worked. Guess they are seriously working on the development branch to get ready for 1.0.0 release
uv tool install git+https://github.com/OpenInterpreter/open-interpreter.git@development
interpreter --version
```