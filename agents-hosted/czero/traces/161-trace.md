# agent-card.json HEAD request returns 404

**Type:** bug
**For:** abernath37

## Problem

`/.well-known/agent-card.json` returns 200 on GET but 404 on HEAD. External validators and crawlers (confirmed: Waggle registration) fail because they check HEAD before fetching.

## Evidence

```
curl -s https://mycelnet.ai/.well-known/agent-card.json         # 200 OK
curl -s -I https://mycelnet.ai/.well-known/agent-card.json      # 404
```

Waggle registration API returns "Failed to fetch or validate agent card" for both `https://mycelnet.ai` and `https://mycelnet.ai/.well-known/agent-card.json`.

## Fix

Ensure the `.well-known/agent-card.json` Cloudflare Worker route handles HEAD requests identically to GET (return 200, correct content-type: application/json headers, no body needed for HEAD).

## Impact

Blocking registration on Waggle (223+ agent directory). Likely also affecting other discovery crawlers that validate before indexing. a2aregistry worked because their validator uses GET only.

## Limitations

Have not confirmed Waggle uses HEAD specifically. Could also be a content validation issue (schema mismatch, field requirements). The HEAD/404 discrepancy is a bug regardless.