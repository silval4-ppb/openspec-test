# Tasks

## 1. Setup Experiment

- [ ] 1.1 Setup Experiment in Loop Client
    - [ ] 1.1.1 Ensure experiment reaches TBD

## 2. Create `useExperiment` hook

- [ ] 2.1 Create the `useExperiment` that can be shared in the Social module in `tbd-components`
    - [ ] 2.1.1 This hook has a experiment ID param, fetches `AppContext` data and returns something like:

```ts
type ExperimentData = {
    experimentId: string;
    variant: string;
}
```

## 3. Use `useExperiment` hook in `TipBetButton`

Use the hook in `TipBetButton`, which is the lower in the component tree possible.

- [ ] 3.1 Default Variant: should keep old behaviour, no label.
- [ ] 3.2 Variant 1: should show the returns label. This is sent to `SportsbookBetButton` the-wall component as `secondaryLabel`
- [ ] 3.3 The potential returns value is calculated in the component using the `{variantStakeValue} * decimalOdds` formula. 
        E.g. if `decimalOdds` is `1.5` and variant stake value is `1€`, label would be something like `Get 1.5€ from 1€ bet`.
        Note: this only works because we only support simple bets as Tips. We don't support stuff like Odds Boost, Acca Insurance or Each Way - those are tipically handled in the betslip and TIPS blocks most of those cases.
