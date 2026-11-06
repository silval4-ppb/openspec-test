# Spec Delta

## Purpose

Defines profile-stat badges displayed on Tip Cards in both the Feed and the Profile View, as assumed for this change.

The X% Win Rate value is yet to be defined by Product.

## ADDED Requirements

### Requirement: Show a top win-rate badge for qualifying tipsters
When a tipster is in the top X% of all tipsters by win rate, the tipster's Tip Card SHALL display a win-rate badge at the top of the card.

#### Scenario: Qualifying tipster's card appears in the Feed
- **WHEN** a tipster in the top X% by win rate has a Tip Card displayed in the Feed
- **THEN** the card displays the win-rate badge at the top

#### Scenario: Qualifying tipster's card appears in the Profile View
- **WHEN** a tipster in the top X% by win rate has a Tip Card displayed in the Profile View
- **THEN** the card displays the win-rate badge at the top
