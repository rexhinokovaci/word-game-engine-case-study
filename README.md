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

## Lessons learned

- **Give each room one owner.** Running every room in its own Durable Object removed race conditions between players without database locks.
- **Use AI where it's cheapest to be wrong.** Dictionary lookups handle the common answers quickly, cheaply and predictably. AI only judges the long tail of unusual ones.
- **Make the market a config file.** Treating language as configuration is what let the seventh market ship on the same engine instead of a fork.
- **Automate content, but gate it.** The daily dictionary pipeline only works because a quality gate decides what ships.
- **Write down deliberate trade-offs.** Room codes as the only access control is a conscious choice for a public party game, and it's documented as one.

## FAQ

### How do multiplayer rooms stay in sync?

Each room is a single Cloudflare Durable Object that holds the authoritative game state, timer and scoring. Players on iOS, Android and web connect to it over WebSockets.

### Do players need an account?

No. Players join with a room code. For a public party game that's a deliberate trade-off in favor of zero friction.

### How is AI used in the game?

Only as a fallback. Answers are checked against a curated per-language dictionary first, and AI helps with edge cases the dictionary doesn't cover. Offensive words are filtered server-side.

### How long does it take to launch a new language?

Days rather than months, because a new market is configuration plus a dictionary, not a fork of the code.

### Can you build a real-time multiplayer app or game for my business?

Yes. I'm a mobile app developer and DevOps engineer based in Tirana, Albania, building real-time apps on iOS, Android, web and the edge for clients across the Balkans and Europe. [Email me about your project](mailto:kovacirexhino@gmail.com?subject=Project%20inquiry).

## Read more

- [Architecture and key decisions](docs/architecture.md)
- [Delivery pipeline and stack](docs/engineering.md)

## Related case studies

- [Nearby Lens](https://github.com/rexhinokovaci/nearby-lens-case-study): smart-glasses detection over Bluetooth LE on iOS, watchOS, Android and Wear OS
- [Kush Jam Unë?](https://github.com/rexhinokovaci/kush-jam-une-case-study): Albanian party game with live content, subscriptions and ads
- [Balkans Quiz](https://github.com/rexhinokovaci/balkans-quiz-case-study): per-country trivia apps with Apple Watch, widgets and an automated question pipeline

## About the author

**Rexhino Kovaci** is a DevOps engineer, mobile app developer and AI engineer based in Tirana, Albania, and the founder of [Modex Apps](https://modex.al). He has 5+ years in DevOps, including work as a DevOps Engineer at Lufthansa Industry Solutions on Volkswagen AG projects, and holds Microsoft DevOps Engineer Expert, Azure Administrator Associate, Azure Developer Associate, HashiCorp Terraform Associate and New Relic Full-Stack Observability certifications. He builds for clients across the Balkans and Europe.

---

**Want something like this built for your business?** I build mobile apps, web apps and AI products end to end. [Email me about your project](mailto:kovacirexhino@gmail.com?subject=Project%20inquiry) · [Full profile](https://github.com/rexhinokovaci)

<sub>This case study is licensed under [CC BY 4.0](LICENSE). Product names and trademarks belong to their owners.</sub>
