# Spec Delta

## Purpose

Defines when the Tip CTA displays a potential-returns label and how that return is calculated for a supported simple tip bet.

## ADDED Requirements

### Requirement: Show the potential-returns label only in the enabled experiment variant
The Tip CTA SHALL display a potential-returns label when the customer is assigned to an experiment variant that enables the label. The default variant SHALL retain the existing Tip CTA behavior without a label.

#### Scenario: Customer is assigned to the default variant
- **WHEN** the customer views a Tip CTA in the default experiment variant
- **THEN** the Tip CTA does not display a potential-returns label

#### Scenario: Customer is assigned to a label-enabled variant
- **WHEN** the customer views a Tip CTA in a variant that enables the label
- **THEN** the Tip CTA displays the potential-returns label below the Add to Betslip text

### Requirement: Calculate potential returns for a simple tip bet
For a supported simple tip bet in a label-enabled variant, the system SHALL calculate potential returns as the stake amount multiplied by the bet's decimal odds and show the potential return and stake in the label.

#### Scenario: Display potential returns for a simple bet
- **WHEN** a label-enabled Tip CTA has a stake of €1 and decimal odds of 1.5
- **THEN** the label shows potential returns of €1.50 from a €1 stake
