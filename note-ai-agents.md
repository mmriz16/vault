---
type: Note
---
# AI Agents — Catatan

## Apa itu AI Agent
AI Agent = LLM + tools + memory. Bukan cuma chatbot — bisa execute command, baca file, manage server, dll.

## Jenis Agent Framework

| Framework | Bahasa | Kelebihan |
|-----------|--------|-----------|
| **Hermes Agent** | Python | Multi-platform (Telegram, Discord, CLI), plugin system, cron, skills |
| **Claude Code** | TypeScript | Bagus buat coding, ACP protocol |
| **Codex CLI** | TypeScript | Dari OpenAI, CLI-native, agent loop |
| **LangChain** | Python | Paling mature, banyak integration |
| **CrewAI** | Python | Multi-agent orchestration |
| **AutoGPT** | Python | Autonomous goal-oriented |

## Hermes Agent (yg kita pake)
- Jalan di server Oracle Linux
- Platform: Telegram, CLI, API server
- Tools: terminal, baca/tulis file, cron, search, browser
- Extension: plugins, skills, MCP servers
- Skill: reusable instructions buat task tertentu
- Cron: scheduled jobs (misal: daily update JKT48)

## MCP (Model Context Protocol)
- Protocol standar dari Anthropic buat AI ↔ tools communication
- Server MCP: provide tools ke AI client
- Client MCP: pake tools dari server
- Contoh: gue bisa connect ke MCP server database, API, dll
- Alternatif: OpenAI Function Calling, tapi MCP lebih universal

## Local LLM vs Cloud
- **Cloud**: OpenAI, Claude, Gemini — cepet, akurat, tapi bayar per token
- **Local**: llama.cpp, Ollama, vLLM — gratis, privacy, tapi perlu GPU/CPU kuat
- Kita pake **DeepSeek V4 Flash** via OpenRouter — murah ($0.06/M input tokens)
