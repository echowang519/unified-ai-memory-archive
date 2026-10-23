# Design Decisions

## Canonical source records are not overwritten

Source evidence remains the system of record.

Derived summaries, chunks, indexes and memory artifacts are stored separately.

## Derived artifacts must be rebuildable

If an index or summary is corrupted, stale or re-designed, it should be possible to regenerate it from canonical source evidence.

## Authorization happens before retrieval

Permission filtering is not a post-processing step.

Unauthorized records should never become retrieval candidates.

## Stable actor identity drives access

Session IDs, thread IDs, model IDs and UI surfaces are execution details.

The authorization principal is the stable logical actor.

## Provenance is part of the result contract

A retrieval result is incomplete if it contains text but cannot explain where the evidence came from.

## Fail closed, never fall back to unrestricted search

If authorization or actor-scoped projection fails, the correct behavior is an error or no result — not broader data access.

## Archive is not equivalent to memory

The archive stores evidence.

Working memory, summaries and per-turn context are derived runtime artifacts with separate lifecycle and policy.
