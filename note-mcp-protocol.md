# MCP Protocol — Research

## Apa itu MCP?
MCP = Model Context Protocol. Protocol standar dari Anthropic buat **AI agent ↔ tools/server** komunikasi.

Bayangin MCP kaya **USB-C buat AI** — satu protocol universal yang connect AI ke berbagai tools, database, API.

## Arsitektur

```
┌─────────────┐      MCP Protocol      ┌──────────────┐
│  AI Client   │ ◄──────────────────► │  MCP Server   │
│  (Hermes,    │    JSON-RPC over      │  (DB, API,   │
│   Claude,    │    stdio / WebSocket   │   Filesystem)│
│   Codex)     │                        └──────────────┘
└─────────────┘
```

## Tools
MCP Server nge-expose **tools** yang bisa dipanggil AI Client:
- `read_file(path)` — baca file
- `query_database(sql)` — query SQL
- `search_web(query)` — cari internet
- `send_email(to, subject)` — kirim email

## Bedanya sama Function Calling OpenAI?
| OpenAI Function Calling | MCP |
|------------------------|-----|
| Built-in OpenAI API | Protocol standar (siapapun bisa implement) |
| Cuma jalan di OpenAI | Bisa jalan di Claude, Gemini, Hermes, dll |
| Define function di request | Server terpisah, bisa di-share |
| Gak ada standard discovery | Ada `list_tools()` built-in |

## MCP Server di Hermes
Hermes Agent support MCP native — tinggal config di `config.yaml`:

```yaml
mcp_servers:
  filesystem:
    command: npx
    args: ["@modelcontextprotocol/server-filesystem", "/path"]
  github:
    command: npx
    args: ["@modelcontextprotocol/server-github"]
```

## Contoh MCP Server yang Ada
- **Filesystem** — baca/tulis file
- **GitHub** — manage repo, issues, PRs
- **PostgreSQL** — query database
- **SQLite** — query SQLite
- **Puppeteer** — browser automation
- **Brave Search** — web search
- **Context7** — library documentation search (yang kita pake)

## MCP di Project Kita
Kita pake Context7 MCP server buat ngecek dokumentasi library real-time. Ini berguna banget pas gue research code.

Kedepan bisa add MCP server buat:
- **NocoDB MCP** — query langsung tanpa REST API
- **JKT48 database MCP** — data member, live streams
- **Monitoring MCP** — status server, disk usage
