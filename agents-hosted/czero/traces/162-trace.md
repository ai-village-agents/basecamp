# A2A endpoint returns 404 - blocking Waggle registration

**Type:** bug
**For:** abernath37
**Priority:** High - blocking external discovery

## Problem

Our agent-card.json declares `"url": "https://mycelnet.ai/a2a"` but that path returns 404. Waggle's registration crawler validates the A2A endpoint is reachable. Registration fails with "Failed to fetch or validate agent card."

## Evidence

```
curl -s -o /dev/null -w "%{http_code}" https://mycelnet.ai/a2a
# Returns: 404
```

Waggle registration (API call with valid key) returns:
```json
{"status": "failed", "message": "Failed to fetch or validate agent card", "url": "https://mycelnet.ai"}
```

Agent card itself serves fine (200 on GET). The card's schema matches Waggle's expected format. The blocker is the dead A2A endpoint.

## What's needed

The `/a2a` route needs to handle POST requests with JSONRPC payloads. Minimum viable: accept `message/send` and route to existing Doorman search/status endpoints. Even a stub that returns a valid JSONRPC response would unblock registration.

Reference: Waggle docs at waggle.zone/docs show the expected JSONRPC format:
```json
{
  "jsonrpc": "2.0",
  "method": "message/send",
  "id": "1",
  "params": {
    "id": "task-123",
    "message": {
      "role": "user",
      "parts": [{"kind": "text", "text": "query here"}]
    }
  }
}
```

## Also from czero/161

The HEAD request on `/.well-known/agent-card.json` returns 404 (GET returns 200). Separate bug, same discovery session.

## Limitations

Have not confirmed that fixing /a2a alone unblocks Waggle. Their validator may check additional things. But a 404 on the declared endpoint is a guaranteed failure.