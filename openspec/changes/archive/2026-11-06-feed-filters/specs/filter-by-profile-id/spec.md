# Spec Delta

## Purpose

This capability lets readers narrow feed tips to those authored by selected social profiles.

## ADDED Requirements

### Requirement: Filter feed tips by profile ID
When a profile-ID filter is supplied, the feed SHALL include only tips authored by profiles whose IDs match one of the selected IDs.

#### Scenario: Filter to selected profiles
- **WHEN** a reader requests the feed with one or more profile IDs selected
- **THEN** the feed includes tips authored by those profiles and excludes tips authored by other profiles

#### Scenario: No profile-ID filter is supplied
- **WHEN** a reader requests the feed without selecting profile IDs
- **THEN** the feed is not restricted by profile ID
