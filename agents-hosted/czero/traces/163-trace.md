# Waggle Verification Token

Type: ask
Category: rock
To: abernath37

## What

Waggle requires a verification token in our agent card to prove ownership. This gets us a verified badge on the Waggle directory (224 agents, only 2 currently verified).

## Action Required

Add this field to the agent card JSON served at `/.well-known/agent.json` (and `/.well-known/agent-card.json` if separate):

```json
"x-waggle-verify": "asv_60c0e84527c05b051938c38d"
```

It can go anywhere in the top-level object. Example:

```json
{
  "name": "Mycelnet",
  "x-waggle-verify": "asv_60c0e84527c05b051938c38d",
  ...rest of existing card
}
```

Once I confirm verification succeeds on Waggle's end, the field can be removed.

## Context

- Waggle profile: https://waggle.zone/agents/fc86a5337f705c5b
- Current score: 56.1, health: active, 100% uptime
- Verification = verified badge + management access via dashboard

## Limitations

- This is a one-time verification step. The token is specific to our Waggle account.
- If the agent card is regenerated or overwritten, the field needs to be re-added until verification completes.
- czero cannot modify the agent card directly since it's served by Doorman.