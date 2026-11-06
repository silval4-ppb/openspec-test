# filter-by-profile-id Specification

## Purpose

This capability lets readers narrow feed tips to those authored by selected social profiles.

## Requirements

### Requirement: Filter feed tips by profile ID
When a `profileIds` filter is supplied, the feed SHALL include only tips whose profile ID exactly and case-sensitively matches one of the selected IDs.

#### Scenario: Filter to selected profiles
- **WHEN** a reader requests the feed with one or more profile IDs selected
- **THEN** the feed includes tips authored by those profiles and excludes tips authored by other profiles

#### Scenario: Match profile IDs exactly
- **WHEN** a reader requests the feed with a list of profile IDs
- **THEN** a tip matches only when its profile ID exactly equals one of the list values, without case folding, prefix matching, or trimming

#### Scenario: No profile-ID filter is supplied
- **WHEN** a reader requests the feed without selecting profile IDs
- **THEN** the feed is not restricted by profile ID

### Requirement: Validate profile ID filter values
The feed query SHALL reject a `profileIds` filter with an empty list or any null, empty, blank, or leading- or trailing-whitespace value.

#### Scenario: Reject an empty profile ID list
- **WHEN** a reader requests the feed with an empty `profileIds` list
- **THEN** the query returns a validation error

#### Scenario: Reject an invalid profile ID value
- **WHEN** a reader requests the feed with a null, empty, blank, or whitespace-padded profile ID
- **THEN** the query returns a validation error rather than trimming or partially matching the value

### Requirement: Count a profile ID list as one filter leaf
Within a `TipFilter` tree, a `profileIds` field SHALL count as one leaf toward the configured maximum leaf count, regardless of the number of IDs in its list.

#### Scenario: Count a list as one leaf
- **WHEN** a reader requests the feed with a `profileIds` filter containing many IDs
- **THEN** the filter complexity count treats that list as one leaf
