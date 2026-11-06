# OpenSpec + OKF Workspace

This repository offers a Spec Driven Development (SDD) workflow using OpenSpec, as well as Open Knowledge Format workspace to keep permanent data and have it be linkable to SDD specs.

## Repository structure

- [`knowledge/`](knowledge/index.md) uses OKF (Open Knowledge Format) and contains durable explanatory knowledge: domain concepts, architecture notes, decisions, and initiatives.
- [`knowledge/initiatives/`](knowledge/initiatives/index.md) maps longer efforts that may span multiple OpenSpec changes. For example, [Social Full Profiles](knowledge/initiatives/social-full-profiles.md) tracks work across the Feed, profile views, editing, and profile activation.
- [`knowledge/capabilities/`](knowledge/capabilities/index.md) stores capabilities and more info about them
- [`knowledge/decisions/`](knowledge/decisions/index.md) stores ADRs and other kinds of decision records
- [`knowledge/architecture/`](knowledge/architecture/index.md) stores permanent architecture artifacts
- [`openspec/specs/`](openspec/specs/) contains the current normative specifications for capabilities.
- [`openspec/changes/`](openspec/changes/) contains proposed and in-progress changes. Completed changes are kept under [`openspec/changes/archive/`](openspec/changes/archive/).
- [`openspec/config.yaml`](openspec/config.yaml) configures the OpenSpec workflow for this repository.

## How the information fits together

- Use an **initiative** to explain the larger goal, shared concepts, assumptions, and dependencies across related work. All using OKF.
- Store durable domain concepts and supporting documentation in the OKF section (`knowledge/`), and link to them from specs when useful.
- Use an **OpenSpec change** for a bounded piece of work that can be designed, implemented, and verified together.
- Use **specs** for the authoritative behavioral requirements. Keep explanatory context in `knowledge/` and link to related specs and changes rather than duplicating their requirements.

An initiative is a planning map, not an execution tracker or a replacement for OpenSpec. Record important dependencies in the relevant change artifacts too, so they remain visible when a change is worked on independently.

## Current examples

- Domain concept: [Profile Type](knowledge/capabilities/social/profile-type.md)
- Initiative: [Social Full Profiles](knowledge/initiatives/social-full-profiles.md)
- Active changes: [Tip Card Uplifts](openspec/changes/tip-card-uplifts/proposal.md), [Tip Card Badges](openspec/changes/tip-card-badges/proposal.md), and [Tip Returns Experiment](openspec/changes/tip-returns-experiment/proposal.md)
- Archived change: [Feed Filters](openspec/changes/archive/2026-11-06-feed-filters/proposal.md)
