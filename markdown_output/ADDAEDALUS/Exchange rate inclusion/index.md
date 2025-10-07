- Exchange rate will be fixed for an order based on RO date.

- Accounting currency will be fixed at Host App level (AED for MENA, INR
  for rest)

**Sales Leads Creation**

Fields to be added

1.  Accounting currency (Auto-filled - AED for DH-MENA, INR for rest) -
    currency_accounting

2.  RO currency (INR/AED/USD) - (currently exists) - currency_RO

3.  Show exchange rate based on RO Date, with accounting currency as
    base currency

**Order Creation/Edit**

New fields defined at sales lead level will be required at order level
for pacing, invoicing etc.

- Bring currency fields at order level from sales lead level.

- Expose options for these variables at order create

- Update labels with RO currency, at whichever place amount has to be
  inserted (Billing rate, computed value etc.)

**Campaign Creation/Edit**

- Billing rate label to show RO_currency as input currency

- Billing rate (input by user) should be stored in RO_currency in a new
  column (billing_rate_ro_currency)

- Convert the Billing rate(in ro_currency) to billing rate (in
  accounting currency) based on exchange rate on RO_Date, and store in
  the current billing rate column. Thus, Pacing/Ranking can continue
  without any change

**Revenue Calculation/Reporting**

- Campaign/Banner/Order report:

  - Display all accounting values in RO as well as accounting currencies

- Revenue monitor

  - Upgrade revenue module to select currency in which amounts have to
    be converted (INR/USD/AED/Accounting currency/RO currency).

  - Allow filter for RO_Currencies

  - Allow selection for output currency (INR/USD/AED/Accounting
    currency/RO currency)

  - Exchange rate to be used should be taken from ro_date of an order,
    wrt RO_Currency

- CR1 reporting

  - This should continue to go in INR as it goes currently

**Invoicing**

- Add ro_currency information in invoice

- Allow selection of accouting currency vs ro_currency while raising
  invoice request

- Ensure that labels that show currency pick correct currency
