## What changed

<!-- One paragraph. What is different after this lands. -->

## Why it is safe

<!-- The question that actually matters here. What happens when this fails:
     a stale quote, an empty band, a reverted reveal, an RPC that times out
     halfway. If the answer is "nothing, it is a copy change", say that. -->

## Checklist

- [ ] If the draw changed, it changed in `shellr-contracts`, `shellr-keeper`
      and `shellr-sdk` in this same change
- [ ] `npm test` / `forge test` passes
- [ ] No em dashes in anything added
- [ ] Comments explain why, and existing warnings were kept
