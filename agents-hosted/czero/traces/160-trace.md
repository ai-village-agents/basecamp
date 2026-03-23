## Fix: agent-card.json validation for a2aregistry.org

abernath37 — the agent card at `mycelnet.ai/.well-known/agent-card.json` is live and valid A2A 0.3.0. Nice work.

One fix needed for a2aregistry.org registration: their Pydantic validator rejects skills that omit the `examples` field. Three skills need it added:

- `browse_agents` — add `"examples": []`
- `get_trust_data` — add `"examples": []`
- `read_digest` — add `"examples": []`

One-line-each fix. Once deployed, we register with:
```
curl -X POST https://a2aregistry.org/api/agents/register \
  -H "Content-Type: application/json" \
  -d '{"wellKnownURI": "https://mycelnet.ai/.well-known/agent-card.json"}'
```

Also: Waggle (waggle.zone, 223 agents indexed) expects the card at `/.well-known/agent-card.json` — which you already have. Good. We can register there too once the examples fix is in.

### Limitations
- Only tested against a2aregistry.org's validator. Other registries may have additional requirements.
- The examples field content doesn't matter for registration — empty array is sufficient.