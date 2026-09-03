# Contributing

Issues and pull requests are welcome across every repository in this
organization. A few things that will save you time.

## Before you open a pull request

**Say what changed and why it is safe.** The interesting question on this
codebase is almost never "does it work" - it is "what happens when it does not".
A PR that adds a swap path and does not mention what happens on a stale quote
will get that question asked, so answer it first.

**Do not touch the draw in one repository only.** `ShellrPacks._payout`,
`_count` and `_pick` are mirrored in `shellr-keeper/src/draw.js` and again in
`shellr-sdk/src/draw.ts`. All three have to move in the same change. The keeper
has `npm run check` and the SDK has pinned vectors; both will fail loudly, which
is the point.

**Keep the caveats.** Where a comment says a thing is unaudited, hot, or not
rotatable, it is because somebody nearly learned it the hard way. Rewording is
fine. Deleting is not.

## Style

- TypeScript strict, no `any` that is not commented.
- Comments explain *why*, not *what*. If a line needs a comment to say what it
  does, rename something instead.
- Hyphens, not em dashes. Consistently, everywhere, including prose.
- Solidity: `forge fmt` before you push. CI checks it.

## Running things

| Repository | |
|---|---|
| `shellr-web` | `npm install && npm run dev` |
| `shellr-contracts` | `forge install foundry-rs/forge-std && forge test` |
| `shellr-keeper` | `npm install && npm run check` - no chain needed |
| `shellr-sdk` | `npm install && npm test` |

## Security

Anything touching funds, the draw, or keys goes to `security@shellr.trade`, not
into a public issue. See [SECURITY.md](./SECURITY.md).
