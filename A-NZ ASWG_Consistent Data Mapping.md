---
title: Guidance and Recommendations for Consistent Data Mapping
---

<p align="center">
  <img src="assets/header.jpg" alt="Header Image" width="100%">
</p>

# A-NZ Industry Practice Statement
**Guidance and Recommendations for Consistent Data Mapping**  
**Version:** 1.0  
**Publication Date:** 9 September 2022  

---

## PURPOSE

This document aims to assist with consistent interpretation and
implementation of the [<u>A-NZ invoice
specification</u>](https://github.com/A-NZ-PEPPOL/A-NZ-PEPPOL-BIS-3.0).

A number of mapping questions and issues were raised and addressed by
the Data Mapping focus group (the group), which was formed as part of
the [<u>A-NZ Peppol All-Stakeholders Working
Group</u>](https://www.dspanz.org/committees/peppol/anz-peppol-all-stakeholders-working-group/consistent-data-mapping-focus-group/)
and represents end-users and solution providers (access points and
providers of accounting solutions/ERP/FMIS).

This document has been developed by the group and includes a problem
statement, a summary and recommended approach for each mapping issue,
and UBL examples.

**Note:**

- This is a living document that will be updated as further data mapping
  resolutions are determined.

- The UBL samples provided through this document are non-normative and
  the specification takes precedence. Please refer to the principles and
  guidance (Recommendations).
  
---

## CONTEXT

Issues and questions were raised that invoice data is not always
conveyed appropriately and caused processing issues (delays or
rejections). Issues include:

- Invoice data is not mapped according to its semantic meaning.

- The same invoice data is mapped differently by different sending
  entities.

- Lack of guidance/consistency for how complex invoice information
  should be conveyed (e.g., utility bills).

The full Problem Statement, examples and descriptions of data mapping
issues can be [<u>found here</u>](https://www.dspanz.org/media/website_pages/committees/peppol/anz-peppol-all-stakeholders-working-group/consistent-data-mapping-focus-group/Problem-Statement-Consistent-Data-Mapping.pdf).

---

## PRINCIPLES

Consistent mapping and usage of the specification is key to ensure automation and realisation of network efficiency.

A joint industry working group developed the [Invoice Contents Industry Practice Statement (IPS)[^1]](https://github.com/A-NZ-PEPPOL/A-NZ-Industry-Practice-Statements/blob/main/A-NZ_Industry_Practice_Statement_%20Invoice_Content_v1.1.docx) in 2020, which discussed buyers’ common data requirements and different systems capabilities. A few overarching principles from the IPS documents were reiterated by the Consistent Data Mapping focus group and it was agreed that the following principles should be adhered to by all participants:

### 1. When sending invoices:

- **a.** When the seller (corner 1, or C1) has the data, it should be provided in the invoice XML message.  
- **b.** The seller and the sending solution should ensure invoice business terms are used according to their semantic definitions, as per the [<u>A-NZ Peppol Invoice Specification</u>](https://github.com/A-NZ-PEPPOL/A-NZ-PEPPOL-BIS-3.0). 
  - **i.** The sending solution may not support some invoice data, such as complex item identification information. Peppol supports a number of multi-purpose, free-text fields and users should refer to the Mapping Questions and Guidance section in this document for recommendations.  

### 2. When receiving invoices:

- **a.** When the buyer (corner 4, or C4) has been provided with the required information on the invoice, they should endeavour to ‘search for’ this information in all reference and contact fields to process the invoice where possible.  
- **b.** The receiving solutions (both access points and buyer/receiver’s solution) should ensure the full Peppol message is accessible.  
  - **i.** The receiving solutions should be able to receive attachments that are transmitted with a Peppol eInvoice.  

It is acknowledged that

- Businesses have different processes and data requirements, e.g., some
  buyers require a purchase order number or product identifiers for
  certain types of goods/supplies in order to process an invoice.

- Large entities may issue tailored supplier onboarding materials to
  specify data requirements and provide mapping guidance. These
  materials should align with the guidance in this document.

---

## MAPPING QUESTIONS AND GUIDANCE

This section lists the mapping questions that were discussed by the group and the recommended fields / approach for mapping.

### 1. Using legislated GST rate

| **Issue Statement** | **Recommendation** |
|---------------------|--------------------|
| There are cases when an invoice contains a GST rate that is different from the legislated tax rate. This could occur if the seller provides a gross total amount (GST inclusive), and the system calculates the GST amount and GST rate. | The invoice must always include the legislated tax rate (e.g., 10% for GST) as the tax rate for an invoiced item. It should not be a percentage that is calculated from the item price or from any other invoice element.<br>*See UBL example 1.1* |



---

### UBL Example 1.1 (non-normative)

```xml
<cac:TaxTotal>
    <cbc:TaxAmount currencyID="AUD">805.56</cbc:TaxAmount>
    <cac:TaxSubtotal>
        <cbc:TaxableAmount currencyID="AUD">8055.56</cbc:TaxableAmount>
        <cbc:TaxAmount currencyID="AUD">805.56</cbc:TaxAmount>
        <cac:TaxCategory>
            <cbc:ID>S</cbc:ID>
            <cbc:Percent>10</cbc:Percent> <!-- use legislated tax rate -->
            <cac:TaxScheme>
                <cbc:ID>GST</cbc:ID>
            </cac:TaxScheme>
        </cac:TaxCategory>
    </cac:TaxSubtotal>
</cac:TaxTotal>
```

---

## Attachment File Name and Path

**\*Note:** A separate [focus
group](https://www.dspanz.org/committees/peppol/anz-peppol-all-stakeholders-working-group/attachments/)
will cover the overall topic of Attachments. The below recommendation
for identifying attachments may receive further consideration and
development from the Attachments group.

| **ID** | **Issue Statement** | **Recommendation** |
|--------|---------------------|--------------------|
| 1 | **Interpretation of fields:**<br>When sending attachments in an eInvoice, three pieces of information must be provided:<br>1. Attachment ID (i.e., the reference or identifier of the attachment)<br>2. The file name attribute, and<br>3. The mime code attribute (i.e., the type/format of attachment, based on a code list).<br><br>There were different interpretations of the meaning of “File name” which has caused inconsistent use of this field. For example, some seller solutions have included the file path in the file name field. | **Definitions of fields:**<br>● **Attachment ID:** This should be the document identifier (similar to a PO having a PO number) of the attachment if applicable.<br>● **File name attribute:** This should be the title / name of the attached document, e.g., *Supporting Document.pdf*. Note that the document type extension (e.g. *.pdf*) should be included to simplify storage and access by the receiver.<br>● **Mime code attribute:** This field is to specify the format of an attachment. The appropriate code from the Peppol code list must be used.<br><br>Not all implementations will include the file type extension (e.g. *.pdf*) in file name. Therefore, it is recommended that C4 should rely on the mime code attribute to determine the format of attachments. |
| 2 | **Identifying attachments\***<br>Questions were also raised around instances where multiple attachments are included in an eInvoice, and how the buyer (eInvoice receiver) should identify whether an attachment is a rendered version of the eInvoice or contains supporting information. | Refer to guidance below for\*:<br>**2.1 Attaching rendered eInvoice**<br>*See UBL example 2.1*<br>**2.2 Attaching supporting information (e.g., timesheet)**<br>*See UBL example 2.2* |

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 45%" />
<col style="width: 48%" />
</colgroup>
<thead>
<tr>
<th></th>
<th>Issue statement:</th>
<th>Recommendation</th>
</tr>
</thead>
<tbody>
<tr>
<td>1</td>
<td><p><u>Interpretation of fields:</u></p>
<p>When sending attachments in an eInvoice, three pieces of information
must be provided:</p>
<ol type="1">
<li><p>Attachment ID (i.e., the reference or identifier of the
attachment)</p></li>
<li><p>The file name attribute, and</p></li>
<li><p>The mime code attribute (i.e., the type/format of attachment,
based on a code list).</p></li>
</ol>
<p>There were different interpretations of the meaning of “File name”
which has caused inconsistent use of this field. For example, some
seller solutions have included the file path in the file name
field.</p></td>
<td><p><u>Definitions of fields:</u></p>
<ul>
<li><p>Attachment ID: This should be the document identifier (similar to
a PO having a PO number) of the attachment if applicable.</p></li>
<li><p>File name attribute: This should be the title / name of the
attached document, e.g., Supporting Document.pdf. Note that the document
type extension (e.g. .pdf) should be included to simplify storage and
access by the receiver.</p></li>
<li><p>Mime code attribute: This field is to specify the format of an
attachment. The appropriate code from the <a
href="https://docs.peppol.eu/poacc/billing/3.0/codelist/MimeCode/"><u>Peppol
code list</u></a> must be used.</p></li>
</ul>
<p>Not all implementations will include the file type extension (e.g.
<em>.pdf</em>) in file name. Therefore, it is recommended that C4 should
rely on the mime code attribute to determine the format of
attachments.</p></td>
</tr>
<tr>
<td>2</td>
<td><p><u>Identifying attachments*</u></p>
<p>Questions were also raised around instances where multiple
attachments are included in an eInvoice, and how the buyer (eInvoice
receiver) should identify whether an attachment is a rendered version of
the eInvoice or contains supporting information.</p></td>
<td><blockquote>
<p>Refer to guidance below for*:</p>
</blockquote>
<ol type="1">
<li><p>attaching rendered eInvoice<br />
<em>See UBL example 2.1</em></p></li>
<li><p>attaching supporting information (e.g., timesheet)<br />
<em>See UBL example 2.2</em></p></li>
</ol></td>
</tr>
</tbody>
</table>

<u>Attachment as a rendered eInvoice:</u>

Some sending solutions by default will include an attachment, which is a
rendered version (e.g., PDF) of the eInvoice, often with additional
information (e.g., to meet regulatory requirements, support, marketing
messages etc.). In this scenario, it is recommended that Peppol data
fields for attachments are populated as follows:



[^1]: Invoice Content IPS is to surface common data requirements by large buyers to assist solutions providers to prioritise and enhance their eInvocing service offers.  
