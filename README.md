# OCR Obsidian
Send pictures of your notes to a Telegram bot, and it will extract the text, convert it to Markdown, suggest tags to organize it in the context of your other notes, and save it to a specified vault.

## Example use case
You upload pictures of your class notes to have them digitized into an obsidian vault. This lets you have the best of both worlds: both digital and physical notes. 

## What I learned
This project taught me how to orchestrate APIs and LLMs for more advanced (in the higher-level sense) functionality. This is one of the most technically complex pieces of software I've written. It combines user input via Telegram, Ollama API integration for vision capabilities, as well as disk reading and file parsing. 

# Ollama integration
This app is designed for use with Ollama. Before using, make sure you have ollama installed on a capable machine with a vision model downloaded, as well as Ollama exposed on your network. 

# AI Endpoint
> (Found in the [config.toml](config.example.toml))

The AI endpoint is designed to point to an Ollama endpoint. For more information, check out the [Ollama docs](https://docs.ollama.com/api/introduction/)

# Installation

## Prerequisites
- Python 3.10+
- An Ollama instance (local or on your network) with a vision-capable model pulled (e.g. `qwen2.5vl:3b`)
- A Telegram API ID/hash and bot token (get these from [my.telegram.org](https://my.telegram.org) and [@BotFather](https://t.me/BotFather))

## Steps
1. Clone the repository and enter the project directory:
   ```bash
   git clone https://github.com/daneohr/ocr-obsidian.git
   cd ocr-obsidian
   ```
2. (Optional but recommended) Create and activate a virtual environment:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Copy the example env file and fill in your Telegram credentials:
   ```bash
   cp .env.example .env
   ```
   Then edit `.env` and set `API_ID`, `API_HASH`, and `BOT_TOKEN`.
5. Copy the example config file and configure your AI endpoint and Obsidian vault(s):
   ```bash
   cp config.example.toml config.toml
   ```
   Then edit `config.toml` — set `ai.endpoint`/`ai.model` to match your Ollama setup, and `vaults.base_path` to the folder where your Obsidian vaults live.
6. Run the bot:
   ```bash
   python telegram_bot.py
   ```
