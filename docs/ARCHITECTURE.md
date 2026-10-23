# Architecture

## Layers

### 1. Source adapters

Each approved source is ingested through a source-specific adapter.

Examples may include:

- historical AI exports
- Home message history
- approved document sources

The adapter is responsible for preserving source identity and producing canonical records.

## 2. Canonical archive

The canonical archive stores durable evidence.

A canonical record should preserve enough information to reconstruct:

- source
- original identifier
- timestamp
- actor / conversation scope
- source payload reference
- ingestion metadata

## 3. Normalized search documents

Search documents are optimized projections derived from canonical records.

They may contain:

- normalized text
- searchable metadata
- actor scope
- conversation identifiers
- timestamps
- source provenance

These documents are derived and rebuildable.

## 4. Actor-scoped views

The same canonical archive can expose different authorized projections.

Conceptually:

```text
Canonical Archive
├── actor/ache view
└── actor/xiaoguai view
```

An actor-scoped view is a permission boundary, not merely a UI filter.

## 5. Retrieval

Retrieval operates on the authorized candidate set.

Possible retrieval stages:

1. trusted principal
2. hard filters
3. structured / FTS search
4. merge and dedup
5. ranking
6. provenance-backed result packaging

## 6. Memory / context integration

The archive does not decide what enters every model prompt.

A Memory Service or Context Compiler may consume archive results under separate policies and token budgets.

This separation keeps durable evidence independent from per-turn context.
