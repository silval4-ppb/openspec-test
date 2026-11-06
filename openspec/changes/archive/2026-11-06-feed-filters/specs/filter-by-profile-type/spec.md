# Spec Delta

## Purpose

This capability lets readers narrow feed tips to those authored by profiles with selected profile types.

## ADDED Requirements

### Requirement: Filter feed tips by profile type
When a profile-type filter is supplied, the feed SHALL include only tips authored by profiles whose type matches one of the selected values.

#### Scenario: Filter to a selected profile type
- **WHEN** a reader requests the feed with `AMBASSADOR` as the selected profile type
- **THEN** the feed includes tips authored by ambassador profiles and excludes tips authored by standard profiles

#### Scenario: No profile-type filter is supplied
- **WHEN** a reader requests the feed without selecting a profile type
- **THEN** the feed is not restricted by profile type
