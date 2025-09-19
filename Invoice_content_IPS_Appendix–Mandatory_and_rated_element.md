---
title: "Invoice Content Specification – Mandatory and Rated Elements"
layout: default
---

<p align="center">
  <img src="assets/header.jpg" alt="Header Image" width="100%">
</p>

# Invoice Content IPS - Mandatory and rated elements of the PINT A-NZ Billing specification


This is a quick reference guide showing all PINT A-NZ Billing specification elements that are either mandatory according to the specification or discussed in the Invoice Content Industry Practice Statement (IPS). It omits all other invoice elements and, as such, is incomplete for the purposes of building a Peppol invoicing solution. As noted in the Invoice Content IPS, 'required for interoperability' and 'recommended' elements should be included when appropriate, but may not be relevant for some end users and will not necessarily have to appear on every eInvoice.

---

|  BT ID &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  | Term | Description | Rating |
|-------|------|-------------|--------|
| [IBT-024](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-CustomizationID/) | Specification identifier | An identification of the specification containing the total set of rules regarding semantic content, cardinalities and business rules to which the data contained in the instance document conforms. | Mandatory |
| [IBT-023](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-ProfileID/) | Business process type | Identifies the business process context in which the transaction appears, to enable the Buyer to process the Invoice in an appropriate way. | Mandatory |
| [IBT-001](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-ID/) | Invoice number | A unique identification of the Invoice. | Mandatory |
| [IBT-002](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-IssueDate/) | Invoice issue date | The date when the Invoice was issued. | Mandatory |
| [IBT-009](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-DueDate/) | Payment due date | The date when the payment is due. When there is an amount due for payment, senders must use either payment due date or IBT-020 Payment terms. | Required for interoperability, conditionally mandatory |
| [IBT-003](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-InvoiceTypeCode/) | Invoice type code | A code specifying the functional type of the Invoice. | Mandatory |
| [IBT-022](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-Note/) | Invoice note | A textual note that gives unstructured information that is relevant to the Invoice as a whole. | Required for interoperability |
| [IBT-005](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-DocumentCurrencyCode/) | Invoice currency code | The currency in which all Invoice amounts are given, except for the Total TAX amount in accounting currency. | Mandatory |
| [IBT-010](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-BuyerReference/) | Buyer reference | An identifier assigned by the Buyer used for internal routing purposes. | Required for interoperability |
| [IBT-013](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-OrderReference/cbc-ID/) | Purchase order reference | An identifier of a referenced purchase order, issued by the Buyer. | Required for interoperability |
| [IBT-025](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-BillingReference/cac-InvoiceDocumentReference/cbc-ID/) | Preceding Invoice reference | The identification of an Invoice that was previously sent by the Seller. | Mentioned |
| [IBT-026](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-BillingReference/cac-InvoiceDocumentReference/cbc-IssueDate/) | Preceding Invoice issue date | The date when the Preceding Invoice was issued. | Mentioned |
| [IBT-017](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-OriginatorDocumentReference/cbc-ID/) | Tender or lot reference | The identification of the call for tender or lot the invoice relates to. | Required for interoperability |
| [IBT-012](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-ContractDocumentReference/cbc-ID/) | Contract reference | The identification of a contract. | Required for interoperability |
| [IBG-24](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AdditionalDocumentReference-2/) | Additional supporting documents | A group of business terms providing information about additional supporting documents substantiating the claims made in the Invoice. | Required for interoperability |
| [IBT-011](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-ProjectReference/cbc-ID/) | Project reference | The identification of the project the invoice refers to. | Required for interoperability |
| [IBG-04](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingSupplierParty/) | Seller | A group of business terms providing information about the Seller. | Mandatory |
| [IBT-034](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingSupplierParty/cac-Party/cbc-EndpointID/) | Seller electronic address | Identifies the Seller's electronic address to which a business document may be delivered. | Mandatory |
| [IBT-028](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingSupplierParty/cac-Party/cac-PartyName/cbc-Name/) | Seller trading name | A name by which the Seller is known, other than Seller name (also known as Business name). | Recommended |
| [IBG-05](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PostalAddress/) | SELLER POSTAL ADDRESS | A group of business terms providing information about the address of the Seller. | Mandatory |
| [IBT-035](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PostalAddress/cbc-StreetName/) | Seller address line 1 | The main address line in an address. | Recommended |
| [IBT-036](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PostalAddress/cbc-AdditionalStreetName/) | Seller address line 2 | An additional address line in an address that can be used to give further details supplementing the main line. | Recommended |
| [IBT-037](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PostalAddress/cbc-CityName/) | Seller city | The common name of the city, town or village, where the Seller address is located. | Recommended |
| [IBT-038](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PostalAddress/cbc-PostalZone/) | Seller post code | The identifier for an addressable group of properties according to the relevant postal service. | Recommended |
| [IBT-039](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PostalAddress/cbc-Region/) | Seller country subdivision | The subdivision of a country. | Recommended |
| [IBT-162](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PostalAddress/cbc-AddressLine3/) | Seller address line 3 | An additional address line in an address that can be used to give further details supplementing the main line. | Recommended |
| [IBT-040](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PostalAddress/cbc-Country/cbc-IdentificationCode/) | Seller country code | A code that identifies the country. | Mandatory |
| [IBT-031](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PartyTaxScheme/cbc-CompanyID/) | Seller TAX identifier | The Seller’s TAX identifier (also known as Seller TAX identification number). | Required for interoperability |
| [IBT-031-1](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PartyTaxScheme/cac-TaxScheme/cbc-ID/) | Tax scheme code | The scheme of the TAX identifier. | Required for interoperability |
| [IBT-027](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-Party/cac-PartyLegalEntity/cbc-RegistrationName/) | Seller name | The full formal name by which the Seller is registered in the national registry of legal entities or as a Taxable person or otherwise trades as a person or persons. | Mandatory |
| [IBT-030](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-Party/cac-PartyLegalEntity/cbc-CompanyID/) | Seller legal registration identifier | An identifier issued by an official registrar that identifies the Seller as a legal entity or person. | Mandatory |
| [IBT-041](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-Party/cac-Contact/cbc-Name/) | Seller contact point | A contact point for a legal entity or person. | Recommended |
| [IBT-042](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-Party/cac-Contact/cbc-Telephone/) | Seller contact telephone number | A phone number for the contact point. | Recommended |
| [IBT-043](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-Party/cac-Contact/cbc-ElectronicMail/) | Seller contact email address | An e-mail address for the contact point. | Required for interoperability |
| [IBG-07](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/) | BUYER | A group of business terms providing information about the Buyer. | Mandatory |
| [IBT-049](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cbc-EndpointID/) | Buyer electronic address | Identifies the Buyer’s electronic address to which the invoice is delivered. | Mandatory |
| [IBT-055](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-PostalAddress/cbc-Country/cbc-IdentificationCode/) | Buyer country code | A code that identifies the country. | Mandatory |
| [IBT-044](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-PartyLegalEntity/cbc-RegistrationName/) | Buyer name | The full name of the Buyer. | Mandatory |
| [IBT-045](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-PartyName/cbc-Name/) | Buyer trading name | A name by which the Buyer is known, other than Buyer name (also known as Business name). | Conditional |
| [IBT-047](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-PartyLegalEntity/cbc-CompanyID/) | Buyer legal registration identifier | An identifier issued by an official registrar that identifies the Buyer as a legal entity or person. | Mandatory |
| [IBT-056](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-Contact/cbc-Name/) | Buyer contact point | A contact point for a legal entity or person. | Recommended |
| [IBT-057](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-Contact/cbc-Telephone/) | Buyer contact telephone number | A phone number for the contact point. | Recommended |
| [IBT-058](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-Contact/cbc-ElectronicMail/) | Buyer contact email address | An e-mail address for the contact point. | Required for interoperability |
| [IBT-083](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-RemittanceInformation/cbc-Reference/) | Remittance information | A textual value used for payment routing or to establish a link between the payment and the Invoice. | Required for interoperability |
| [IBT-084](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PaymentMeans/cbc-PayeeFinancialAccount/cbc-ID/) | Payment account identifier | A unique identifier of the financial payment account, at a payment service provider, to which payment should be made. | Required for interoperability |
| [IBT-085](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PaymentMeans/cbc-PayeeFinancialAccount/cbc-Name/) | Payment account name | The name of the payment account, at a payment service provider, to which payment should be made. | Required for interoperability |
| [IBT-086](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PaymentMeans/cac-PayeeFinancialAccount/cac-FinancialInstitutionBranch/cac-FinancialInstitution/cbc-ID/) | Payment service provider identifier | An identifier for the payment service provider where a payment account is located, such as a bank identifier code (BIC) or financial institution branch. | Required for interoperability |
| [IBG-20](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AllowanceCharge/) | DOCUMENT LEVEL ALLOWANCES | A group of business terms providing information about allowances applicable to the Invoice as a whole. | Recommended |
| [IBG-21](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AllowanceCharge/) | DOCUMENT LEVEL CHARGES | A group of business terms providing information about charges and taxes other than TAX, applicable to the Invoice as a whole. | Recommended |
| [IBT-110](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-TaxTotal/cbc-TaxAmount/) | Invoice total TAX amount | The total TAX amount for the Invoice. | Mandatory |
| [IBG-23](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-TaxTotal/) | TAX BREAKDOWN | A group of business terms providing information about TAX breakdown by different categories, rates and exemption reasons. | Mandatory |
| [IBG-22](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-RequestedMonetaryTotal/) | DOCUMENT TOTALS | A group of business terms providing the monetary totals for the Invoice. | Mandatory |
| [IBG-25](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/) | INVOICE LINE | A group of business terms providing information on individual Invoice lines. | Mandatory |
| [IBT-126](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-ID/) | Invoice line identifier | A unique identifier for the individual line within the Invoice. | Mandatory |
| [IBT-129](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-InvoicedQuantity/) | Invoiced quantity | The quantity of items (goods or services) that is charged in the Invoice line. | Mandatory |
| [IBT-130](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-InvoicedQuantity/unitCode/) | Invoiced quantity unit of measure code | The unit of measure that applies to the invoiced quantity. | Mandatory |
| [IBT-131](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-LineExtensionAmount/) | Invoice line net amount | The total amount of the Invoice line (before tax). | Mandatory |
| [IBT-132](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-OrderLineReference/cbc-LineID/) | Referenced purchase order line reference | An identifier for a referenced line within a purchase order, issued by the Buyer. | Conditional |
| [IBG-27](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-AllowanceCharge/) | INVOICE LINE ALLOWANCES | A group of business terms providing information about allowances applicable to the individual Invoice line. | Mentioned |
| [IBG-28](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-AllowanceCharge/) | INVOICE LINE CHARGES | A group of business terms providing information about charges and taxes other than TAX applicable to the individual Invoice line. | Mentioned |
| [IBG-31](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-Item/) | ITEM INFORMATION | A group of business terms providing information about the goods and services invoiced. | Mandatory |
| [IBT-154](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-Description/) | Item description | A description for an item. | Required for interoperability |
| [IBT-153](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-Name/) | Item name | A name for an item. | Mandatory |
| [IBT-156](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-BuyersItemIdentification/cbc-ID/) | Item Buyer's identifier | An identifier, assigned by the Buyer, for the item. | Mentioned |
| [IBT-155](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-SellersItemIdentification/cbc-ID/) | Item Seller's identifier | An identifier, assigned by the Seller, for the item. | Mentioned |
| [IBT-157](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-StandardItemIdentification/cbc-ID/) | Item standard identifier | An item identifier based on a registered scheme. | Mentioned |
| [IBG-30](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-TaxTotal/) | LINE TAX INFORMATION | A group of business terms providing information about the TAX applicable for the goods and services invoiced on the Invoice line. | Mandatory |
| [IBG-29](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-PricingReference/) | PRICE DETAILS | A group of business terms providing information about the price applied for the goods and services invoiced on the Invoice line. | Mandatory |

## Legend

- **Mandatory**: Required by the PINT A2C Billing specification  
- **Recommended for Interoperability**: Strongly advised for cross-system compatibility  
- **Conditional**: Required depending on context (ICIPS guidance)  
- **Required for Interoperability**: Needed for consistent data exchange  
- **Mentioned**: Referenced but not formally required  
