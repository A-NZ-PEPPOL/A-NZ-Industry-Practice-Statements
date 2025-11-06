---
title: Guidance and Recommendations for Consistent Data Mapping
---

<p align="center">
  <img src="assets/header.jpg" alt="Header Image" width="100%">
</p>

# A-NZ Industry Practice Statement
# Guidance and Recommendations for Consistent Data Mapping
Version: 1.0  
Publication Date: 9 September 2022  

📄 Copy available for download [here](Update the link)

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

 1- When sending invoices:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**a.** When the seller (corner 1, or C1) has the data, it should be provided in the invoice XML message.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**b.** The seller and the sending solution should ensure invoice business terms are used according to their semantic definitions, as per the [<u>A-NZ Peppol Invoice Specification</u>](https://github.com/A-NZ-PEPPOL/A-NZ-PEPPOL-BIS-3.0). 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**i.** The sending solution may not support some invoice data, such as complex item identification information. Peppol supports a number of multi-purpose, free-text fields and users should refer to the **Mapping Questions and Guidance** section in this document for recommendations.  

 2- When receiving invoices:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**a.** When the buyer (corner 4, or C4) has been provided with the required information on the invoice, they should endeavour to ‘search for’ this information in all reference and contact fields to process the invoice where possible.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**b.** The receiving solutions (both access points and buyer/receiver’s solution) should ensure the full Peppol message is accessible.  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**i.** The receiving solutions should be able to receive attachments that are transmitted with a Peppol eInvoice.  

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
|:---------------------|:--------------------|
| There are cases when an invoice contains a GST rate that is different from the legislated tax rate. This could occur if the seller provides a gross total amount (GST inclusive), and the system calculates the GST amount and GST rate. | The invoice must always include the legislated tax rate (e.g., 10% for GST) as the tax rate for an invoiced item. It should not be a percentage that is calculated from the item price or from any other invoice element.<br>*See UBL example 1.1* |


*UBL Example 1.1 (non-normative)*

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

## 2. Attachment File Name and Path

**\*Note:** A separate [focus
group](https://www.dspanz.org/committees/peppol/anz-peppol-all-stakeholders-working-group/attachments/)
will cover the overall topic of Attachments. The below recommendation
for identifying attachments may receive further consideration and
development from the Attachments group.

<table width="642">
<tbody>
<tr>
<td width="37">
<p>&nbsp;</p>
</td>
<td width="293">
<p><strong>Issue statement:</strong></p>
</td>
<td width="312">
<p><strong>Recommendation</strong></p>
</td>
</tr>
<tr>
<td width="37">
<p>1</p>
</td>
<td width="293">
<p><u>Interpretation of fields:</u></p>
<p>When sending attachments in an eInvoice, three pieces of information must be provided:</p>
<p>1.&nbsp;&nbsp;&nbsp; Attachment ID (i.e., the reference or identifier of the attachment)</p>
<p>2.&nbsp;&nbsp;&nbsp; The file name attribute, and</p>
<p>3.&nbsp;&nbsp;&nbsp; The mime code attribute (i.e., the type/format of attachment, based on a code list).</p>
<p>There were different interpretations of the meaning of &ldquo;File name&rdquo; which has caused inconsistent use of this field.&nbsp; For example, some seller solutions have included the file path in the file name field.&nbsp;</p>
</td>
<td width="312">
<p><u>Definitions of fields:</u></p>
<p>●&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Attachment ID: This should be the document identifier (similar to a PO having a PO number) of the attachment if applicable.&nbsp;&nbsp;</p>
<p>●&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; File name attribute: This should be the title / name of the attached document, e.g., Supporting Document.pdf.&nbsp; Note that the document type extension (e.g. .pdf) should be included to simplify storage and access by the receiver.</p>
<p>●&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Mime code attribute: This field is to specify the format of an attachment.&nbsp; The appropriate code from the <a href="https://docs.peppol.eu/poacc/billing/3.0/codelist/MimeCode/">Peppol code list</a> must be used.</p>
<p><strong>&nbsp;</strong></p>
<p>Not all implementations will include the file type extension (e.g. <em>.pdf</em>) in file name. Therefore, it is recommended that C4 should rely on the mime code attribute to determine the format of attachments.&nbsp; <strong>&nbsp;</strong></p>
</td>
</tr>
<tr>
<td width="37">
<p>2</p>
</td>
<td width="293">
<p><u>Identifying attachments*</u></p>
<p>Questions were also raised around instances where multiple attachments are included in an eInvoice, and how the buyer (eInvoice receiver) should identify whether an attachment is a rendered version of the eInvoice or contains supporting information.</p>
</td>
<td width="312">
<p>Refer to guidance below for*:</p>
<p>2.1&nbsp; attaching rendered eInvoice <br /> <em>See UBL example 2.1 </em></p>
<p><em>2.2&nbsp; </em>attaching supporting information (e.g., timesheet)<br /> <em>See UBL example 2.2</em></p>
</td>
</tr>
</tbody>
</table>

---

<u>Attachment as a rendered eInvoice:</u>

Some sending solutions by default will include an attachment, which is a
rendered version (e.g., PDF) of the eInvoice, often with additional
information (e.g., to meet regulatory requirements, support, marketing
messages etc.). In this scenario, it is recommended that Peppol data
fields for attachments are populated as follows:

<table>
<tbody>
<tr>
<td width="425">
<p><strong>Peppol fields</strong></p>
</td>
<td width="207">
<p><strong>Proposed</strong></p>
</td>
</tr>
<tr>
<td width="425">
<p>Attachment ID (<em>cac:Attachment/cbc:ID</em>)</p>
</td>
<td width="207">
<p>Invoice number, e.g., INV123</p>
</td>
</tr>
<tr>
<td width="425">
<p>File name (cac:Attachment/cbc:EmbeddedDocumentBinaryObject/@filename)</p>
</td>
<td width="207">
<p>Suggested a default value of</p>
<p>&ldquo;Rendered_Invoice_INV123.pdf&rdquo;</p>
<p>(Acknowledging that not all implementations will include the file type extension, e.g. .pdf in file name. Therefore, it is recommended that C4 should rely on the mime code attribute to determine the format of attachments)</p>
</td>
</tr>
<tr>
<td width="425">
<p>Mime code</p>
<p>(<em>cac:Attachment/cbc:EmbeddedDocumentBinaryObject/@mimeCode)</em></p>
</td>
<td width="207">
<p>Must use one of the code from the <a href="https://docs.peppol.eu/poacc/billing/3.0/codelist/MimeCode/">Peppol code list</a>, e.g. application/pdf&rdquo;.</p>
</td>
</tr>
</tbody>
</table>

*UBL example 2.1 (non-normative)*

```xml
<cac:AdditionalDocumentReference>
  <cbc:ID>Inv123</cbc:ID> <!--include the invoice number-->
  <cac:Attachment>
    <cbc:EmbeddedDocumentBinaryObject 
      filename="Rendered_Invoice_inv123.pdf" 
      mimeCode="application/pdf">Q29uZ3JhdHVsYXRpb25zISAgWW91IHdpbiB0aGUgZWFzdGVyIGVnZyBwcml6ZSAobm8gYWN0dWFsIHByaXplKS4gIEdvIGdldCB5b3Vyc2VsZiBhIGNvZmZlZSB0byBjZWxlYnJhdGUu
    </cbc:EmbeddedDocumentBinaryObject>
  </cac:Attachment>
</cac:AdditionalDocumentReference>
```

---

<u>Attachments as supporting documents</u>

<table>
<tbody>
<tr>
<td width="425">
<p><strong>Peppol fields</strong></p>
</td>
<td width="207">
<p><strong>Proposed</strong></p>
</td>
</tr>
<tr>
<td width="425">
<p>Attachment ID (<em>cac:Attachment/cbc:ID</em>)</p>
</td>
<td width="207">
<p>This should be the identifier of the supporting document, if applicable, e.g. timesheetwk18.</p>
<p>&nbsp;</p>
<p>If the attached document does not have an identifier, it is recommended to re-use the value of @filename (see below).</p>
</td>
</tr>
<tr>
<td width="425">
<p>File name (cac:Attachment/cbc:EmbeddedDocumentBinaryObject/@filename)</p>
</td>
<td width="207">
<p>This is the name of the attached file, e.g., Supporting_document.jpeg.</p>
</td>
</tr>
<tr>
<td width="425">
<p>Mime code</p>
<p>(<em>cac:Attachment/cbc:EmbeddedDocumentBinaryObject/@mimeCode)</em></p>
</td>
<td width="207">
<p>Must use one of the code from the <a href="https://docs.peppol.eu/poacc/billing/3.0/codelist/MimeCode/">Peppol code list</a>, e.g. image/jpeg&rdquo;.</p>
</td>
</tr>
</tbody>
</table>

*UBL example 2.2 (non-normative)*

```xml

<cac:AdditionalDocumentReference>
  <cbc:ID>Supporting_document.JPEG</cbc:ID> <!--repeat file name if Attachment ID is not applicable-->
  <cac:Attachment>
    <cbc:EmbeddedDocumentBinaryObject 
      filename="Supporting_document.JPEG" 
      mimeCode="image/jpeg">Q29uZ3JhdHVsYXRpb25zISAgWW91IHdpbiB0aGUgZWFzdGVyIGVnZyBwcml6ZSAobm8gYWN0dWFsIHByaXplKS4gIEdvIGdldCB5b3Vyc2VsZiBhIGNvZmZlZSB0byBjZWxlYnJhdGUu
    </cbc:EmbeddedDocumentBinaryObject>
  </cac:Attachment>
</cac:AdditionalDocumentReference>

```

---

## 3. How to convey non-Financial Delivery Information

**Issue Statement:** An invoice may contain details for delivery
arrangements, such as freight terms, origin of delivery or tracking of
shipment.

The Peppol eInvoice data model supports information needed to make the
delivery (i.e., delivery date, address etc.). It does not have the
designated fields for the above additional information.

This is not financial / accounts payable information and unlikely to be
auto-processed by the receiving system. This complex information is
better supported by [<u>BIS Despatch Advice
3.1</u>](https://docs.peppol.eu/poacc/upgrade-3/profiles/30-despatchadvice/),
however, widespread use of this document is yet to be established in the
A-NZ region.

**Recommendation:** If the sender and/or receiver don’t have the
capability to exchange Despatch Advice messages, it is recommended to
use the free text field (cbc:Note) for the sender to include detailed
delivery information. It is noted the free text field is not ideal for
automation. For your reference, find a sample invoice and example UBL
below:

*Sample invoice*
<table width="529">
<tbody>
<tr>
<td width="96">
<p><strong>Customer Account</strong></p>
<p>123456</p>
</td>
<td colspan="2" width="113">
<p><strong>Customer PO</strong></p>
<p>PO123</p>
</td>
<td width="123">
<p><strong>Invoice Date</strong></p>
<p>01.11.2021</p>
</td>
<td colspan="2" width="131">
<p><strong>Payment Terms</strong></p>
<p>Next 30 Days</p>
</td>
<td width="66">
<p><strong>Page</strong></p>
<p>1 of 1</p>
</td>
</tr>
<tr>
<td colspan="2" width="162">
<p><strong>BD Sales Document:</strong> 5007879</p>
</td>
<td colspan="3" width="188">
<p><strong>Drop Ship Reference: </strong>Nil</p>
</td>
<td colspan="2" width="180">
<p><strong>Contact:</strong></p>
<p>John.Smith</p>
</td>
</tr>
<tr>
<td colspan="2" width="162">
<p><strong>BD Delivery:</strong></p>
<p>Delivery Address</p>
<p>&nbsp;</p>
</td>
<td colspan="3" width="188">
<p><strong>Mode of Shipment: </strong>Truck FTL</p>
</td>
<td colspan="2" width="180">
<p><strong>Shipped From: </strong></p>
<p>ABC Creek NSW 2178</p>
</td>
</tr>
<tr>
<td colspan="2" width="162">
<p><strong>Carrier Reference</strong></p>
<p>Nil</p>
</td>
<td colspan="3" width="188">
<p><strong>Carrier: </strong>ABC Pty.Ltd</p>
</td>
<td colspan="2" width="180">
<p><strong>Freight Terms:</strong></p>
<p>DDP PER BD Terms &amp; Conditions</p>
</td>
</tr>
</tbody>
</table>

*UBL example 3.1 (non-normative)*

```xml
<cbc:ID>1234567890</cbc:ID> <!--Invoice number-->
<cbc:IssueDate>2021-11-01</cbc:IssueDate>
<cbc:DueDate>2021-12-01</cbc:DueDate>
<cbc:InvoiceTypeCode>380</cbc:InvoiceTypeCode>
<!--Delivery and tracking information are included in the free text field-->
<cbc:Note>Carrier: ABC Pty Ltd; Mode: Truck FTL; Freight Terms: DDP PER BD Terms and Conditions; Shipped from: ABC Creek NSW 2178; Contact: John Smith</cbc:Note>
```

---


## 4. Freight and Delivery Charges

**Issue statement:** Peppol has designated fields to support both
invoice-level and line-level charges. Some sellers do not have the
capability, or the sending solutions are unable to specify which invoice
line(s) a charge/discount applies to.

**Recommendation**: If the sending solution is able to cater for the
designated Peppol fields,

freight charges should use the appropriate fields (see XML sample
below). This will allow for optimal automation by the buyer (C4).

Where the seller or the sending solution has limited data capability,
freight charge can be provided as a separate invoice line. The seller
should provide clear descriptions using the Item Name and Description
fields to ensure better processing by the buyer.

Note that Buyers (C4) should be aware of various sending capabilities
and be flexible to support all options.

*UBL Example 4.1 - Freight as invoice level charge (non-normative)*

<table>
  <colgroup>
    <col style="width: 30%" />
    <col style="width: 2%" />
    <col style="width: 66%" />
  </colgroup>
  <tbody>
    <tr>
      <td>
        <table>
          <colgroup>
            <col style="width: 62%" />
            <col style="width: 37%" />
          </colgroup>
          <thead>
            <tr>
              <th>
                <p><strong>Sales Amount:</strong></p>
                <blockquote>
                  <p>Freight:</p>
                  <p>GST:</p>
                </blockquote>
                <p><strong>Total Amount:</strong></p>
                <p><strong>Paid Today:</strong></p>
              </th>
              <th>
                <p>$197.50</p>
                <p>$25.00</p>
                <p>$22.25</p>
                <p>$244.75</p>
                <p>$0.00</p>
              </th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td><strong>Balance Due</strong></td>
              <td><strong>$244.75</strong></td>
            </tr>
          </tbody>
        </table>
      </td>
      <td></td>
      <td>
        <blockquote>
          <pre><code>&lt;!--Freight as invoice level charge--&gt;
&lt;cac:AllowanceCharge&gt;
  &lt;cbc:ChargeIndicator&gt;true&lt;/cbc:ChargeIndicator&gt;
  &lt;cbc:AllowanceChargeReasonCode&gt;FC&lt;/cbc:AllowanceChargeReasonCode&gt;
  &lt;cbc:Amount currencyID="AUD"&gt;25.00&lt;/cbc:Amount&gt;
  &lt;cac:TaxCategory&gt;
    &lt;cbc:ID&gt;S&lt;/cbc:ID&gt;
    &lt;cbc:Percent&gt;10&lt;/cbc:Percent&gt;
    &lt;cac:TaxScheme&gt;
      &lt;cbc:ID&gt;GST&lt;/cbc:ID&gt;
    &lt;/cac:TaxScheme&gt;
  &lt;/cac:TaxCategory&gt;
&lt;/cac:AllowanceCharge&gt;
</code></pre>
        </blockquote>
      </td>
    </tr>
  </tbody>
</table>
<p>&nbsp;</p>

*UBL Example 4.2 - Freight as invoice line (non-normative)*

| Code   | Description    | QTY | Price | Amount |
|--------|----------------|-----|-------|--------|
| 210556 | 2x5 Litre      | 2   | 41.27 | 82.54  |
| 980003 | Freight Charge | 1   | 32.00 | 32.00  |


```xml
<!--Freight as invoice line-->
<cac:InvoiceLine>
  <cbc:ID>2</cbc:ID>
  <cbc:InvoicedQuantity unitCode="EA">1</cbc:InvoicedQuantity>
  <cbc:LineExtensionAmount currencyID="AUD">32.00</cbc:LineExtensionAmount>
  <cac:Item>
    <cbc:Name>Freight charge</cbc:Name>
    <cac:ClassifiedTaxCategory>
      <cbc:ID>S</cbc:ID>
      <cbc:Percent>10</cbc:Percent>
      <cac:TaxScheme>
        <cbc:ID>GST</cbc:ID>
      </cac:TaxScheme>
    </cac:ClassifiedTaxCategory>
  </cac:Item>
  <cac:Price>
    <cbc:PriceAmount currencyID="AUD">32.00</cbc:PriceAmount>
  </cac:Price>
```
<p>&nbsp;</p>


*UBL Example 4.3 - Freight for an invoice line (non-normative)*

<table>
<colgroup>
<col style="width: 17%" />
<col style="width: 28%" />
<col style="width: 14%" />
<col style="width: 22%" />
<col style="width: 18%" />
</colgroup>
<thead>
<tr>
<th>Code</th>
<th>Description</th>
<th>QTY</th>
<th>Price</th>
<th>Amount</th>
</tr>
</thead>
<tbody>
<tr>
<td>20</td>
<td><p>V2 Reagents</p>
<p>Handling Charge ANZ</p>
<p>GST</p></td>
<td>10</td>
<td><p>796.72</p>
<p>10%</p></td>
<td><p>7967.20</p>
<p>68.40</p>
<p>6.84</p></td>
</tr>
</tbody>
</table>


```xml
<!--Freight for an invoice line-->
<cac:InvoiceLine>
  <cbc:ID>1</cbc:ID>
  <!--codes omitted for clarity-->
  <cac:AllowanceCharge>
    <cbc:ChargeIndicator>true</cbc:ChargeIndicator>
    <cbc:AllowanceChargeReasonCode>FC</cbc:AllowanceChargeReasonCode>
    <cbc:Amount currencyID="AUD">68.40</cbc:Amount>
  </cac:AllowanceCharge>
```

---

## 5. Discounts

Discounts are recommended to be applied in the same way as freight and
delivery charges (see above).

---

## 6. Calculated Invoice Quantity

**Issue statement:** Peppol eInvoice has a designated field for invoiced
item quantity (cbc:InvoicedQuantity). Quantities may also be determined
by calculations based on multiple parameters, for example: gas/water
consumption based on open and close meter readings, or when a charge is
based on number of hired items multiplied by the number of days.

Buyers (C4) have different data requirements and currently it is
unlikely for Buyers to require the calculation details in structured
XML. It is also unlikely that sending solutions can support that level
of detail.

**Recommendation:**

<u>Option 1</u> - Additional Item Property

If a seller needs to provide the data in a structured way, the group
recommends using cac:AdditionalItemProperty.

*UBL Example 6.1 (non-normative)*


```xml
<cac:InvoiceLine>
  <cbc:ID>1</cbc:ID>
  <cbc:InvoicedQuantity unitCode="EA">635</cbc:InvoicedQuantity>
  <!--codes omitted for clarity-->
  <cac:Item>
    <cbc:Name>Discount</cbc:Name>
    <!--codes omitted for clarity-->
    <cac:AdditionalItemProperty>Discount</cac:AdditionalItemProperty>
      <cbc:Name>Open reading</cbc:Name>
      <cbc:Value>193167</cbc:Value>
    </cac:AdditionalItemProperty>Discount</cac:AdditionalItemProperty>
      <cbc:Name>Close reading</cbc:Name>
      <cbc:Value>193802</cbc:Value>
```

<u>Option 2</u> - Item Description

When a sending solution does not support cac:AdditionalItemProperty, it
is recommended to use cbc:Description (free text).

*UBL Example 6.2 (non-normative)*

```xml
<cac:InvoiceLine>
  <cbc:ID>1</cbc:ID>
  <cbc:InvoicedQuantity unitCode="EA">635</cbc:InvoicedQuantity>
  <cbc:LineExtensionAmount currencyID="AUD">3.75</cbc:LineExtensionAmount>
  <cac:Item>
    <cbc:Description>Open reading: 93167; Close reading: 103802</cbc:Description>
    <!--codes omitted for clarity-->
  </cac:Item>
  <cac:Price>
    <cbc:PriceAmount currencyID="AUD">0.00592</cbc:PriceAmount>
  </cac:Price>
```

---


## 7. Asset/Equipment Identifiers

**Issue statement:**

- **Scenario 1** - Asset or equipment identifiers may be shown on an
  invoice as an “invoice object”, e.g., invoiced items are black/white
  toners (line 1) and colour toners (line2). All invoiced items are for
  the same printer with the Asset ID X685P801197.

- **Scenario 2** - An invoice may include multiple lines where each line
  references different equipment with a different identifier.

Peppol supports a number of fields for item / asset identifiers but
guidance is required to ensure consistent usage for different scenarios.

---

**Recommendation:**

<u>Scenario 1</u>

Peppol eInvoice supports “Invoiced object identifier” at invoice level
using cbc:ID and cbc:DocumentTypeCode, both under
cac:AdditionalDocumentReference.

When Document Type Code is “130”, it indicates the ID is the identifier
of the “invoiced object”. See examples below

*UBL Example 7.1 (non-normative)*

```xml
<cac:AdditionalDocumentReference>
  <cbc:ID>X685P801197</cbc:ID>
  <cbc:DocumentTypeCode>130</cbc:DocumentTypeCode>
  <!--Code 130 indicates this is the identifier of the invoiced “object”-->
```

Alternatively, this information may be included in cbc:Note as free text
if the sending solution does not support the above Peppol fields.

<u>Scenario 2</u>

“Invoiced object identifier” is also supported at invoice line level, as
the line object identifier.

In addition, Peppol also supports three types of item identification:

1.  Seller-assigned

2.  Buyer-assigned or

3.  Standard identifiers.

The seller should choose the most appropriate fields depending on the
origin of the ID.

**Note:** cac:StandardItemIdentification is best used for commercial
standards and it requires a scheme ID to specify identifier type, e.g. a
scheme ID of 0160 means GTIN.

*UBL Example 7.2 (non-normative) – Invoiced Object at line level*

```xml
<cac:InvoiceLine>
  <cbc:ID>1</cbc:ID>
  <cbc:InvoicedQuantity unitCode="EA">12</cbc:InvoicedQuantity>
  <cbc:LineExtensionAmount currencyID="AUD">360.00</cbc:LineExtensionAmount>
  <cac:DocumentReference>
    <cbc:ID>X685P801197</cbc:ID>
    <cbc:DocumentTypeCode>130</cbc:DocumentTypeCode>
    <!--Code 130 indicates this is the identifier of the “object” for the invoice line-->
  </cac:DocumentReference>
  <cac:Item>
    <!--codes omitted for clarity-->
```

*UBL Example 7.3 (non-normative) – Using appropriate item
identification*

```xml
<cac:BuyersItemIdentification>
  <cbc:ID>X685P801197</cbc:ID>
</cac:BuyersItemIdentification>

<!-- Or -->

<cac:StandardItemIdentification>
  <cbc:ID schemeID="0160">123456789012</cbc:ID>
</cac:StandardItemIdentification>
```

Alternatively, line level equipment IDs may be included as free text, if
the sending solution does not support the above Peppol fields, by using
line item description or name fields (cbc:Description or cbc:Name)

*UBL Example 7.4 (non-normative) – Using Item Description or Name*

```xml
<cac:Item>
  <cbc:Description>Serial number is X685P801197</cbc:Description>
  <cbc:Name>X685P801197</cbc:Name>
```


An invoice line level free text field cbc:Note is also available,
however this is highly likely to require manual effort from Buyers to
access the information.

*UBL Example 7.5 (non-normative) – Using line level free text field*


```xml
<cac:InvoiceLine>
  <cbc:ID>1</cbc:ID>
  <cbc:Note>Serial number is X685P801197</cbc:Note>
```

---

## 8. Purchase Order Number and Buyer Reference

**Issue Statement:**

<ol>
  <li><u>Default value</u>
    <p>A Peppol eInvoice must contain either a purchase order (PO) number or a buyer reference number. This is commonly required to enable buyers to trigger automated workflows, e.g. for PO matching or invoice approval.</p>
    <p>Some invoices require neither reference and therefore the sending solution needs to include a “dummy” value to pass validation, e.g., “PO”, “NA” or the invoice number.</p>
    <p>Some sending solutions have coded the dummy value in the purchase order field. This has caused processing issues for some buyers as the dummy value was treated as a PO number but could not be matched, causing rejection of invoices.</p>
  </li>

  <li><u>Buyer Reference information</u>
    <p>Buyer Reference information is the alternative but it is a key piece of information that enables buyers to trigger processing workflows. Buyers require different reference information depending on business processes and system capabilities, such as Buyer’s contact (e.g., email or staff name), Trading account number, or a Location ID.</p>
  </li>
</ol>

---

**Recommendation**

<ol>
  <li><u>Default value</u>
    <ul>
      <li>Where neither a PO or Buyer Reference is relevant, the default value should be put in <code>cbc:BuyerReference</code>.</li>
      <li>Default values should be: “BUYER_REFERENCE” or “NA”.</li>
      <li>Invoice number is <strong>not</strong> a recommended default value as, being an alphanumeric value, it could look like a purchase order reference number and may cause exceptions by receiving systems attempting to match to a PO.</li>
    </ul>
    <p>The group noted that the above recommendation may not be implemented immediately by existing solutions.</p>
    <p>Buyers and receiving systems (C3/C4) should be aware that some sending systems currently include the invoice number in the PO field, and this may continue for some time. Ideally, buyers should provide some flexibility in processing. For example, if the value in the PO field does not match with an existing PO, the invoice is treated as a non-PO invoice.</p>
  </li>

  <li><u>Buyer Reference information</u>
    <p>It is recommended that sellers should provide the data when it is available to assist with easier processing.</p>
    <p>Sellers may not fully understand what their various buyers require as a ‘buyer reference’. To reduce processing time by the buyer, and where practical, a seller/seller’s solution should use designated Peppol fields to provide the above information (e.g. use <code>cac:AccountingCustomerParty/cac:Party/cac:Contact</code> to include buyer’s name or email).</p>
    <p>Buyers should not expect sellers to understand various data/processing needs, and should endeavour to ‘search for’ required information in other reference and contact fields to process the invoice where possible.</p>
  </li>
</ol>

## 9. Organisational specific / Seller assigned client account number 

**Issue statement:** There are scenarios where an invoice is specific to
an account, location, or business branch/unit. An invoice needs to
provide enough information for buyers to allocate an invoice to the
right cost centre (internal routing).

1.  Although the field cbc:BuyerReference should be used for internal
    routing information, buyers may have different data needs that are
    challenging for suppliers to manage.

2.  It is unclear which Peppol field should be used for seller-assigned
    client / account number.


**Recommendation:**

1.  As per principle 1b in this document, invoice data should be mapped
    according to its semantic meaning. See UBL example 9.1 below.

2.  For seller-assigned client / account number:

    1.  the Peppol semantic model supports using
        AccountingCustomerParty/Party cac:PartyIdentification for “a
        previously exchanged seller-assigned identifier of the buyer.”

    2.  If the supplier expects this will be used by the buyer for
        routing purpose, the supplier can use cbc:BuyerReference.

    3.  Alternatively a supplier may include this in cbc:Note as free
        text, noting this is not ideal for automation.

*UBL Example 9.1 (non-normative) – For organisational specific IDs, such
as a location ID for a construction site, or an office/service location,
use DeliveryLocation.*

*Note: this is the location where the goods/services are delivered to.*

```xml
<cac:DeliveryLocation>
  <cbc:ID>Location123</cbc:ID> <!--scheme ID can be provided if applicable-->
</cac:DeliveryLocation>
```

*UBL Example 9.2 (non-normative) - Using PartyIdentification for
customer/account number (123abc).*

```xml
<cac:AccountingCustomerParty>
  <cac:Party>
    <cbc:EndpointID schemeID="0151">123456789</cbc:EndpointID>
    <cac:PartyIdentification>
      <cbc:ID>123abc</cbc:ID>
    </cac:PartyIdentification>
    <cac:PartyName>
      <cbc:Name>ClientAccountNumber</cbc:Name>
```

*UBL Example 9.2 (non-normative) - Using BuyerReference for
customer/account number (123abc).*

```xml
<cbc:BuyerReference>123abc</cbc:BuyerReference>
```

---

## 10. Party Identification

**For clarification:** Peppol supports multiple fields for party
identification information such as its legal entity ID, branch ID, or
GST registration number.

The table below lists the Peppol fields with descriptions and examples
for their usage.


<table width="100%">
<tbody>
<tr>
<td width="13%">
<p><strong>Field Name</strong></p>
</td>
<td width="16%">
<p><strong>Definition</strong></p>
</td>
<td width="16%">
<p><strong>Rule</strong></p>
</td>
<td width="53%">
<p><strong>Notes and UBL examples</strong></p>
</td>
</tr>
<tr>
<td width="13%">
<p>Endpoint ID</p>
</td>
<td width="16%">
<p>Seller or buyer&rsquo;s electronic address</p>
</td>
<td width="16%">
<p>Mandatory</p>
<p>One occurrence only</p>
</td>
<td width="53%">
<p>This is the digital delivery address for an entity.</p>
<p>Although most businesses in A-NZ would use an ABN or NZBN as the endpoint ID, this does not need to match the entity&rsquo;s legal identifier.</p>
<p>&nbsp;&lt;cbc:EndpointID schemeID="0151"&gt;47555222000&lt;/cbc:EndpointID&gt;</p>
</td>
</tr>
<tr>
<td width="13%">
<p>Party Legal Entity</p>
</td>
<td width="16%">
<p>Information as an entity has been registered in an official registrar as a legal entity or person.</p>
<p>In A-NZ, this group will include the ABN/NZBN and an entity&rsquo;s legal name.</p>
</td>
<td width="16%">
<p>Mandatory</p>
<p>One occurrence only</p>
</td>
<td width="53%">
<p>A Peppol eInvoice always includes an ABN or NZBN, if the seller or buyer is located in Australian or New Zealand.&nbsp;</p>
<p>&lt;cac:PartyLegalEntity&gt;</p>
<p>&lt;cbc:RegistrationName&gt;EntityName&lt;/cbc:RegistrationName&gt;</p>
<p>&lt;cbc:CompanyID&nbsp; schemeID="0151"&gt;47555222000&lt;/cbc:CompanyID&gt;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &lt;cbc:CompanyLegalForm&gt;Partnership&lt;/cbc:CompanyLegalForm&gt;</p>
<p>&lt;/cac:PartyLegalEntity&gt;</p>
</td>
</tr>
<tr>
<td width="13%">
<p>Party Identification</p>
</td>
<td width="16%">
<p>Other identifiers (e.g. Australian company number, GLN) and business names of a seller or buyer.</p>
</td>
<td width="16%">
<p>Optional</p>
<p>Multiple occurrences</p>
</td>
<td width="53%">
<p>&lt;cac:Party&gt;</p>
<p>&lt;cbc:EndpointID schemeID="0151"&gt;47555222000&lt;/cbc:EndpointID&gt;</p>
<p>&lt;cac:PartyIdentification&gt;</p>
<p>&lt;cbc:ID&gt;47555222000&lt;/cbc:ID&gt;</p>
<p>&lt;/cac:PartyIdentification&gt;</p>
<p>&lt;cac:PartyName&gt;</p>
<p>&lt;cbc:Name&gt;Trading Name Ltd&lt;/cbc:Name&gt;</p>
<p>&lt;/cac:PartyName&gt;</p>
</td>
</tr>
<tr>
<td width="13%">
<p>Party Tax Scheme</p>
</td>
<td width="16%">
<p>The seller or buyer&rsquo;s tax identifier</p>
</td>
<td width="16%">
<p>Conditional*</p>
<p>In AU, a seller must include GST branch number when a GST branch (i.e. specifically registered for GST) is making a taxable sale. In NZ when a GST registered organisation makes a taxable sale, the New Zealand GST number must be entered as the value.</p>
</td>
<td width="53%">
<p>&lt;cac:PartyTaxScheme&gt;</p>
<p>&lt;cbc:CompanyID&gt;47555222000&lt;/cbc:CompanyID&gt;</p>
<p>&lt;cac:TaxScheme&gt;</p>
<p>&lt;cbc:ID&gt;GST&lt;/cbc:ID&gt;</p>
<p>&lt;/cac:TaxScheme&gt;</p>
<p>&lt;/cac:PartyTaxScheme&gt;</p>
</td>
</tr>
</tbody>
</table>

---

## 11. Unit of Measure

**Issue statement:**

1.  UOM mismatch between Order and Invoice: Manual exceptions or invoice
    rejections could be triggered when the UOM on the invoice does not
    match the corresponding purchase order.

2.  Peppol [code
    list](https://docs.peppol.eu/poacc/billing/3.0/codelist/UNECERec20/)
    for units of measure (UOM): Peppol uses the code list where specific
    / complex UOM can be used. However, some solutions may not be able
    to support (sending) the full code list.

3.  Inconsistent interpretation and system capability relating to the
    eInvoice field Base Quantity.


**Recommendation:**

1.  The group discussed the issue of UOM mismatch between an invoice and
    PO. E.g. A buyer orders a carton of goods, and issues a PO with UOM
    of “carton”. The supplier may deliver 10 packages of goods (equals a
    carton) and issues an invoice with UOM of “package”.

    It was agreed that different business processes are the main trigger
    of issue which is beyond data mapping. eInvoicing does not affect
    existing processes of how the trading parties manage different unit of
    measure. Businesses should continue to manage this scenario as they
    currently do.

2.  It is acknowledged that some sending solutions may not support the
    full list of / complex UOM, and use generic values such as “EA”
    (each) or “C62” (one). Receiving entities (buyers) should support
    some flexibility and do not reject invoices due to unexpected UOM
    values (given it contains a valid value from the code list).

3.  Peppol eInvoices may **optionally** include base quantity
    (*cbc:BaseQuantity*), which indicates the number of item units to
    which the price applies.  
      
    For example, a supplier sells drinks in cans or in cartons. A carton
    has 24 cans of drinks and the supplier may deliver drinks in cans
    and invoice based on either Carton or Can prices.

    If the price for a carton is \$24, each can has a price of \$1. When
    the supplier delivers 39 cans of drinks and sends an eInvoice, there
    are three ways for an eInvoice to display price and quantity:

<table>
<colgroup>
<col style="width: 29%" />
<col style="width: 23%" />
<col style="width: 23%" />
<col style="width: 23%" />
</colgroup>
<tbody>
<tr>
<td></td>
<td style="text-align: center;"><strong>1</strong></td>
<td style="text-align: center;"><strong>2</strong></td>
<td style="text-align: center;"><strong>3</strong></td>
</tr>
<tr>
<td><p><strong>Unit price</strong></p>
<p>(<em>cbc:PriceAmount</em>)</p></td>
<td style="text-align: center;">$24</td>
<td style="text-align: center;">$24</td>
<td style="text-align: center;">$1</td>
</tr>
<tr>
<td><p><strong>Base Quantity</strong></p>
<p>(<em>cbc:BaseQuantity</em>)</p></td>
<td style="text-align: center;">1 or not included</td>
<td style="text-align: center;">24</td>
<td style="text-align: center;"><em>not included</em></td>
</tr>
<tr>
<td style="text-align: right;"><p>unit of measure</p>
<p>(<em>@unitCode</em>)</p></td>
<td style="text-align: center;">Carton (XCT) or not included</td>
<td style="text-align: center;">Can (XCX)</td>
<td style="text-align: center;"><em>not included</em></td>
</tr>
<tr>
<td><p><strong>Line quantity</strong></p>
<p>(<em>cbc:InvoicedQuantity</em>)</p></td>
<td style="text-align: center;">1.625</td>
<td style="text-align: center;">39</td>
<td style="text-align: center;">39</td>
</tr>
<tr>
<td style="text-align: right;"><p>unit of measure</p>
<p>(<em>@unitCode</em>)</p></td>
<td style="text-align: center;">Carton (XCT)</td>
<td style="text-align: center;">Can (XCX)</td>
<td style="text-align: center;">Can (XCX)</td>
</tr>
<tr>
<td><p><strong>Line net amount</strong></p>
<p>(<em>cbc:LineExtensionAmount</em>)</p></td>
<td style="text-align: center;">$39</td>
<td style="text-align: center;">$39</td>
<td style="text-align: center;">$39</td>
</tr>
<tr>
<td colspan="4"><p>Line net amount = Unit price / Base Quantity x Line
Quantity.</p>
<p><strong>Note:</strong> base quantity is optional. If it is provided,
its UOM must match the UOM for line quantity.</p></td>
</tr>
</tbody>
</table>

It was noted that receiving systems (for C4) may not always be able to
ingest and display Base Quantity, in which case users would refer to the
full rendered invoice to understand how the price was calculated
Regardless of C4’s system capability, the line net amount will be
calculated incorporating base quantity and will therefore be accurate.

---

## 12. Usage Details 

**Issue statement:**

 Invoices for specific industries such as utilities and
 telecommunications may include information to support specific usage
 data, such as itemised services, peak/off-peak rates and client usage
 information including comparisons to previous bills. This information
 is not expected to be required or processed by accounts payable
 systems, but still needs to be made available to the client in some
 format.


**Recommendation:**

 This type of supporting data is not financial / accounts payable
 information and unlikely to be processed automatically by the
 receiving system. Summarised invoices that convey data to support
 routing and accounts payable actions is the preferred option for
 inclusion in XML. Rich supporting information such as usage details
 and service calculations should be conveyed via attachments or through
 existing systems, such as customer portals.

---

## Version Control

| Version | Date         | Note                                                                                                                                                                                                 |
|:---------|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Draft   | 21 July 2022 | Initial draft. Distributed to the Consistent Data Mapping Focus Group.                                                                                                                              |
| 1.0     | 09 Sept 2022 | Distributed to the A-NZ All Stakeholders Working Group, feedback incorporated. Key updates: <br> • Noted that the UBL samples through this document are non-normative; <br> • Under #2 Attachment: <br> &nbsp;&nbsp;&nbsp;&nbsp; o Improved the format <br> &nbsp;&nbsp;&nbsp;&nbsp; o Included links to the Attachment Working Group. <br> • Added an explanation for using Base Quantity in an eInvoice, under #12 Unit of Measure. |

[^1]: Invoice Content IPS is to surface common data requirements by
    large buyers to assist solutions providers to prioritise and enhance
    their eInvocing service offers.


[^1]: Invoice Content IPS is to surface common data requirements by large buyers to assist solutions providers to prioritise and enhance their eInvocing service offers.  
