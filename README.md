# OnyxLock: SoSoValue Wave 3

A browser based, zero install web build of OnyxLock, focused on live crypto market data, trading tools, and an AI market assistant. Built for SoSoValue Buildathon Wave 3.

**Live demo:** https://onyxcapitalweb.netlify.app/
**Video walkthrough:** https://youtu.be/gkLFuicjyJQ

No install, no clone, no setup. Open the link and every feature below is live and testable in under a minute.

## Why this wave is scoped the way it is

OnyxLock's original submission combined two categories of feature:

* **OS level security:** AES 256 encryption, intrusion detection via webcam, system level monitoring
* **Market facing tools:** signals, trading simulation, live data, an AI advisor

The single most common piece of feedback across Wave 2 judges was accessibility: a Windows desktop app is hard to evaluate without cloning a repo and running it locally. Wave 3 answers that directly with a build anyone can open in a browser, on any device, with nothing to install.

The security suite is intentionally not part of this build, and won't be ported here. A browser sandbox has no access to the file system, webcam, or OS level processes that layer depends on. Porting it to the web wouldn't produce a lighter version of the feature, it would produce a different, weaker feature pretending to be the same one. Rather than fake that in JavaScript to satisfy a checklist, this wave ships the half of OnyxLock that is honestly a web product, and does it without cutting corners. The security suite and self learning signal engine remain part of OnyxLock's desktop product, where they belong.

## What's live in this build

| Feature | Description |
|---|---|
| **Price Ticker** | Real time prices across 500 coins: 24h change, market cap, volume |
| **Currency Calculator** | Convert between top cryptocurrencies and 20 world currencies, including NGN |
| **Trading Interface** | Order book, live price chart, funding rate, demo wallet |
| **Demo Wallet** | Paper trading, clearly labeled as simulated, $10,000 USDC starting balance |
| **Trade Journal** | Position history and trade by trade analysis |
| **Zeal AI** | Market and portfolio assistant. Answers questions on sentiment, funding rates, coin fundamentals, and the user's own journal and positions |
| **Market Intel** | Recent trades feed and market pulse |

Every feature above runs against live data pulled client side. Nothing is mocked for demo purposes.

## Tech stack

* **Vanilla JS + HTML/CSS:** self contained, single file architecture (no framework runtime required to load)
* **Live data sources:**
  * [CoinGecko](https://www.coingecko.com/en/api): price, market cap, volume
  * Binance Futures API: funding rate data
  * [SoSoValue](https://sosovalue.com): market signal data
  * [alternative.me](https://alternative.me/crypto/fear-and-greed-index/): Fear and Greed Index
  * open.er-api.com: fiat exchange rates
  * Groq: LLM backend for Zeal AI
  * Custom backend (`onyxlockapi.onrender.com`): supplementary market data

## Architecture note

This build is deliberately packaged as a single self contained `index.html`. There is no build step required to run it, no bundler, no dependency install. This was a direct design choice for Wave 3: judges can open the file or the live link and see the entire working product with zero friction, matching the accessibility standard set by the feedback in Wave 2.

## Running locally

No build tools required.

```bash
git clone <this repo>
cd <this repo>
# open index.html directly in a browser, or serve it:
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Roadmap

* Continued expansion of Zeal AI's market analysis capabilities
* Additional live data integrations
* The OS level security suite (encryption, intrusion detection) continues development as part of the OnyxLock desktop product line, separate from this web build

## Links

* **Live demo:** https://onyxcapitalweb.netlify.app/
* **Video walkthrough:** https://youtu.be/gkLFuicjyJQ

Built by Onyx Capital for the SoSoValue Buildathon.
