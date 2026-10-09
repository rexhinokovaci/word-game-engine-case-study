# Architecture

```mermaid
flowchart LR
  A[iOS / Android app<br/>React Native · Expo] -- WebSocket --> W
  B[Web client<br/>Cloudflare Pages] -- WebSocket --> W
  subgraph Edge[Cloudflare Workers]
    W[API worker] --> RD[Room Durable Object<br/>state · timer · scoring]
    W --> DU[Duel Durable Object]
    W --> LX[Lexicon Durable Object<br/>per-language dictionary]
    LX --> AI[AI validation<br/>edge cases only]
  end
  P[Daily dictionary pipeline] -->|gated PR → auto-deploy| LX
```

## Key decisions

| Decision | Why |
|---|---|
| One Durable Object per room | Each room has exactly one authoritative copy of game state, so there's no race between players and no database locks |
| Edge-hosted, no servers to manage | Low latency for players across Europe, and almost no ops work |
| Dictionary first, AI as fallback | Fast, cheap and predictable. AI handles only the long tail of unusual answers |
| Language as configuration | A new market costs days, not months |
| Room codes as the only access control | A public party game needs no accounts, and that's a deliberate, documented trade-off |
