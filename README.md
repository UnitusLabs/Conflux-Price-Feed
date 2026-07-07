# Conflux eSpace Price Feed Dashboard

A live dashboard for the Pyth-compatible price oracle from
[conflux-fans/oracle-contracts](https://github.com/conflux-fans/oracle-contracts),
tracking all supported price feeds (BTC, ETH, CFX, BNB, USDT, USDC, AxCNH vs USD)
on Conflux eSpace.

- Reads prices on-chain via batched `eth_call` to `getPriceUnsafe(bytes32)` on the
  oracle proxy (mainnet `0x5286BD91e2C79fE066926a15193C7e531bBF6750`), with public
  RPC endpoint fallback.
- Auto-refreshes every 30 seconds; feeds update on-chain every hour.
- Freshness badges (Fresh / Delayed / Stale), confidence intervals, mainnet/testnet
  toggle, and a detail table with copyable feed IDs.
- Single static `index.html` — no build step, no dependencies.

## Run locally

Open `index.html` in a browser, or serve the directory:

```sh
python3 -m http.server 4173
```

## Deploy

Any static host works. On [Vercel](https://vercel.com), import this repo with
framework preset **Other** and no build command — `index.html` at the repo root
is served as-is.
