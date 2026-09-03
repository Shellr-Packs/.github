# Security policy

## The short version

These contracts are **not audited**, they hold user funds, and they are live on
mainnet. If you have found something, we would much rather hear it from you
than from the explorer.

**Report to:** `security@shellr.trade`, or a DM to
[@shellr_co](https://x.com/shellr_co) if you want a faster first response.

Please do not open a public issue for anything that touches funds, the draw, or
the keeper's key. Everything else is fine in the open.

## What we will do

- Acknowledge within 48 hours. If we have not, assume the mail went missing and
  poke us on X.
- Tell you plainly whether we think it is exploitable and what we intend to do.
- Credit you when it is fixed, unless you would rather we did not.

There is no bug bounty programme. There is a treasury and a founder who would
rather pay for a report than for an incident, so ask.

## Scope

In scope, roughly in order of how much we care:

| | |
|---|---|
| **Draw manipulation** | Anything that lets the operator, a buyer, or a miner steer which coins drop or what multiplier lands. This is the whole product. |
| **Fund loss** | Draining `bankroll`, stealing `held` ETH between buy and reveal, escaping the `maxStake` cap, or getting a refund and a settlement for the same pack. |
| **Keeper griefing** | Making reveals revert cheaply and repeatedly, so packs stall until the refund window. |
| **Token sales** | Anything that makes `buyWithToken` cost the bankroll more than `tokenPerEth` and `tokenDailyCap` intend. |
| **Frontend** | XSS, a swapped contract address, a wallet prompt that does not say what it will do. |

Out of scope: the price of $SHELLR, the fact that packs have a house edge, the
fact that `MASTER_SECRET` gives the operator advance knowledge of outcomes it
cannot change, and anything that requires the owner key.

## Known and accepted

Stated here so nobody spends a weekend on them.

- **The operator knows outcomes in advance.** It holds `MASTER_SECRET`, so it
  can compute any queued secret. It cannot change which commitment your pack
  takes, and it cannot see your client seed before you send it, so it cannot
  choose an outcome for you. It can decline to reveal - which refunds you.
- **`tokenPerEth` is set by hand.** There is no pool on this chain to read a
  rate from. Stale in one direction is a gift to buyers; `tokenDailyCap` and
  `tokenSales` bound how expensive that gift can get.
- **Reveals are one keeper.** Two would race and waste gas. If it is down,
  packs refund after `revealWindow`. That is the designed failure, not a bug.
- **No audit.** See the top of this file.
