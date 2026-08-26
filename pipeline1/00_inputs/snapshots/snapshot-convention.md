# Snapshot Convention

## Purpose

Snapshots freeze the input state used by a particular run so later results can be reproduced and compared.

## Recommended structure

Each snapshot folder should contain:
- a date or version label
- the input files included
- source notes or provenance summary
- important caveats
- the scenarios or runs that depend on it
- the level of analysis in scope
- the value framework in scope

## Naming convention

A simple starter pattern is:

`YYYY-MM-DD_<scope>_<version>`

Example:

`2026-03-13_core-world_v1`

## Minimum manifest fields

A snapshot manifest should eventually state:
- snapshot id
- creation date
- included files
- excluded known gaps
- intended downstream runs
- notes on incompleteness or provisional assumptions
- which actor levels are in scope
- which capital forms are in scope
- which priority ladder is assumed
- which moral or practical exclusions are active

## Reproducibility rule

A result is not fully reproducible unless the snapshot reveals both:
- what the world description was
- what the evaluative frame was

The same facts can lead to different recommendations under different priorities.
