# Risk analysis for tax calculation software

## Overview

This document provides risks analysis identified during trade-off analysis for the tax calculation storage and architecture. It includes impact and probability of risks, and mitigation strategies.

The estimated overall risk scope is calculated as `Probability X Impact` for each risk. Based on the calculated risk score, assign a risk rating or category. The following risk rating categories are used:

- Low Risk: `Score 1-3`
- Moderate Risk: `Score 4-6`
- High Risk: `Score 7-9`

Probability levels:

- Low Probability: `1`
- Moderate Probability: `2`
- High Probability: `3`

Impact levels:

- Low Impact: `1`
- Moderate Impact: `2`
- High Impact: `3`

## Risks

### Risk 1: Blazor WASM is not mature enough

 Blazor WASM is a new technology that is not yet widely adopted and have significant limitations in terms of compatibility with .NET Core and interopability with JavaScript. Ability of Blazor WASM to perform complex calculations is not yet proven and brings a risk that all requirements may not be satisfied due to technical feasibility and performance limitations. For example, Blazor WASM is [very limited on security alogorithm support](https://github.com/dotnet/designs/blob/main/accepted/2021/blazor-wasm-crypto.md) and interop with JavaScript is [very limited](https://learn.microsoft.com/en-us/aspnet/core/blazor/javascript-interoperability/import-export-interop?view=aspnetcore-7.0). Interop performance for Blazor WASM [is tested to be several time less performant than JavaScript](https://krausest.github.io/js-framework-benchmark/current.html#1139).

#### Impact

The impact of this risk is that the solution may not be able to satisfy all functional requirements and may not be performant enough compared to the alternatives.

Impact: **HIGH**

#### Probability

The probability of this risk occurring can be assessed based on the following factors:

- Complexity of Calculations: The likelihood of this risk also depends on the complexity of the tax calculations required. If the calculations are straightforward, the risk may be lower compared to highly complex calculations.
- Use of Interop: The probability of issues related to interop with JavaScript may vary depending on how extensively the application relies on such interop.
- Security Requirements: If the tax calculation software has stringent security requirements that Blazor WASM cannot fully meet, the probability of this risk increases.
- Performance Demands: If the software requires high-performance calculations and Blazor WASM performance falls significantly short, the probability of this risk is higher.
- Development Team Expertise: The probability can also be influenced by the expertise of the development team in working with Blazor WASM and addressing its limitations effectively.

Probability: **MODERATE** (2)

#### Risk score

Overall Risk Score: `2 (Probability) x 3 (Impact) = 6`  
Risk Rating: With a score of 6, this risk would be categorized as a **Moderate Risk**.

#### Mitigation strategies

1. Pilot Testing and Proof of Concept

    Conduct a pilot test or proof of concept to evaluate Blazor WASM's capabilities in handling tax calculations and to identify any potential limitations or performance bottlenecks.
    Use this phase to assess the suitability of Blazor WASM for our specific use case.

2. Expertise and Training

    Invest in training and upskilling your development team in Blazor WASM to ensure they have the necessary expertise to work effectively with this technology.
    Leverage Microsoft partnership to evaluate the solution and provide guidance on best practices.

3. Utilize Blazor 7 that has extended security algorithms support

4. WebAssembly Ahead-of-Time (AOT) Compilation

    Consider using WebAssembly AOT compilation to convert C# code to WebAssembly bytecode ahead of time. This can improve runtime performance compared to Just-In-Time (JIT) compilation.
