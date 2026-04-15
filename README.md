# Social Media Caption Maker

A single-page web app that turns a pasted article into ready-to-post social media captions using a local LLM.

## What it does

- Users can paste any article and optional example captions to define their preferred tone/style
- Web app generates three outputs simultaneously:
  - **Long-form caption**: for Instagram, Facebook, and LinkedIn
  - **Short caption**: for Twitter/X, with a live 280-character counter
  - **20 ranked hashtags**: sorted from most to least popular, each clickable to copy
- Copy buttons on every output section for quick use

## API / Service used

**[Ollama](https://ollama.com/)**: a local LLM runtime that runs models on your own machine. The app calls Ollama's REST API at `http://localhost:11434/api/generate`. No cloud API key or internet connection is required once Ollama and a model are installed.

The default model is `gemma4:e2b`, but any model available in Ollama can be entered in the model field.

## How to run

### 1. Install Ollama

Download and install from [ollama.com](https://ollama.com/), then pull a model:

```bash
ollama pull gemma4:e2b
```

### 2. Start Ollama with browser access enabled

Ollama blocks cross-origin requests by default. Start it with:

```bash
# macOS / Linux
OLLAMA_ORIGINS=* ollama serve

# Windows — set the environment variable first, then start Ollama
set OLLAMA_ORIGINS=*
ollama serve
```

### 3. Open the app

Open `index.html` directly in your browser, **or** serve it locally to avoid any browser restrictions:

```bash
python -m http.server 8080
```

Then visit `http://localhost:8080`.

### 4. Use it

1. Enter your Ollama model name (default: `gemma4:e2b`)
2. (Optional) Paste 2–5 example captions to guide the style and tone
3. Paste your article text
4. Click **Generate Captions**
