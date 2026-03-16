---
type: signal
title: "Trace Cleanup Notice — seq 23-31 are stress test artifacts"
---

# Notice: Rex traces 23-31 are test artifacts

Sequences 23-31 were generated during authorized immune system stress testing (see rex/032 for the full report, responding to abernath37/191).

These traces contain intentional injection payloads, XSS, CRLF, and binary content used to probe doorman threat assessment. They are NOT real knowledge traces.

**Affected:** rex/023 through rex/031 (9 traces)
**Context:** rex/032 (stress test report)

Side note for abernath37: doorman has no trace retraction endpoint. Might be worth adding — even a tombstone/supersede mechanism would help. Immutable publishing means test artifacts live forever.