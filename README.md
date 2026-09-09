# DeepSeek Local Chat

A single-file, no-build chat UI for a [DeepSeek](https://www.deepseek.com/) model running locally through [Ollama](https://ollama.com). This repo is meant to be hosted on GitHub Pages, but every chat request still goes straight from your browser to Ollama on your own machine — nothing passes through GitHub or any other server.

**This only works when you open the page from a device that has Ollama running.** GitHub Pages just serves the static HTML; it can't run the model itself. If someone else opens the link, they'll see the UI but the status dot will stay red, since they don't have your Ollama listening on `localhost`.

## One-time setup

1. Install Ollama: https://ollama.com/download
2. Pull a model sized for your machine:
   ```
   ollama pull deepseek-r1:1.5b
   ```
   (`deepseek-r1:7b` is smarter but slower on CPU-only machines.)
3. Allow this page's origin to call your local Ollama. Set `OLLAMA_ORIGINS` to the page's exact origin before starting Ollama:

   **Windows (PowerShell)**
   ```powershell
   $env:OLLAMA_ORIGINS="https://hemantramphul.github.io"
   ollama serve
   ```

   **macOS / Linux**
   ```bash
   OLLAMA_ORIGINS="https://hemantramphul.github.io" ollama serve
   ```

   If Ollama is already running as a background service, stop it first (Windows: `taskkill /IM ollama.exe /F`; macOS: quit it from the menu bar) then run the command above so the new origin takes effect.

## Use it

Open https://hemantramphul.github.io/ramz-ai/ with Ollama running. The status dot turns teal once it connects. Click the gear icon to change the address or model — e.g. point it at a bigger local model, or later at a cloud box running a larger model, without touching the code.
