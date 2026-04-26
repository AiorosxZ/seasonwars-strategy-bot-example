# SeasonWars Dev Kit — Example #2: Strategy Bot

> Compare all 12 burn strategies in real-time using on-chain simulation.

Find the optimal burn decision before committing capital —  
in under 30 minutes, using only on-chain data.

Example: the difference between COLD and HOT burns  
is +20% efficiency — invisible without simulation.

→ [Live demo](https://aiorosxz.github.io/seasonwars-strategy-bot-example)  
→ Open index.html  
→ Enter an amount → compare all 12 strategies instantly  

This repo is part of the **SeasonWars Dev Kit**.  
[← Example #1: Burn Tracker](https://github.com/AiorosxZ/seasonwars-burn-tracker-example)

---

## ⚡ What this bot does

Calls `quoteBurn()` for all 12 ZOD signs simultaneously  
and ranks them by expected burn points.

```js
for (let sign = 0; sign < 12; sign++) {
  points[sign] = await contract.quoteBurn(cycleId, user, sign, amount);
}
// → ranked list, best strategy highlighted
```

**This is the core insight:**  
SeasonWars has no dominant strategy.  
The optimal burn depends on the current cycle, timing, and your position.  
→ This is why simulation matters before every decision.

---

## 🎯 What makes this interesting

- COLD token → ×1.2 burn bonus (+20%)
- OPPOSITE token → ×1.1 burn bonus (+10%)
- HOT token → ×1.0 (no burn bonus — better to stake at 8% APY)
- Clan bonus → up to ×1.05 early season (first 7 days)
- NFTs → additional multipliers (not included in this bot)

**This bot covers the base layer.**  
The deeper layers (NFTs, clan rewards, long-term positioning)  
are the next frontier for builders.

---

## 🔑 Core primitive: `quoteBurn()`

```js
const points = await contract.quoteBurn(
  cycleId,
  userAddress,
  zodSign,  // 0=Aries ... 11=Pisces
  amount
);
// → expected burn points before you commit
```

This is what separates SeasonWars from standard DeFi:  
you can simulate outcomes before acting.

---

## 🔄 What the protocol exposes

**Views used in this bot**
- `getCurrentSigns()` → hot, cold, opposite
- `quoteBurn(cycleId, player, zodSign, amount)` → simulate

**For more primitives → [`INTEGRATION.md`](https://github.com/AiorosxZ/seasonwars-burn-tracker-example/blob/main/INTEGRATION.md)**

---

## 🔗 Contracts (Sepolia Testnet)

| Contract | Address |
|---|---|
| SeasonWars V2.3 | [`0x5598...2fc8`](https://sepolia.etherscan.io/address/0x5598778158a66d376bd96243FC6bc27316fD2fc8) |
| xZOD | [`0x017f...9D2f`](https://sepolia.etherscan.io/address/0x017f4333Aa7e83fA42d119d5489c41e3648c9D2f) |

---

## 🛠 Build your own

Extend this bot:
- Add wallet connection → personalized ranking
- Add NFT bonuses → deeper simulation
- Automate decisions → full strategy agent
- Add historical data → pattern recognition

→ Full integration guide: [`INTEGRATION.md`](https://github.com/AiorosxZ/seasonwars-burn-tracker-example/blob/main/INTEGRATION.md)

---

## 🧠 Mental model

You are not optimizing yield.  
You are competing under constraints.

SeasonWars Dev Kit:
- **Example #1** — Observe: [Burn Tracker](https://github.com/AiorosxZ/seasonwars-burn-tracker-example)
- **Example #2** — Decide: Strategy Bot ← you are here
- **Next** — Automate

---

Part of the **xZod Network** ecosystem.

SeasonWars is the first step toward a new class of  
on-chain strategy applications.

[xzod.io](https://xzod.io) ·
[Whitepaper](https://xzod.io/whitepaper) ·
[github.com/AiorosxZ/xzod-contracts](https://github.com/AiorosxZ/xzod-contracts)

*"In Zod we trust."* 🔥
