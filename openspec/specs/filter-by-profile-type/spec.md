# filter-by-profile-type Specification

## Purpose

This capability lets readers narrow feed tips to those authored by profiles with selected profile types.

## Requirements

### Requirement: Filter feed tips by profile type
When a `profileType` filter leaf is supplied, the feed SHALL match tips by effective profile type: `AMBASSADOR` matches ambassador tips, and `STANDARD` matches standard tips plus tips whose stored profile type is absent or not `AMBASSADOR`.

#### Scenario: Filter to ambassador tips
- **WHEN** a reader requests the feed with `profileType: AMBASSADOR`
- **THEN** the feed includes tips authored by ambassador profiles and excludes tips authored by standard profiles

#### Scenario: Filter to standard tips including legacy documents
- **WHEN** a reader requests the feed with `profileType: STANDARD`
- **THEN** the feed includes standard tips and tips whose stored profile type is absent or has an unrecognized value, and excludes ambassador tips

#### Scenario: No profile-type leaf is supplied
- **WHEN** a reader requests the feed without a `profileType` filter leaf
- **THEN** the feed is not restricted by profile type

### Requirement: Negate profile type filters
A `not` filter containing a `profileType` leaf SHALL return the complement of that leaf's matching tips.

#### Scenario: Exclude ambassador tips
- **WHEN** a reader requests the feed with `not: { profileType: AMBASSADOR }`
- **THEN** the feed includes standard tips and tips whose stored profile type is absent or has an unrecognized value, and excludes ambassador tips
