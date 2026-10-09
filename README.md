# Word game engine: case study

**One real-time multiplayer engine, shipped as 7 localized games** of the classic "Country, City, River" family.

| Game | Market | Link |
|---|---|---|
| Shtet·Qytet | Albania | [play](https://shtet-qytet.pages.dev) |
| Χώρα·Πόλη | Greece | [play](https://hora-poli.pages.dev) |
| Stadt·Land·Fluss | Germany | [play](https://stadt-land-fluss-67w.pages.dev) |
| Nomi·Cose·Città | Italy | [play](https://nomi-cose-citta.pages.dev) |
| Država·Grad | Balkans (BCS) | [play](https://drzava-grad.pages.dev) |
| Țară·Oraș | Romania | [play](https://tara-oras-e8g.pages.dev) |
| By·Land·Flod | Denmark | |

> Source code is private. This repo documents what was built and how. Ask for a live walkthrough of the real codebase.

## What I built

- **Live multiplayer rooms** with join codes, synced rounds and scoring, over WebSockets on the edge.
- **Solo and duel modes** so a player can play alone at any time.
- **Answer validation** against a curated dictionary for each language, with AI assistance for edge cases and server-side filtering of offensive words.
- **Self-updating dictionaries.** A daily automated pipeline proposes new words, quality gates check them, and accepted batches deploy themselves.
- **Monetization.** Subscriptions through RevenueCat on iOS and Android.

## Results

- Adding a new market means configuring a language, not forking the code. The seventh market shipped on the same engine.
- Dictionaries grow every day with no manual work.

## Read more

- [Architecture and key decisions](docs/architecture.md)

---

**Want something like this built for your business?** I build mobile apps, web apps and AI products end to end. [Email me about your project](mailto:kovacirexhino@gmail.com?subject=Project%20inquiry) · [Full profile](https://github.com/rexhinokovaci)
