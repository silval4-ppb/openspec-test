# filter-by-tip-status Specification

## Purpose

This capability lets readers narrow feed tips according to whether the tips can still be copied.

## Requirements

### Requirement: Filter feed tips by tip status
The feed SHALL evaluate a `status` filter against each tip's derived lifecycle status, not a stored status value alone. A tip is `COPYABLE` only when it is not risk-restricted, its tip-level result and every leg result are `NOT_RESULTED`, and its earliest event start time is in the future; otherwise it is `INACTIVE`.

#### Scenario: Filter to copyable tips
- **WHEN** a reader requests the feed with `status: COPYABLE`
- **THEN** the feed includes exactly the tips whose derived status is `COPYABLE`

#### Scenario: Filter to inactive tips
- **WHEN** a reader requests the feed with `status: INACTIVE`
- **THEN** the feed includes exactly the tips whose derived status is `INACTIVE`, including expired, resulted, and risk-restricted tips

#### Scenario: Status selections are complements
- **WHEN** a reader requests the feed with `not: { status: COPYABLE }`
- **THEN** the feed returns the same tips as `status: INACTIVE`

#### Scenario: Legacy tips derive status without backfill
- **WHEN** a tip has no stored lifecycle fields
- **THEN** its status is derived from its current expiry and risk-restriction state without requiring a data backfill

### Requirement: Default to copyable tips when no status leaf is present
The feed query SHALL apply an implicit `status: COPYABLE` selection when the filter is omitted or its tree contains no `status` leaf. A `status` leaf anywhere in the tree, including under `not`, `and`, or `or`, SHALL suppress that implicit selection.

#### Scenario: Omitted or content-only filter uses the default status
- **WHEN** a reader requests the feed without a filter or with a filter tree containing no `status` leaf
- **THEN** the feed includes only tips whose derived status is `COPYABLE`

#### Scenario: Nested status leaf suppresses the implicit default
- **WHEN** a reader requests the feed with a `status` leaf nested under `not`, `and`, or `or`
- **THEN** the query applies the filter tree's status predicates without adding an implicit `COPYABLE` selection

### Requirement: Count status filters in filter complexity limits
A `status` leaf SHALL count as one leaf and one node toward the `TipFilter` tree's configured leaf-count and depth limits.

#### Scenario: Count a status leaf toward filter limits
- **WHEN** a reader requests the feed with a `status` leaf in a filter tree
- **THEN** that leaf contributes one to the tree's leaf count and one to its depth

### Requirement: Return no matches for contradictory status predicates
A self-contradictory filter tree combining incompatible status selections SHALL return an empty result set rather than a validation error.

#### Scenario: Contradictory status selections
- **WHEN** a reader requests the feed with `and: [{ status: COPYABLE }, { status: INACTIVE }]`
- **THEN** the query returns an empty result set without a validation error
