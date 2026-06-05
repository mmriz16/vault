# Polymarket Trading Bot

Repo: [MrFadiAi/Polymarket-bot](https://github.com/MrFadiAi/Polymarket-bot)
Stars: 124 ⭐
Bahasa: TypeScript
License: MIT

## Apa ini
Bot trading otomatis buat Polymarket (prediction market). Pake SDK `@catalyst-team/poly-sdk` yang wrapping official Polymarket API.

## 4 Strategies
1. **Arbitrage** — profit dari perbedaan harga YES + NO < $1.00
2. **DipArb** — beli saat panic sell >15% dalam 3 detik
3. **Smart Money** — copy trade dari trader top leaderboard
4. **Direct Trading** — manual tools (FOK, Sniper)

## Kualitas Code: 7/10
✅ Clean TypeScript, service separation, rate limiter, caching
✅ Pake official Polymarket API
✅ Risk management 4 layer
❌ Bukan bot siap jalan — lebih ke SDK wrapper
❌ Dry run = basic simulation
❌ Ethers v5 (bukan v6)

## Notes
- Butuh private key Polymarket wallet — risk tinggi
- Jalan di local machine (Node.js 18+)
- Ada dashboard UI
- Start with DRY_RUN=true

## Streambert
Repo: [truelockmc/streambert](https://github.com/truelockmc/streambert)
Stars: 5.100 ⭐
Bahasa: JavaScript (Electron + React + Vite)
License: GPL-3.0

## Apa ini
Desktop app buat streaming + download movie, TV series, anime. Sumber dari VidSrc/Videasy/Vidking (piracy grey area).

## Streaming Sources
| Source | URL | Default |
|--------|-----|---------|
| Vidking | vidking.net/embed/movie/{id} | ✅ Default non-anime |
| Videasy | player.videasy.net/movie/{id} | Partial |
| VidSrc | vsembed.su/embed/movie/{id} | Partial (butuh intercept) |
| AllManga | allmanga.to | ✅ Khusus anime |

## Cara Kerja
1. Cari TMDB ID → 2. Buka embed di webview → 3. Intercept .m3u8 → 4. Play

## Catatan
- Gak host content sendiri — scraping dari situs pihak ketiga
- Built-in ad blocking via Electron session filter
- Download pake ffmpeg + vid-dl-cli
- Butuh TMDB API key (gratis)
- Gak ada subtitle Indonesian
