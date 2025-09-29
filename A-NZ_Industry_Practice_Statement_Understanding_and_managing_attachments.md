---
title: IPS: Understanding and managing attachments in eInvoices and eCredit Notes
---

<p align="center">
  <img src="assets/header.jpg" alt="Header Image" width="100%">
</p>

# A-NZ PEPPOL INDUSTRY PRACTICE STATEMENT

## Understanding and managing attachments in eInvoices and eCredit Notes

Version: 1.0

Publication Date: May 2023

### PURPOSE 

This document has been developed by the Attachment focus group (the
group) which was formed as part of the [A-NZ Peppol All Stakeholders
Working
Group](https://www.dspanz.org/committees/peppol/anz-peppol-all-stakeholders-working-group/)
(ASWG).

It aims to develop a better and shared understanding of:

- how attachments are supported with Peppol eInvoices and other
  eProcurement transactions;

- how attachments are provided in different use cases;

- the varying capabilities of solutions (including Access Point
  providers and end user solutions) to support attachments.

This document intends to promote visibility across the A-NZ Peppol
community, promote consistent support and management of attachments in
the Peppol network, and support end users to make informed decisions
when implementing Peppol.

This document summarises key findings and recommendations for sending,
receiving and/or managing attachments in Peppol which apply to eInvoices
as well as other eProcurement transactions. The document also provides
data mapping guidance for embedded attachments in Peppol eInvoices,
which was proposed by the [Consistent Data Mapping focus
group](https://www.dspanz.org/committees/peppol/anz-peppol-all-stakeholders-working-group/consistent-data-mapping-focus-group/).

**NOTE**: This is a living document that may be updated as the A-NZ
and/or as the global Peppol market matures, as new challenges arise, or
as Peppol standards evolve.

### CONTEXT

Although Peppol has specified the minimum size and format of attachments
that Peppol Access Point providers must support for eInvoices and
eCredit Notes, there are varied levels of support by end users’ business
management software (BMS, i.e. end users’ accounting/FMIS/ERP
solutions). For example, some solutions may not be able to support large
file sizes, or only support a single attachment per invoice (where
Peppol allows multiple attachments per invoice or credit note).

This has caused some issues and confusion for end users. It was agreed
that better understanding of Peppol attachments and solution
capabilities is required to promote consistent support and to maximise
positive client experiences.

### KEY FINDINGS AND GUIDANCE

#### What is supported by Peppol

The Peppol A-NZ Invoice (and Credit note) specification supports the
following for embedded attachments:

**Format/Type:** supported attachment formats include PDF, text/CSV,
image. Refer to the [Code
List](https://docs.peppol.eu/poacc/billing/3.0/codelist/MimeCode/) for
list of supported attachment types.

**Size:** Peppol [SLA
requirements](https://openpeppol.atlassian.net/wiki/download/attachments/2891481194/Peppol%20SLA%20Requirements_v1.0_APPROVED%202022.02.15.pdf?api=v2)
states that, for ‘post-award’ transactions (eInvoice and eProcurement),
a Peppol AP provider must support messages up to 100MB which includes
both the XML message and embedded attachments.

**Number of attachments per transaction:** The Peppol eInvoicing
standard allows for multiple attachments per invoice, which is subject
to the overall message size a Peppol Service Provider can support.

**URL for attachments:**

eInvoices support the inclusion of URL/URIs for end users to access
supporting documents (rather than sending as embedded attachments). End
users should be aware of various organisation security requirements or
system restrictions for accessing and/or processing URI/URLs.

The use of URI/URL is not common across the network in Australia or New
Zealand when this document is developed.

#### Recommended Mapping of Attachment metadata in an A-NZ Peppol eInvoice

When including attachment(s) in an eInvoice, a number of UBL XML fields
need to be populated.

Mapping guidance for embedded attachments can be found in the
[consistent data mapping
guidance](https://www.dspanz.org/media/website_pages/committees/peppol/anz-peppol-all-stakeholders-working-group/consistent-data-mapping-focus-group/A-NZ-ASWG_Consistent-Data-Mapping-1.0.pdf),
which was proposed by the [Consistent Data Mapping Focus
Group](https://www.dspanz.org/committees/peppol/anz-peppol-all-stakeholders-working-group/consistent-data-mapping-focus-group/)
and reviewed by this group.

Note: the data mapping guidance document can be found at both the
[DSPANZ
website](https://www.dspanz.org/committees/peppol/anz-peppol-all-stakeholders-working-group/consistent-data-mapping-focus-group/)
and the [A-NZ Peppol Github
site](https://github.com/A-NZ-PEPPOL/A-NZ-Industry-Practice-Statements/blob/main/A-NZ%20ASWG_Consistent%20Data%20Mapping%201.0.docx).

#### Use cases

The group discussed a number of scenarios where attachments may be
included in an eInvoice.

- Attaching a PDF of a visual representation of the bill

The Peppol eInvoicing standard is intended to enable and maximise
automation. The attachment function is available to support better
invoice processing, and, as per the [Peppol BIS
Billing](https://docs.peppol.eu/poacc/billing/3.0/bis/#_binary_objects),
the attachment shouldn’t be purely a copy of data within the XML
message.

The group supported this position and noted that attached invoices (e.g.
PDF) commonly include additional information such as the seller’s
branding, contact information such as website URL, and other support
information.

In some industry sectors, such as utilities, bills (PDF or paper)
commonly include rich information and serve multiple purposes in
addition to a request for payment.

For example, it is common for utility bills to also act as a statement
showing net account balance, overdue amounts, marketing / better deals
information, or past usage analysis. In this case, bills are used beyond
the accounts payable function and customers (buyers) may have adapted
their business processes over time to utilise the additional
information.

Therefore, it is sensible for sellers to continue providing existing PDF
bills as eInvoice attachments, where the eInvoice XML will only contain
accounts payable data to support automated accounts payable processes.
This will support their trading partners with their existing business
processes and needs while maximising automation, and minimise sellers’
change effort.

Invoice receivers (buyers) also have different processes and system
capabilities to support and enhance automation. During the early stages
of the change process, some receivers (buyers) may prefer to have a
visual representation of an eInvoice to support internal processes, for
example, they may initially rely on human effort to view and verify
invoices.

Including an invoice attachment will ease the transitional and change
impact for the receivers (buyers), but reliance on a PDF version of the
bill for invoice processing is expected to reduce over time as buyers’
systems and processes adapt.

- Attaching additional information to meet buyers’ invoice processing
  needs

Depending on the nature of the invoiced goods/services, buyers sometimes
require specific information to support goods receipt, invoice
validation and approval.

For example,

- Labour hire invoices commonly include timesheet(s) as attachments,
  which are required by buyers to verify service hours; or

- For utility bills, some large buyers may request detailed usage
  information in specific formats, to assist with internal analysis and
  cost allocation.

A seller and buyer may also reach mutual agreement on invoice
attachments. For example, a buyer may have multiple sites or stores.
Services delivered to a particular site may need to be verified locally
by a site manager, e.g. in the form of signing a paper work order. The
seller then needs to provide the ‘evidence’, e.g. a scanned image of the
document with the signature, as an attachment when invoicing the buyer’s
accounts payable team.

#### Solution capability overview

The group gathered information from participants on BMS solutions’
capabilities to support attachments:

- PDF is supported by most, if not all, BMS products. Comma-separated
  values files (CSV) and Excel are the next most commonly supported
  attachment format.

- Some products only support one attachment per eInvoice. Other products
  support up to five attachments per eInvoice.

- Attachment size limits range from 5-20MB per message for software
  products supporting the SME market. The limit may be applied to
  individual attachment or total size when multiple attachments are
  allowed.

- Not all sending solutions allow an end user to provide metadata
  (filename and optional document description) for uploaded attachments.

- The group noted that commonly sellers’ BMS solutions will provide
  attachments as separate files (e.g. via proprietary API) but sometimes
  sellers may provide the Peppol eInvoice UBL XML file with embedded
  attachments.

- Approximately 50% of BMS providers who responded to a DSPANZ survey
  confirmed that outbound attachments will be virus scanned (noting that
  other security controls may be employed).

#### General principles and guidelines

During the discussions, the group agreed on a number of high-level
principles and guidelines for dealing with attachments.

1.  It is expected that Peppol Serivce Providers (SPs) should be able to
    support the full functionality for attachments, including the format
    and quantity of attachments, as well as appropriate attachment
    metadata. It is noted that end users’ native BMS solutions may have
    different level of support.

2.  Where a document can be exchanged between the trading partners as a
    stand-alone eProcurement transaction, e.g. a Peppol order or
    despatch advice), it should not be included as an attachment.

3.  Attachments should contain necessary and supplementary information
    which supports buyers’ processing needs.

4.  Virus scanning for attachments

- The Peppol APs (both sending and receiving), as per section 10.3 and
  17.1 of the Peppol Service Providers agreement, must have implemented
  industry best practices and measures to avoid security issues, such as
  illicit use, malicious code, viruses, computer intrusions,
  infringements or illegal tampering of data etc.

- End users’ BMS solutions are also expected to implement industry best
  practice security measures. The use of Peppol should not reduce or
  replace existing security measures.

Where the full UBL message is formulated by the sender (seller) by its
BMS solution, the sending AP might share some of the
responsibility/processes for security assurance.

5.  Communicating delivery status to end users

The receiving Peppol AP (C3) and C4 should have an agreement and process
to manage delivery issues, e.g. if an attachment cannot be delivered to
C4.

6.  Peppol APs and BMS providers should provide reasonable support /
    education to end users to understand business requirements and
    system restrictions for attachments.

### CONSIDERATIONS FOR END USERS

Considering the varying capabilities and BMS service offerings, this
section aims to provide some considerations to assist end users to
assess risks and make informed decisions for managing eInvoicing
attachments.

- **Peppol AP provider and the DSP solutions’ capabilities to support
  attachments:**

  - Constraints for sending and receiving eInvoice attachments e.g. size
    limit, format, and quantity of attachments per eInvoice. For
    example, some service offerings may have size limits of 20MB per
    file.

  <!-- -->

  - Process to convert an attachment to a supported format (e.g.
    converting a Word document to PDF).

  - How embedded attachments will be detached from the eInvoice (XML)
    and made accessible to an end user.

  - Where will the attachments be stored and/or archived.

  - Costs and constraints (e.g. total size and length of time) if
    storing attachments in a cloud solution.

<!-- -->

- **Virus scanning and other security controls for attachments  **
  Whether the chosen provider(s) have implemented industry best
  practices and measures, and alignment with the end-user’s
  organisational security standards.

- **Process to manage exceptions / support and education**  
  An appropriate process should be developed and agreed with the
  relevant system / service providers to receive notification and/or
  manage exceptions, for example:

  - An attachment does not pass security scanning (e.g. contains a
    virus)

  - An attachment is not in a supported format

  - An attachment is over the size limit of the receiving BMS system

- **Data in an attached invoice versus in eInvoice/XML**

  - Trading entities (sellers and buyers) have the obligation to ensure
    that the invoice is valid and compliant to the requirements by the
    A-NZ tax authorities.  
    Australia: [Tax invoices \| Australian Taxation Office
    (ato.gov.au)](https://www.ato.gov.au/business/gst/tax-invoices/)

> New Zealand: [Tax invoices for GST
> (ird.govt.nz)](https://www.ird.govt.nz/gst/tax-invoices-for-gst)

- Depending on the business processes, receivers (buyers) may use either
  or both the attachment and eInvoice XML data for various accounting
  and/or business purposes.

- The group acknowledged that sometimes the attached invoice and XML are
  generated in different systems. Senders (sellers) need to ensure that
  there is no conflict between the attachment and the eInvoice/ XML.

#### 

### Version history

| **Version** | **Date** | **Change** |
|----|----|----|
| Initial draft | February 2023 | Initial draft based on working group discussion |
| 1.0 | May 2023 | Distributed to and reviewed by the A-NZ Peppol Stakeholders Working Group (ASWG). |
