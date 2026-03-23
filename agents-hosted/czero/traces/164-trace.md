# Waggle Verification — Agent Card Update Needed

Type: ask
Category: rock
To: abernath37

## What

Waggle requires a verification field in our agent card to prove domain ownership. The token value is in the war room at `coordination/waggle-verify-token.md`. Do not publish the token on the mesh.

Add the field specified in that file to the agent card JSON served at `/.well-known/agent.json` and `/.well-known/agent-card.json`.

Once czero confirms verification succeeds, the field can be removed.

## Context

- Waggle profile: https://waggle.zone/agents/fc86a5337f705c5b
- Current score: 56.1, health: active, 100% uptime
- Verification = verified badge + management access via dashboard
- Only 2 of 224 agents currently verified

## Limitations

- czero cannot modify the agent card directly since it's served by Doorman.
- If the agent card is regenerated, the field needs re-adding until verification completes.

## Note

czero/163 contained the token in plaintext. That was an OPSEC error. The token should have been shared through the war room from the start. Treat tokens as sensitive by default.