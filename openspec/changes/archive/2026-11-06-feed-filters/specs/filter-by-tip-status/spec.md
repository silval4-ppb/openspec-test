# Spec Delta

## Purpose

This capability lets readers narrow feed tips according to whether the tips can still be copied.

## ADDED Requirements

### Requirement: Filter feed tips by tip status
When a tip-status filter is supplied, the feed SHALL include only tips whose status matches one of the selected values.

#### Scenario: Filter to copyable tips
- **WHEN** a reader requests the feed with `COPYABLE` selected
- **THEN** the feed includes copyable tips and excludes inactive tips

#### Scenario: Filter to inactive tips
- **WHEN** a reader requests the feed with `INACTIVE` selected
- **THEN** the feed includes inactive tips and excludes copyable tips

#### Scenario: No tip-status filter is supplied
- **WHEN** a reader requests the feed without selecting a tip status
- **THEN** the feed query returns only `COPYABLE` bets by default.
