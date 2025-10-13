---
title: Invoice content A-NZ industry practice statement
---

<p align="center">
  <img src="assets/header.jpg" alt="Header Image" width="100%">
</p>

# A-NZ industry practice statement 

# Invoice content

📄 File available for download [here](Update the link)

**Version history**

| Date&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Version | Changes |
|----|----|----|
| 1 October 2021 | 1.1 | Initial release |
| 28 February 2022 | 1.1 | Minor corrections |
| 7 July 2025 | 2.0 | Edited to simplify language and clarify meaning. Updated rating names and descriptions. Added buyer contact email and invoice note as *Required for interoperability*. Prioritised seller contact email over seller contact name and telephone. Added seller trading name as *Recommended*. Deprioritised buyer trading name. Removed payment terms (in favour of payment due date). |

---

## Background

Experiences using Peppol invoicing (or eInvoicing) indicate that sending
only the mandatory data elements required in the [PINT A-NZ Billing
specification](https://docs.peppol.eu/poac/aunz/pint-aunz/) doesn’t give
medium to large business and government buyers enough information to be
able to process and pay eInvoices. In some cases, buyers receive less
invoice data using Peppol than from other channels (such as emailed
PDF).

Providing enough invoice data to support automated invoice processing is
critical to achieve efficiency and savings for buyers and faster
payments for sellers, which are core drivers for Peppol adoption. Beyond
invoice processing automation, buyers may also require this information
to support data processing, data integrity, fraud, risk and quality
checks, or to support industry specific requirements such as dangerous
goods labels and identification.

---

## Purpose

This document provides guidance for digital service and software
providers (collectively referred to here as digital service providers or
DSPs) for both sellers and buyers for managing invoice data to ensure
buyers – particularly medium to large business and government buyers –
can process eInvoices smoothly and efficiently. It was developed in
partnership with the Australian and New Zealand Peppol Authorities and
Digital Service Providers Australia and New Zealand (DSPANZ) through
consultation with the Australian and New Zealand Peppol communities.

It helps sending DSPs and those providing services to sellers to:

- build product sending capability to support data elements that are
  commonly required by medium to large buyers to ensure eInvoices can be
  processed and paid efficiently

- understand how invoice data is used to support common accounts payable
  processes particularly in medium to large buyers, and the implications
  of not including particular invoice elements

- develop eInvoicing product design to better support buyer automation
  and an improved client experience.

It helps receiving DSPs and those providing services to buyers to:

- appreciate that some sellers may face limitations in the invoice data
  they can provide from their software

- support buyers through change management and process redesign required
  to accommodate for such limitations to prevent rejection of otherwise
  compliant Peppol invoices

- support buyers to balance their invoice processing needs against the
  costs of data collection and exchange for sellers to determine if this
  data can and should be provided, noting relevant industry specific
  considerations.

---

## Related documents

DSPs must utilise the [PINT A-NZ Billing
specification](https://docs.peppol.eu/poac/aunz/pint-aunz/) in
conjunction with this document. You should also consider the following
additional guidance when developing your eInvoicing solutions:

- [Peppol A-NZ guidance
  documents](https://github.com/A-NZ-PEPPOL/Guidance-documents) hosted
  on Github, including:

  - Payment means and use of the UNCL4461 code list

  - Use of tax category codes in Australia

- [Peppol A-NZ industry practice
  statements](https://github.com/A-NZ-PEPPOL/A-NZ-Industry-Practice-Statements)
  hosted on Github, including:

  - Guidance and implementation options for specific billing scenarios

  - Consistent data mapping

  - Understanding and managing attachments

  - Communicating invoice status.

<span id="_Principles" class="anchor"></span>

---

## Principles

The overarching principles for DSPs in relation to Peppol invoice
content are:

When the seller (corner 1, or C1)[^1] has relevant data, it should be
provided in the eInvoice. At a minimum, sellers should ensure that all
relevant data that would otherwise be contained in a PDF invoice is also
available in the eInvoice.

All data should be placed in the semantically correct Peppol invoice
elements as defined in the [PINT A-NZ Billing
specification](https://docs.peppol.eu/poac/aunz/pint-aunz/).

Buyers and their access points should not reject eInvoices that comply
with the Peppol invoice specification. If eInvoices fail non-Peppol
business rule validation (such as purchase order (PO) format checks or
3-way matching etc.), buyers should use an invoice response message[^2]
or communicate out of band.

Buyers should search eInvoices for required data as it may not be in the
expected data element.

Buyers should consider the sellers’ potential software limitations and
balance their chosen information requirements with the burden on sellers
to provide bespoke information.

---

## Information you should include in an eInvoice

In addition to the mandatory Peppol data elements set out in the [PINT
A-NZ Billing
specification](https://docs.peppol.eu/poac/aunz/pint-aunz/), the
elements below are commonly required for interoperability.

The PINT A-NZ Billing specification is designed to support a broad range
of circumstances. This means choices must be made about which of the
hundreds of possible elements to include.

The elements detailed in this document are necessary to meet the common
needs of medium to large business and government entities,
notwithstanding additional industry or use-case-specific requirements.
Including them helps ensure a smooth invoicing process and greater
certainty of prompt payment in the most common trading circumstances.

Element ratings are determined by how commonly they are required to
ensure an eInvoice can be processed and paid by buyers.

The rating names refer to how important an element is for
interoperability – that is, effective processing and payment of an
invoice by medium to large enterprise and government buyers.

---

## Invoice content element ratings

<table>
<colgroup>
<col style="width: 18%" />
<col style="width: 81%" />
</colgroup>
<tbody>
<tr>
<td>Name</td>
<td>Description</td>
</tr>
<tr>
<td>Required for interoperability</td>
<td><p>These elements are frequently required by buyers and are vital to
enable automatic invoice processing and/or completion of integrity
checks.</p>
<p>Sellers are often expected to provide these elements in an eInvoice,
noting they are not mandated for every eInvoice or seller/buyer
relationship. Without them, the invoice is highly likely to be rejected
or managed through a manual exception process, which delays
payment.</p></td>
</tr>
<tr>
<td>Recommended</td>
<td><p>These elements help buyers achieve quicker and more
straightforward processing such as 3-way matching or vendor
verification; however, they are less commonly required for automation.
Some of the information in this group may only be applicable in certain
circumstances such as auditing or tax compliance.</p>
<p>Sellers should include these elements in an eInvoice whenever
possible.</p>
<p>Buyers should be aware that not every sending solution will be able
to include all of these recommended elements. Some sellers may not be
able to provide the data at all, while others may provide it in
different eInvoice elements (such as invoice note).</p></td>
</tr>
<tr>
<td>Conditional</td>
<td><p>Conditional elements may be included in the interests of
supporting buyer processing by including rich business information where
possible. However:</p>
<ul>
<li><p>Buyers are not expected to be able to process this information
automatically, and those who cannot utilise it might ignore it.</p></li>
<li><p>Buyers should also be aware that some sending solutions will not
be able to include this information at all, while others may provide it
in different eInvoice elements (such as invoice note).</p></li>
<li><p>This information may be a known requirement in some
industries.</p></li>
</ul></td>
</tr>
</tbody>
</table>

Rated elements are detailed below. See the separate
[appendix](https://raw.githubusercontent.com/A-NZ-PEPPOL/A-NZ-Industry-Practice-Statements/main/Invoice_content_IPS_Appendix–Mandatory_and_rated_element.xlsx)
for a tabulated list of these rated elements as well as mandatory
elements of the [PINT A-NZ Billing
specification](https://docs.peppol.eu/poac/aunz/pint-aunz/).

---

## Required for interoperability

### 1. Payment due date

The Peppol invoice specification requires either [payment due
date](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-DueDate/)
or [payment
terms](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PaymentTerms/cbc-Note/)
to be provided in an eInvoice.

Use payment due date (unless payment terms is specifically required) as
this information is structured and easier for systems to automatically
process.

### 2. Seller GST identifier

It is a legal requirement in Australia that when a GST branch makes a
taxable sale, the branch number (or [seller tax
identifier](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingSupplierParty/cac-Party/cac-PartyTaxScheme-1/cbc-CompanyID/))
must be provided (ABN and 3-digit branch number).

New Zealand requires the GST number if the supplier is GST registered.
Note that the New Zealand Business Number (NZBN) is **not** the GST
number.

### 3. Seller contact email

The Peppol invoice specification includes 3 child elements for seller
contact details: email address, name, and phone.

Provide an [email
address](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingSupplierParty/cac-Party/cac-Contact/cbc-ElectronicMail/)
to make it easier for the buyer to contact the seller if there are any
issues with the eInvoice.

Name and telephone are also recommended – see [14. Seller contact name
and telephone](#seller-contact-name-and-telephone).

### 4. Buyer contact email

Some buyers cannot process seller invoices without buyer contact
details. They use this information to route the invoice internally to
the person or team responsible for approving the invoice or receipting
the supplied goods or services.

Most buyers will require the [buyer contact email
address](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-Contact/cbc-ElectronicMail/).

Buyer contact name and telephone are also recommended – see [15. Buyer
contact name and telephone](#buyer-contact-name-and-telephone).

### 5. Payee financial account

When used, provide payee bank account ([credit
transfer](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PaymentMeans/cac-PayeeFinancialAccount/))
details on the eInvoice. This is critical for fraud risk management and
internal control processes.

<img src="./media/media/image1.png"
style="width:0.27559in;height:0.27559in" /> This should not be relied on
to update a buyer’s vendor master data unless the buyer has
independently verified the information to be correct. Buyers are
expected to have internal controls and/or approval processes in place to
update payment details. Also note that sending solutions may also
support other payment options within the Peppol invoice specification.

### 6. Item description

In addition to an [item
name](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-Item/cbc-Name/)
(which is mandatory for each invoice line), provide an [item
description](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-Item/cbc-Description/)
to help buyers with goods receipting and invoice approval processes.

<img src="./media/media/image1.png"
style="width:0.27559in;height:0.27559in" /> Item description is one of
several available [item
information](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-Item/)
elements available in a Peppol invoice. In some scenarios it may be
appropriate to use other elements. For example, a seller stock keeping
unit (SKU) should be included in the [sellers item
identification](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-Item/cac-SellersItemIdentification/)
element, while a standard identifier like a global trade item number
(GTIN) should be included in the [standard item
identification](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-Item/cac-StandardItemIdentification/)
element. If a buyer item ID is used, this should be included in the
[buyers item
identification](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-Item/cac-BuyersItemIdentification/)
element.

### 7. Reference number

Five invoice elements support the use of reference numbers used by
buyers for data matching and to route invoices to the correct person or
team to approve an invoice:

purchase order (PO) number ([purchase order
reference](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-OrderReference/cbc-ID/))\*

buyer-assigned reference ([buyer
reference](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-BuyerReference/))\*
– for example, a code assigned to an individual, team, branch, or
geolocation

contract number ([contract
reference](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-ContractDocumentReference/cbc-ID/))

project number ([project
reference](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-ProjectReference/cbc-ID/))

tender number ([tender or lot
reference](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-OriginatorDocumentReference/cbc-ID/)).

\*It is mandatory in the PINT A-NZ Billing specification for sellers to
include either a PO number or buyer reference with a Peppol invoice.
Where neither are required, a default value of ‘BUYER_REFERENCE’ or ‘NA’
should be used in the buyer reference element. Refer to section 8 of the
[consistent data mapping industry practice
statement](https://raw.githubusercontent.com/A-NZ-PEPPOL/A-NZ-Industry-Practice-Statements/main/A-NZ%20ASWG_Consistent%20Data%20Mapping%201.0.docx)
for more details.

The buyer will need to tell the seller which reference number(s) should
be quoted on the invoice so that it can be processed efficiently. PO and
contract numbers are most used by buyers to help them match invoices
with approved spending.

When opting for a buyer reference, the buyer should select a value that
can be easily recognised by its systems and used to automatically
process or direct the invoice to the correct person or business team.

There may be instances where the seller enters a reference number into a
different element on the eInvoice. Buyers’ systems should provide
flexibility to search all elements for the reference number (in
accordance with [principle 4](#_Principles)). This process should
ideally be automated.

Sending DSPs should support the ability to include any combination of
reference numbers and avoid making any 2 references mutually exclusive.

<img src="./media/media/image1.png"
style="width:0.27559in;height:0.27559in" /> Peppol also supports
referencing one or multiple preceding invoices ([preceding invoice
reference](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-BillingReference/cac-InvoiceDocumentReference/cbc-ID/))
– for example, when an invoice adjusts or replaces an invoice that was
sent previously.

### 8. Remittance information

The seller should give the buyer [remittance
information](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-PaymentMeans/cbc-PaymentID/)
such as a reference number which the buyer can use on their payment or
remittance – for example, a client reference number. This helps the
seller to reconcile a payment with a particular invoice.

It is common for the invoice number to be used for this purpose.

### 9. Invoice attachments

In certain scenarios, buyers require [additional supporting
documents](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AdditionalDocumentReference-2/)
to be sent as attachments to help process invoices (for example, labour
hire timesheets).

The Peppol invoice specification supports several file formats, as
defined in the [media types code
list](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/codelist/MimeCode/).
DSPs should consider their clients’ business needs when determining what
features they need to offer, including limits on the number and size of
attachments they can send and receive and how end users will access
those attachments.

The A-NZ Peppol GitHub has guidance about [understanding and managing
attachments in eInvoices and eCredit
Notes](https://raw.githubusercontent.com/A-NZ-PEPPOL/A-NZ-Industry-Practice-Statements/main/A-NZ%20Industry%20Practice%20Statement_Understanding%20and%20managing%20attachments%20in%20eInvoices%20and%20eCredit%20Notes_v1.docx).

The Peppol invoice specification supports the inclusion of URLs within
invoices, but buyers may be constrained by security limitations and may
not be able to access them.

<img src="./media/media/image1.png"
style="width:0.27559in;height:0.27559in" /> Attachments should only be
included to support the processing of an invoice. Other documents not
directly related to invoice processing should not be attached. Attaching
a copy of the invoice in another format (such as PDF) that includes only
the data within the eInvoice XML is discouraged. It may be acceptable
when additional value-add information is included (such as to comply
with regulations or to provide usage trend graphs). Where a sending
solution is incapable of including required information in the XML part
of the eInvoice, or a receiving solution can’t allow an end user to
access required information in the eInvoice, and where the information
is contained in the attachment, this may be done with agreement between
trading parties.

### 10. Invoice note

Senders frequently need to include free-text information relevant to the
whole invoice. An example of this is the inclusion of legal or
contractual terms that apply to the transaction. Additionally, the
[invoice
note](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cbc-Note/)
helps buyers with more basic software solutions – particularly small
businesses – to receive data that would not otherwise be displayed in
their receiving solutions. Sellers should be able to use the invoice
note to send information that they know the buyer can’t otherwise
receive.

Invoice note should be used according to the Peppol design. All data
should be correctly mapped to a dedicated invoice element where one
exists for that data.

---

## Recommended

### 11. Discount or charge

Peppol supports document-level
[allowances](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AllowanceCharge-1/)
(discounts) and
[charges](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AllowanceCharge-2/)
as well as line-level
[allowances](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-AllowanceCharge-1/)
and
[charges](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-AllowanceCharge-2/).
These elements support automatic processing.

Sellers should attempt to provide allowance or charge information on the
invoice even if their software doesn’t support the semantic elements
designed for it (in accordance with [principle 1](#_Principles)). Buyers
should appreciate some sellers can’t populate these elements and so
should look for that information elsewhere (in accordance with
[principle 4](#_Principles)). Document-level allowances and charges
could appear as additional line items while line-level allowances and
charges may be rolled into the unit price and details provided in the
invoice note (see [10. Invoice note](#invoice-note)) or item description
(see [6. Item description](#item-description)).

### 12. Seller postal address

[Seller postal
address](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingSupplierParty/cac-Party/cac-PostalAddress/)
is useful where multiple branches or businesses trade under the same ABN
or NZBN. For reference and to avoid format inconsistences, use the
[Australia Post addressing
guidelines](https://auspost.com.au/sending/guidelines/addressing-guidelines)
and [New Zealand Post
guidelines](https://www.nzpost.co.nz/business/shipping-in-nz/bulk-mail/address-layout-standards).

<img src="./media/media/image1.png"
style="width:0.27559in;height:0.27559in" /> The [seller country
code](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingSupplierParty/cac-Party/cac-PostalAddress/cac-Country/cbc-IdentificationCode/)
is mandatory according to the Peppol invoice specification.

### 13. Seller trading name 

[Seller trading
name](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingSupplierParty/cac-Party/cac-PartyName/cbc-Name/)
is recommended if it differs from the seller’s legal name and helps the
buyer identify the seller.

### 14. Seller contact name and telephone

Providing the seller contact
[name](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingSupplierParty/cac-Party/cac-Contact/cbc-Name/)
and [telephone
number](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingSupplierParty/cac-Party/cac-Contact/cbc-Telephone/)
on the invoice will make it easier for the buyer to contact the seller
if there are any issues.

Note that including the seller contact email is required in most cases –
see [3. Seller contact email](#seller-contact-email).

### 15. Buyer contact name and telephone

Some buyers rely upon the [buyer contact
point](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-Contact/cbc-Name/)
(name) and [buyer contact telephone
number](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-Contact/cbc-Telephone/)
to route messages to the appropriate person or team for approval or
receipting the supplied goods or services.

Note that including the buyer contact email is required in most cases –
see [4. Buyer contact email](#buyer-contact-email).

---

## Conditional

### 16. Purchase order line reference

The Peppol invoice specification supports referencing to a PO line for
each invoice line item to support PO line-level matching ([purchase
order line
reference](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-InvoiceLine/cac-OrderLineReference/cbc-LineID/)).
This is important in some industries, particularly where purchase orders
are heavily relied upon.

### 17. Buyer trading name

Some buyers may use the [buyer trading
name](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-PartyName/cbc-Name/)
for internal processing and verification, and sellers should be able to
provide this when buyers request it.

<img src="assets/i.JPG"
style="width:0.1in;height:0.1in" /> This is different from
[buyer
name](https://docs.peppol.eu/poac/aunz/pint-aunz/trn-invoice/syntax/cac-AccountingCustomerParty/cac-Party/cac-PartyLegalEntity/cbc-RegistrationName/),
which is mandatory.

---

[^1]: The Peppol network operates in a 4-corner model in which corner 1
    (C1) is the seller, C2 is the seller’s access point, C3 is the
    buyer’s access point and C4 is the buyer. [Read more about the
    Peppol
    network](https://www.ato.gov.au/businesses-and-organisations/einvoicing/peppol#ato-ThePeppolnetwork)
    and the 4-corner model on the ATO website.

[^2]: Some buyers incorrectly use message level response (MLR) instead
    of [invoice
    response](https://docs.peppol.eu/poacc/upgrade-3/2024-Q4/profiles/63-invoiceresponse/).
    Invoice response ‘provides the Seller… with information about the
    status of his invoice or credit note and provides the Buyer… with
    efficient means for keeping the Seller informed’ (section [2.1
    Invoice Response message in
    general](https://docs.peppol.eu/poacc/upgrade-3/2024-Q4/profiles/63-invoiceresponse/#principles)).
    In contrast, ‘a key nature of \[MLRs\] is that they report on the
    message content on the basis of the technical specifications that
    apply’ (section [2.1 Message Level Response message in
    general](https://docs.peppol.eu/poacc/upgrade-3/2024-Q4/profiles/36-mlr/#message-level-response-message-in-general)).
