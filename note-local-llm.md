---
type: Note
---
# Local LLMs — Research Notes

## Kenapa pake local?
- Gratis (gak bayar per token)
- Privacy (data gak keluar server)
- Latency rendah (gak perlu network trip)
- Bisa offline

## Metrik Penting
- **t/s** — tokens per second (throughput)
- **TTFT** — time to first token (latency)
- **Context window** — max input length
- **Quantization** — GGUF Q4/Q5/Q8, AWQ, GPTQ (ngecilin model size)

## Software

| Software | Backend | Kelebihan |
|----------|---------|-----------|
| **llama.cpp** | C/C++ | Paling ringan, support GGUF, CUDA/CPU |
| **Ollama** | llama.cpp wrapper | Gampang pakenya, `ollama run`, API OpenAI-compatible |
| **vLLM** | Python/C++ | High-throughput, PagedAttention, production-grade |
| **LM Studio** | llama.cpp wrapper | GUI desktop, gampang download model |

## Model Populer (Juni 2026)

### Kecil (< 10B)
| Model | Size | Kebolehan |
|-------|------|-----------|
| Qwen3 4B | 2.5GB Q4 | Coding + reasoning, ringan |
| Phi-4 7B | 4GB Q4 | Microsoft, bagus buat coding |
| Llama 4 Scout 8B | 5GB Q4 | Meta, 1M context window |
| DeepSeek-V4 Lite | 8B param | Mirip DeepSeek V4 tapi kecil |

### Sedang (10B-30B)
| Model | Size | Kebolehan |
|-------|------|-----------|
| Qwen3 14B | 8GB Q4 | Strong reasoning, coding |
| Mistral Small 3.1 24B | 14GB Q4 | Multilingual, instruction following |
| Llama 4 Maverick 17B | 10GB Q4 | MoE, efisien |

### Besar (30B+)
| Model | Size | Kebolehan |
|-------|------|-----------|
| DeepSeek V4 Flash | ~80B MoE | Yang kita pake via OpenRouter |
| Qwen3 235B | ~130GB Q4 | Butuh multi-GPU |
| Llama 4 Behemoth | 288B MoE | Butuh cluster |

## Setup Ollama di Server
```bash
curl -fsSL https://ollama.com/install.sh | sh
ollama pull qwen3:4b
ollama run qwen3:4b
# API: http://localhost:11434/v1
```

## Kita pake apa?
Sekarang pake **DeepSeek V4 Flash via OpenRouter** — gak perlu GPU, bayar $0.06/M input. Kalo mau local, bisa mulai dari Qwen3 14B (butuh ~12GB RAM).
