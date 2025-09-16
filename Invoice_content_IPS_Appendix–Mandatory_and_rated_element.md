---
title: "Invoice Content Specification – Mandatory and Rated Elements"
layout: default
---

<p align="center">
  <img src="assets/header.jpg" alt="Header Image" width="100%">
</p>

# Invoice Content IPS - Mandatory and rated elements of the PINT A-NZ Billing specification


This is a quick reference guide showing all PINT A-NZ Billing specification elements that are either mandatory according to the specification or discussed in the Invoice Content Industry Practice Statement (IPS). It omits all other invoice elements and, as such, is incomplete for the purposes of building a Peppol invoicing solution. As noted in the Invoice Content IPS, 'required for interoperability' and 'recommended' elements should be included when appropriate, but may not be relevant for some end users and will not necessarily have to appear on every eInvoice.

|     BT ID &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;         | Term                             | Description                                                                 | Rating      |
|------------|---------------------------------------------|------------------------------------------------------------------------------|-------------------------------|
| IBT-024    | Specification identifier                    | Identification of the specification containing semantic rules and business logic | Mandatory                     |
| IBT-023    | Business process type                       | Identifies the business process context for the transaction                  | Mandatory                     |
| IBT-001    | Invoice number                              | Unique identification of the Invoice                                         | Mandatory                     |
| IBT-002    | Invoice issue date                          | Date when the Invoice was issued                                             | Mandatory                     |
| IBT-009    | Payment due date                            | Date when payment is due. Use with IBT-020 Payment terms                     | Required for interoperability, & conditionally mandatory |
| IBT-003    | Invoice type code                           | Code specifying the functional type of the Invoice                           | Mandatory                     |
| IBT-022    | Invoice note                                | Unstructured note relevant to the Invoice                                    | Required for interoperability |
| IBT-005    | Invoice currency code                       | Currency for all Invoice amounts except TAX in accounting currency           | Mandatory                     |
| IBT-010    | Buyer reference                             | Identifier assigned by Buyer for internal routing                            | Required for interoperability |
| IBT-013    | Purchase order reference                     | Identifier of referenced purchase order issued by Buyer                      | Required for interoperability |
| IBT-025    | Preceding Invoice reference                 | Identification of a previously sent Invoice                                  | Mentioned                     |
| IBT-026    | Preceding Invoice issue date                | Date when the Preceding Invoice was issued                                   | Mentioned                     |
| IBT-017    | Tender or lot reference                     | Identification of the call for tender or lot                                 | Required for interoperability |
| IBT-012    | Contract reference                          | Identification of a contract                                                 | Required for interoperability |
| IBG-24     | ADDITIONAL SUPPORTING DOCUMENTS             | Info about supporting documents substantiating invoice claims                | Required for interoperability |
| IBT-011    | Project reference                           | Identification of the project the invoice refers to                          | Required for interoperability |
| IBG-04     | SELLER                                      | Info about the Seller                                                        | Mandatory                     |
| IBT-034    | Seller electronic address                   | Seller's electronic address for document delivery                            | Mandatory                     |
| IBT-028    | Seller trading name                         | Alternate name by which the Seller is known                                  | Recommended                   |
| IBG-05     | SELLER POSTAL ADDRESS                       | Info about Seller’s postal address                                           | Mandatory                     |
| IBT-035    | Seller address line 1                       | Main address line                                                            | Recommended                   |
| IBT-036    | Seller address line 2                       | Additional address line                                                      | Recommended                   |
| IBT-037    | Seller city                                 | City, town or village                                                        | Recommended                   |
| IBT-038    | Seller post code                            | Postal code                                                                  | Recommended                   |
| IBT-039    | Seller country subdivision                  | Subdivision of a country                                                     | Recommended                   |
| IBT-162    | Seller address line 3                       | Additional address line                                                      | Recommended                   |
| IBT-040    | Seller country code                         | Country identifier                                                           | Mandatory                     |
| IBT-031    | Seller TAX identifier                       | Seller’s TAX ID                                                              | Required for interoperability |
| IBT-031-1  | Tax scheme code                             | Scheme of the TAX identifier                                                 | Required for interoperability |
| IBT-027    | Seller name                                 | Formal name of the Seller                                                    | Mandatory                     |
| IBT-030    | Seller legal registration identifier        | Legal registration ID                                                        | Mandatory                     |
| IBT-041    | Seller contact point                        | Contact point for the Seller                                                 | Recommended                   |
| IBT-042    | Seller contact telephone number             | Phone number for the contact point                                           | Recommended                   |
| IBT-043    | Seller contact email address                | Email address for the contact point                                          | Required for interoperability |
| IBG-07     | BUYER                                       | Info about the Buyer                                                         | Mandatory                     |
| IBT-049    | Buyer electronic address                    | Buyer’s electronic address                                                   | Mandatory                     |
| IBT-055    | Buyer country code                          | Country identifier                                                           | Mandatory                     |
| IBT-044    | Buyer name                                  | Full name of the Buyer                                                       | Mandatory                     |
| IBT-045    | Buyer trading name                          | Alternate name for the Buyer                                                 | Conditional                   |
| IBT-047    | Buyer legal registration identifier         | Legal registration ID                                                        | Mandatory                     |
| IBT-056    | Buyer contact point                         | Contact point for the Buyer                                                  | Recommended                   |
| IBT-057    | Buyer contact telephone number              | Phone number for the contact point                                           | Recommended                   |
| IBT-058    | Buyer contact email address                 | Email address for the contact point                                          | Required for interoperability |
| IBT-083    | Remittance information                      | Text used for payment routing or linking payment to Invoice                  | Required for interoperability |
| IBT-084    | Payment account identifier                  | Unique ID of the payment account                                             | Required for interoperability |
| IBT-085    | Payment account name                        | Name of the payment account                                                  | Required for interoperability |
| IBT-086    | Payment service provider identifier         | Identifier for the payment service provider                                  | Required for interoperability |
| IBG-20     | DOCUMENT LEVEL ALLOWANCES                   | Info about allowances for the Invoice as a whole                             | Recommended                   |
| IBG-21     | DOCUMENT LEVEL CHARGES                      | Info about charges and taxes other than TAX                                  | Recommended                   |
| IBT-110    | Invoice total TAX amount                    | Total TAX amount for the Invoice                                             | Mandatory                     |
| IBG-23     | TAX BREAKDOWN                               | Info about TAX breakdown by category, rate, and exemption                    | Mandatory                     |
| IBG-22     | DOCUMENT TOTALS                             | Monetary totals for the Invoice                                              | Mandatory                     |
| IBG-25     | INVOICE LINE                                | Info about individual Invoice lines                                          | Mandatory                     |
| IBT-126    | Invoice line identifier                     | Unique ID for the Invoice line                                               | Mandatory                     |
| IBT-129    | Invoiced quantity                           | Quantity of items charged                                                    | Mandatory                     |
| IBT-130    | Invoiced quantity unit of measure code      | Unit of measure for invoiced quantity                                        | Mandatory                     |
| IBT-131    | Invoice line net amount                     | Total amount of the Invoice line before tax                                  | Mandatory                     |
| IBT-132    | Referenced purchase order line reference    | ID for referenced line in a purchase order                                   | Conditional                   |
| IBG-27     | INVOICE LINE ALLOWANCES                     | Info about allowances for individual Invoice lines                           | Mentioned                     |
| IBG-28     | INVOICE LINE CHARGES                        | Info about charges and taxes other than TAX for Invoice lines                | Mentioned                     |
| IBG-31     | ITEM INFORMATION                            | Info about goods and services invoiced                                       | Mandatory                     |
| IBT-154    | Item description                            | Description of an item                                                       | Required for interoperability |
| IBT-153    | Item name                                   | Name of an item                                                              | Mandatory                     |
| IBT-156    | Item Buyer's identifier                     | Buyer-assigned item identifier                                               | Mentioned                     |
| IBT-155    | Item Seller's identifier                    | Seller-assigned item identifier                                              | Mentioned                     |
| IBT-157    | Item standard identifier                    | Item identifier based on a registered scheme                                 | Mentioned                     |
| IBG-30     | LINE TAX INFORMATION                         | TAX info for goods/services on the Invoice line                              | Mandatory                     |
| IBG-29     | PRICE DETAILS                               | Price info for goods/services invoiced                                       | Mandatory                     |


## Legend

- **Mandatory**: Required by the PINT A2C Billing specification  
- **Recommended for Interoperability**: Strongly advised for cross-system compatibility  
- **Conditional**: Required depending on context (ICIPS guidance)  
- **Required for Interoperability**: Needed for consistent data exchange  
- **Mentioned**: Referenced but not formally required  
