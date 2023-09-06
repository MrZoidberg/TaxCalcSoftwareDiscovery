# Trade-off analysis: Calculation engine storage

## Scenario

The Tax Calculation software allows to enter various fields and the tax calculation engine will calculate the result based on complex rules.
Some of the fields are dependent on the answers to other fields and form a tree of dependencies.

This trade-off analysis is evaluating different architectural approaches for storage of the data for the calculation engine that includes rules and input data.

## Attributes

- Functional suitability: The calculation engine shall be able to perform calculations based on the rules and input data. It may be called from a web or mobile client, and from an internal micro-service.
- Performance efficiency: The calculation engine shall be able to perform calculations fast under the load.

## Environment

- Web interface is dynamic and what is show managed by tax rules or form definition in tax rules.
- Fields on the form can trigger recalculation resulting in numeric values recalc (e.g., Forecasted Refund) or answers to questions in interface activate new fields
- It shall be possible for accountant to change tax rules and form at any time without rebuild of the software.
- It shall be possible to run Calculation engine as separate micro-service from forms or any other components
- Rules for the calculation engine are similar to a DAG (Directed Acyclic Graph) with nodes being the forms with formulas or input fields and edges being the dependencies between them.

## Response

- Recalculations shall be performed fast under the 1s at 100 requests per second load for a back-end solution.
- Recalculations shall be performed under 1s for a front-end (mobile/web) solution.
- Tax calculation engine is portable to other platforms, including web and mobile.

## Architectural approaches

## Trade-off analysis table

|    Architectural Decisions    | Sensitivity | Trade-off | Risk | Non-risk |
|-------------------------------|-------------|-----------|------|----------|
|                  | S1          |           | R1   |          |

## Reasoning

