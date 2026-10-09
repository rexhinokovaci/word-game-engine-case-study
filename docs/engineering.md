# How it ships

- **CI and deploy pipelines.** Tests and a dependency gate run on every change, and the worker deploys from CI.
- **Dependency automation.** Dependabot updates are auto-merged only after they pass the gate.
- **Dictionary autodeploy.** The daily word batch is validated by a dictionary gate, then deployed with no manual step.
- **Security policy.** Secrets live only in CI, inputs are validated server-side, and words are filtered before storage.
- **Store growth tooling.** Scripted App Store and Play listing optimization in several languages.

## Stack

React Native · Expo · TypeScript · Cloudflare Workers · Durable Objects · Cloudflare Pages · RevenueCat · GitHub Actions · Dependabot
