# Tax Calculation Software

A client has desktop software developed for decades for tax calculation. This software allows users to enter income and loss on forms into entry fields, and the tax calculation engine will calculate based on tax rules how much money a person owes to the state or state owes to a person in case more taxes paid. When a person is happy with the calculation, it shall be possible to send it to the financial regulator web service and ask for results.

**Example**: The client has desktop software, but the result can be seen here as an example [Tax Calculator](https://www.taxact.com/tools/tax-calculator).

## Software requirements

- As a user, I want to enter my personal information (Name, Surname, Tax ID, Single or married, are there any dependents) on basic info form.

- As a user, I want to enter Tax Year and answer the questions:
  - "Did you use software to complete last year’s taxes?" on the basic info form.

- As a system, I want to be driven by configurable rules so additional questions may be asked in case of an answer:
  - In case you answer as single, additional "Do you qualify as head of household? Are you a qualifying surviving spouse?"
  - In case you answer married, "Are you filing jointly?"
    - In case you file jointly, year of birth of the spouse is needed.

- As a user, I want to enter on the income page:
  - Taxable Wages
  - Spouse's taxable wages
  - Federal taxes withheld and estimated payments
  - Interest income
  - Unemployment income
    - In case I am married and we file taxes jointly, the same information shall be entered for the spouse.
    - There might be more additional information required on the form and shall be configured like Dividend Income.

- As a user, I want to enter deductions related information on the deductions page.

- On each page, I would like to see information on return as:
  - Forecasted Refund
  - Filing Status (married or single)
  - Total Income
  - Adjustments
  - Deductions considered for forecasted refund

- Tools shall be implemented as a web application with mobile support.

- For more functional requirements use link provided
- Web interface is dynamic and what is show managed by tax rules or form definition in tax rules
- Fields on the form can trigger recalculation resulting in numeric values recalc (e.g., Forecasted Refund) or answers to questions in interface activate new fields
- It shall be possible for accountant to change tax rules and form at any time without rebuild of the software
- I would like to avoid any downtime of software or software shall handle it
- Financial data privacy is important. No data lost and data shall be reliable.
- System shall be secure, and every use shall register and login
- It shall be possible to run Calculation engine as separate micro-service from forms or any other components
- Recalculations shall be fast under the load, sequence of recalculations matters

## Trade off exercise

Given the fact that dynamic UI rules (what to show and what not) and tax calculation rules (triggered on data or number entry to the input field in web) are interdependent from application business logic as shown below, provide trade-off analysis:

- Trade-off of possible database or data persistence options for the software. Suggest different options and make a trade-off between them. Client is biased towards MS SQL Server storage. Consider performance of calculation engine and forms rendering application as part of trade off

[Result](Calculation%20engine%20storage%20trade-off.md)

- Trade off of different micro-service architecture options so that requirements – 1) calculation engine shall be a micro-service called by 3rd party and 2) calculation engine shall provide instant calculation result is satisfied.

[Result](Tax%20calculation%20engine%20architecture%20trade-off.md)

Do both trade-off's in terms of Azure cloud or cloud provider of your choice. Make sure trade-off approach or option is described and approach, service or libraries you will use is clear
