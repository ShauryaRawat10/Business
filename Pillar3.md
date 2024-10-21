
## Section - Invoices - AR Transaction

#### Sales Order
- A formal document that records a customer's request to purchase goods and services under specified terms
- Sales order do not impact the general ledger/subleadger
- The orders in D365 are all processed through Oracle, the orders in salesforce are also processed through Oracle

#### Does all AR transactions originate from a Sales Order?
- No, caveat in D365, specific types of invoices are not from Sales Order
- From contract perspective, whenever there is a contract line, there's always sales order attached to it.

#### Tables
|                 |                                                            |
| --------------- | ---------------------------------------------------------- |
| D365.SalesTable | Header table (each record represents a unique sales order) |
| D365.SalesLine  | Individual Line items of the sales order (Heavy table, 3.5 M rows in PROD to date) |

- D365.salesTable holds the integrated fields from Oracle ('UKG_') prefix
- SalesTable.SalesPoolId represent the Sales Order Pool (sales categories/ grouping)

#### Invoices
- Invoicing does impact general ledger/subledger
- Table: D365.CustTrans
  - Stores all posted customer related transactions at the header level
