# Validation

## Known challenges

- LLM consistency and drift
- payoff design bias
- high-dimensional interaction effects
- difficulty of calibrating political and strategic latent variables
- risk of confusing coherent narrative with robust explanatory power

## Validation anchors

| Layer | What to check | Example reference types |
|---|---|---|
| Political / geopolitical | event timing, policy response patterns, escalation logic | central bank minutes, sanctions databases, treaty events, official releases |
| Investment / strategic behavior | allocation shifts, defensive repositioning, institutional adaptation | fund-flow data, balance-sheet disclosures, filings, sector reports |
| Game-theoretic behavior | stability of incentives and best responses | event studies, benchmark games, historical episode comparison |
| Scenario outputs | plausibility ranges and failure modes | stress tests, historical analogues, expert review |

## Practical guidelines

- version assumptions and scenario definitions
- keep calibration notebooks reproducible
- prefer ranges and sensitivity analysis over point certainty
- benchmark isolated modules before integrated runs
- record failed scenarios, not only successful ones
