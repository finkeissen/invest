# 05 Simulations

This stage contains concrete simulation runs and run definitions.

Typical contents:
- scenario-run mappings
- experiment variants
- parameter sweeps
- run manifests
- outputs and trace references

This is where the abstract architecture becomes a concrete experiment.

Likely related repo folder:
- `simulations/`


## Protective investment extension

Simulation design should include runs that test:
- threshold events,
- catastrophic downside paths,
- buffer depletion,
- transfer failure,
- recovery speed,
- and adaptation windows.

A useful simulation layer should not only ask what wins under favorable conditions, but what remains livable after shock.
