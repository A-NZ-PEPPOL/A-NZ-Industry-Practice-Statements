---
title: Guidance and recommendations for consistent data mapping
---


<p align="center">
  <img src="assets/ips_header.jpg" alt="Black IPS header" width="100%">
</p>

# A-NZ Industry Practice Statement
# Guidance and Recommendations for Consistent Data Mapping
Version: 1.0  
Publication Date: 9 September 2022  

📄 Copy available for download [here](./assets/PDF/A-NZ_IPS_Consistent_Data_Mapping.pdf)

---

## PURPOSE

This document aims to assist with consistent interpretation and
implementation of the [<u>A-NZ invoice
specification</u>](https://docs.peppol.eu/poac/aunz/).

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

A joint industry working group developed the [Invoice Contents Industry Practice Statement (IPS)](https://a-nz-peppol.github.io/A-NZ-Industry-Practice-Statements/) in 2020, which discussed buyers’ common data requirements and different systems capabilities. A few overarching principles from the IPS documents were reiterated by the Consistent Data Mapping focus group and it was agreed that the following principles should be adhered to by all participants:

1. **When sending invoices:**  
   **a.** When the seller (corner 1, or C1) has the data, it should be provided in the invoice XML message.  
   
   **b.** The seller and the sending solution should ensure invoice business terms are used according to their semantic definitions, as per the [A-NZ Peppol Invoice Specification](https://docs.peppol.eu/poac/aunz/).  
   
   &nbsp;&nbsp;&nbsp;&nbsp;**i.** The sending solution may not support some invoice data, such as complex item identification information.<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Peppol supports a number of multi-purpose, free-text fields and users should refer to the **Mapping Questions and Guidance**<br>
   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;section in this document for recommendations.

2. **When receiving invoices:**  
   **a.** When the buyer (corner 4, or C4) has been provided with the required information on the invoice, they should endeavour to ‘search for’ this information in all reference and contact fields to process the invoice where possible.  
   
   **b.** The receiving solutions (both access points and buyer/receiver's solution) should ensure the full Peppol message is accessible.  
   
   &nbsp;&nbsp;&nbsp;&nbsp;**i.** The receiving solutions should be able to receive attachments that are transmitted with a Peppol eInvoice.

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
| There are cases when an invoice contains a GST rate that is different from the legislated tax rate. This could occur if the seller provides a gross total amount (GST inclusive), and the system calculates the GST amount and GST rate. | The invoice **MUST** always include the legislated tax rate (e.g., 10% for GST) as the tax rate for an invoiced item. It should not be a percentage that is calculated from the item price or from any other invoice element.<br>*See UBL example 1.1* |


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

<table width="100%" style="width: 100%; border-collapse: collapse; table-layout: fixed;">
  <colgroup>
    <col width="8%" />
    <col width="46%" />
    <col width="46%" />
  </colgroup>
  <thead>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><u><strong>Issue statement:</strong></u></p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><u><strong>Recommendation</strong></u></p></td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>1</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">
        <p><ins>Interpretation of fields:</ins></p>
        <p>When sending attachments in an eInvoice, three pieces of information must be provided:</p>
        <ol>
          <li>Attachment ID (i.e., the reference or identifier of the attachment)</li>
          <li>The file name attribute, and</li>
          <li>The mime code attribute (i.e., the type/format of attachment, based on a code list).</li>
        </ol>
        <p>There were different interpretations of the meaning of “File name” which has caused inconsistent use of this field. For example, some seller solutions have included the file path in the file name field.</p>
      </td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">
        <p><ins>Definitions of fields:</ins></p>
        <ul>
          <li><strong>Attachment ID:</strong> This should be the document identifier (similar to a PO having a PO number) of the attachment if applicable.</li>
          <li><strong>File name attribute:</strong> This should be the title / name of the attached document, e.g., Supporting Document.pdf. Note that the document type extension (e.g. .pdf) should be included to simplify storage and access by the receiver.</li>
          <li><strong>Mime code attribute:</strong> This field is to specify the format of an attachment. The appropriate code from the <a href="https://docs.peppol.eu/edelivery/">Peppol code list</a> must be used.</li>
        </ul>
        <p>Not all implementations will include the file type extension (e.g. <em>.pdf</em>) in file name. Therefore, it is recommended that C4 should rely on the mime code attribute to determine the format of attachments.</p>
      </td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>2</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">
        <p><ins>Identifying attachments*:</ins></p>
        <p>Questions were also raised around instances where multiple attachments are included in an eInvoice, and how the buyer (eInvoice receiver) should identify whether an attachment is a rendered version of the eInvoice or contains supporting information.</p>
      </td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">
        <p>Refer to guidance below for*:</p>
        <p>2.1 attaching rendered eInvoice<br><em>See UBL example 2.1</em></p>
        <p>2.2 attaching supporting information (e.g., timesheet)<br><em>See UBL example 2.2</em></p>
      </td>
    </tr>
  </tbody>
</table>

<ins>Attachment as a rendered eInvoice:</ins>

Some sending solutions by default will include an attachment, which is a
rendered version (e.g., PDF) of the eInvoice, often with additional
information (e.g., to meet regulatory requirements, support, marketing
messages etc.). In this scenario, it is recommended that Peppol data
fields for attachments are populated as follows:

<table width="100%" style="width: 100%; border-collapse: collapse; table-layout: fixed;">
  <colgroup>
    <col width="50%" />
    <col width="50%" />
  </colgroup>
  <thead>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Peppol fields</strong></p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Proposed</strong></p></td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>Attachment ID (<em>cac:Attachment/cbc:ID</em>)</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>Invoice number, e.g., INV123</p></td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>File name (<em>cac:Attachment/cbc:EmbeddedDocumentBinaryObject/@filename</em>)</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">
        <p>Suggested a default value of</p>
        <p>“Rendered_Invoice_INV123.pdf”</p>
        <p>(Acknowledging that not all implementations will include the file type extension, e.g. .pdf in file name. Therefore, it is recommended that C4 should rely on the mime code attribute to determine the format of attachments.)</p>
      </td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>Mime code<br><em>(cac:Attachment/cbc:EmbeddedDocumentBinaryObject/@mimeCode)</em></p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>Must use one of the code from the <a href="https://docs.peppol.eu/edelivery/">Peppol code list</a>, e.g. application/pdf”.</p></td>
    </tr>
  </tbody>
</table>

*UBL example 2.1 (non-normative)*

```xml
<cac:AdditionalDocumentReference>
  <cbc:ID>Inv123</cbc:ID> <!-- include the invoice number -->
  <cac:Attachment>
    <cbc:EmbeddedDocumentBinaryObject
      filename="Rendered_Invoice_inv123.pdf"
      mimeCode="application/pdf">
      Q29uZ3JhdHVsYXRpb25zISAgWW91IHdpbiB0aGUgZWFzdGVyIGVnZyBwcml6ZSAobm8gYWN0dWFsIHByaXplKS4g
      IEdvIGdldCB5b3Vyc2VsZiBhIGNvZmZlZSB0byBjZWxlYnJhdGUu
    </cbc:EmbeddedDocumentBinaryObject>
  </cac:Attachment>
</cac:AdditionalDocumentReference>
```

<ins>Attachments as supporting documents:</ins>

<table width="100%" style="width: 100%; border-collapse: collapse; table-layout: fixed;">
  <colgroup>
    <col width="50%" />
    <col width="50%" />
  </colgroup>
  <thead>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Peppol fields</strong></p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Proposed</strong></p></td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>Attachment ID (<em>cac:Attachment/cbc:ID</em>)</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">
        <p>This should be the identifier of the supporting document, if applicable, e.g. timesheetwk18.</p>
        <p>If the attached document does not have an identifier, it is recommended to re-use the value of @filename (see below).</p>
      </td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>File name (<em>cac:Attachment/cbc:EmbeddedDocumentBinaryObject/@filename</em>)</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>This is the name of the attached file, e.g., Supporting_document.jpeg.</p></td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>Mime code<br><em>(cac:Attachment/cbc:EmbeddedDocumentBinaryObject/@mimeCode)</em></p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>Must use one of the code from the <a href="https://docs.peppol.eu/edelivery/">Peppol code list</a>, e.g. image/jpeg”.</p></td>
    </tr>
  </tbody>
</table>

*UBL example 2.2 (non-normative)*

```xml
<cac:AdditionalDocumentReference>
  <cbc:ID>Supporting_document.JPEG</cbc:ID> <!-- repeat file name if Attachment ID is not applicable -->
  <cac:Attachment>
    <cbc:EmbeddedDocumentBinaryObject
      filename="Supporting_document.JPEG"
      mimeCode="image/jpeg">
      Q29uZ3JhdHVsYXRpb25zISAgWW91IHdpbiB0aGUgZWFzdGVyIGVnZyBwcml6ZSAobm8gYWN0dWFsIHByaXplKS4g
      IEdvIGdldCB5b3Vyc2VsZiBhIGNvZmZlZSB0byBjZWxlYnJhdGUu
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
<table width="100%" style="width: 100%; border-collapse: collapse; table-layout: fixed;">
  <colgroup>
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
  </colgroup>
  <tbody>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Customer Account</strong><br>123456</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Customer PO</strong><br>PO123</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Invoice Date</strong><br>01.11.2021</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Payment Terms</strong><br>Next 30 Days</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Page</strong><br>1 of 1</p></td>
    </tr>
    <tr>
      <td colspan="2" valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>BD Sales Document:</strong> 5007879</p></td>
      <td colspan="2" valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Drop Ship Reference:</strong> Nil</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Contact:</strong><br>John.Smith</p></td>
    </tr>
    <tr>
      <td colspan="2" valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>BD Delivery:</strong><br>Delivery Address</p></td>
      <td colspan="2" valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Mode of Shipment:</strong> Truck FTL</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Shipped From:</strong><br>ABC Creek NSW 2178</p></td>
    </tr>
    <tr>
      <td colspan="2" valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Carrier Reference</strong><br>Nil</p></td>
      <td colspan="2" valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Carrier:</strong> ABC Pty.Ltd</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Freight Terms:</strong><br>DDP PER BD Terms &amp; Conditions</p></td>
    </tr>
  </tbody>
</table>

*UBL example 3.1 (non-normative)*

```xml
<cbc:ID>1234567890</cbc:ID> <!-- Invoice number -->
<cbc:IssueDate>2021-11-01</cbc:IssueDate>
<cbc:DueDate>2021-12-01</cbc:DueDate>
<cbc:InvoiceTypeCode>380</cbc:InvoiceTypeCode>
<!-- Delivery and tracking information are included in the free text field -->
<cbc:Note>
  Carrier: ABC Pty Ltd; Mode: Truck FTL; Freight Terms: DDP PER BD Terms and Conditions;
  Shipped from: ABC Creek NSW 2178; Contact: John Smith
</cbc:Note>
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

<table width="100%">
  <colgroup>
    <col width="28%" />
    <col width="72%" />
  </colgroup>
  <tbody>
    <tr>
      <td valign="top">
        <table width="100%">
          <tbody>
            <tr>
              <td><strong>Sales Amount:</strong></td>
              <td align="right"><strong>$197.50</strong></td>
            </tr>
            <tr>
              <td>&nbsp;&nbsp;&nbsp;&nbsp;Freight:</td>
              <td align="right">$25.00</td>
            </tr>
            <tr>
              <td>&nbsp;&nbsp;&nbsp;&nbsp;GST:</td>
              <td align="right">$22.25</td>
            </tr>
            <tr>
              <td><strong>Total Amount:</strong></td>
              <td align="right"><strong>$244.75</strong></td>
            </tr>
            <tr>
              <td>Paid Today:</td>
              <td align="right">$0.00</td>
            </tr>
            <tr>
              <td><strong>Balance Due</strong></td>
              <td align="right"><strong>$244.75</strong></td>
            </tr>
          </tbody>
        </table>
      </td>
      <td valign="top">
<pre><code>&lt;!-- Freight as invoice level charge --&gt;
&lt;cac:AllowanceCharge&gt;
  &lt;cbc:ChargeIndicator&gt;true&lt;/cbc:ChargeIndicator&gt;
  &lt;cbc:AllowanceChargeReasonCode&gt;FC&lt;/cbc:AllowanceChargeReasonCode&gt;
  &lt;cbc:Amount currencyID=&quot;AUD&quot;&gt;25.00&lt;/cbc:Amount&gt;
  &lt;cac:TaxCategory&gt;
    &lt;cbc:ID&gt;S&lt;/cbc:ID&gt;
    &lt;cbc:Percent&gt;10&lt;/cbc:Percent&gt;
    &lt;cac:TaxScheme&gt;
      &lt;cbc:ID&gt;GST&lt;/cbc:ID&gt;
    &lt;/cac:TaxScheme&gt;
  &lt;/cac:TaxCategory&gt;
&lt;/cac:AllowanceCharge&gt;</code></pre>
      </td>
    </tr>
  </tbody>
</table>

*UBL Example 4.2 - Freight as invoice line (non-normative)*

| Code   | Description    | QTY | Price | Amount |
|--------|----------------|-----|-------|--------|
| 210556 | 2x5 Litre      | 2   | 41.27 | 82.54  |
| 980003 | Freight Charge | 1   | 32.00 | 32.00  |


```xml
<!-- Freight as invoice line -->
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

*UBL Example 4.3 - Freight for an invoice line (non-normative)*

<table width="100%" style="width: 100%; border-collapse: collapse; table-layout: fixed;">
  <colgroup>
    <col width="18%" />
    <col width="32%" />
    <col width="15%" />
    <col width="17%" />
    <col width="18%" />
  </colgroup>
  <thead>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><strong>Code</strong></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><strong>Description</strong></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><strong>QTY</strong></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><strong>Price</strong></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><strong>Amount</strong></td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">20</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>V2 Reagents</p><p>Handling Charge ANZ</p><p>GST</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">10</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>796.72</p><p>10%</p></td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>7967.20</p><p>68.40</p><p>6.84</p></td>
    </tr>
  </tbody>
</table>


```xml
<!-- Freight for an invoice line -->
<cac:InvoiceLine>
  <cbc:ID>1</cbc:ID>
  <!-- codes omitted for clarity -->
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

<ins>Option 1</ins> - Additional Item Property

If a seller needs to provide the data in a structured way, the group
recommends using <code>cac:AdditionalItemProperty</code>.

*UBL Example 6.1 (non-normative)*

```xml
<cac:InvoiceLine>
  <cbc:ID>1</cbc:ID>
  <cbc:InvoicedQuantity unitCode="EA">635</cbc:InvoicedQuantity>
  <!-- codes omitted for clarity -->
  <cac:Item>
    <cbc:Name>Discount</cbc:Name>
    <!-- codes omitted for clarity -->
    <cac:AdditionalItemProperty>Discount</cac:AdditionalItemProperty>
      <cbc:Name>Open reading</cbc:Name>
      <cbc:Value>193167</cbc:Value>
    <cac:AdditionalItemProperty>Discount</cac:AdditionalItemProperty>
      <cbc:Name>Close reading</cbc:Name>
      <cbc:Value>193802</cbc:Value>
```

<ins>Option 2</ins> - Item Description

When a sending solution does not support <code>cac:AdditionalItemProperty</code>, it
is recommended to use <code>cbc:Description</code> (free text).

*UBL Example 6.2 (non-normative)*

```xml
<cac:InvoiceLine>
  <cbc:ID>1</cbc:ID>
  <cbc:InvoicedQuantity unitCode="EA">635</cbc:InvoicedQuantity>
  <cbc:LineExtensionAmount currencyID="AUD">3.75</cbc:LineExtensionAmount>
  <cac:Item>
    <cbc:Description>Open reading: 93167; Close reading:103802</cbc:Description>
    <!-- codes omitted for clarity -->
  </cac:Item>
  <cac:Price>
    <cbc:PriceAmount currencyID="AUD">0.00592</cbc:PriceAmount>
  </cac:Price>
```

## 7. Asset/Equipment Identifiers

**Issue statement:**

- **Scenario 1 -** Asset or equipment identifiers may be shown on an
  invoice as an “invoice object”, e.g., invoiced items are black/white
  toners (line 1) and colour toners (line2). All invoiced items are for
  the same printer with the Asset ID X685P801197.

- **Scenario 2 -** An invoice may include multiple lines where each line
  references different equipment with a different identifier.

Peppol supports a number of fields for item / asset identifiers but
guidance is required to ensure consistent usage for different scenarios.

**Recommendation:**

<ins>Scenario 1</ins>

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
  <!-- Code 130 indicates this is the identifier of the invoiced “object” -->
```

Alternatively, this information may be included in cbc:Note as free text
if the sending solution does not support the above Peppol fields.

<ins>Scenario 2</ins>

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
    <!-- Code 130 indicates this is the identifier of the “object” for the invoice line -->
  </cac:DocumentReference>
  <cac:Item>
    <!-- codes omitted for clarity -->
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

<ins>1. Default value</ins>

   A Peppol eInvoice must contain either a purchase order (PO) number or a buyer reference number. This is commonly required to enable buyers to trigger automated workflows, e.g. for PO matching or invoice approval.

   Some invoices require neither reference and therefore the sending solution needs to include a “dummy” value to pass validation, e.g., “PO”, “NA” or the invoice number.

   Some sending solutions have coded the dummy value in the purchase order field. This has caused processing issues for some buyers as the dummy value was treated as a PO number but could not be matched, causing rejection of invoices.

<ins>2. Buyer Reference information</ins>

   Buyer Reference information is the alternative but it is a key piece of information that enables buyers to trigger processing workflows. Buyers require different reference information depending on business processes and system capabilities, such as Buyer’s contact (e.g., email or staff name), Trading account number, or a Location ID.

**Recommendation**

<ins>1. Default value</ins>

   - Where neither a PO or Buyer Reference is relevant, the default value should be put in <code>cbc:BuyerReference</code>.
   - Default values should be: “BUYER_REFERENCE” or “NA”.
   - Invoice number is <strong>not</strong> a recommended default value as, being an alphanumeric value, it could look like a purchase order reference number and may cause exceptions by receiving systems attempting to match to a PO.

   The group noted that the above recommendation may not be implemented immediately by existing solutions.

   Buyers and receiving systems (C3/C4) should be aware that some sending systems currently include the invoice number in the PO field, and this may continue for some time. Ideally, buyers should provide some flexibility in processing. For example, if the value in the PO field does not match with an existing PO, the invoice is treated as a non-PO invoice.

<ins>2. Buyer Reference information</ins>

   It is recommended that sellers should provide the data when it is available to assist with easier processing.

   Sellers may not fully understand what their various buyers require as a ‘buyer reference’. To reduce processing time by the buyer, and where practical, a seller/seller’s solution should use designated Peppol fields to provide the above information (e.g. use <code>cac:AccountingCustomerParty/cac:Party/cac:Contact</code> to include buyer’s name or email).

   Buyers should not expect sellers to understand various data/processing needs, and should endeavour to ‘search for’ required information in other reference and contact fields to process the invoice where possible.

## 9. Organisational specific / Seller assigned client account number 

**Issue statement:** There are scenarios where an invoice is specific to
an account, location, or business branch/unit. An invoice needs to
provide enough information for buyers to allocate an invoice to the
right cost centre (internal routing).

1.  Although the field <code>cbc:BuyerReference</code> should be used for internal
    routing information, buyers may have different data needs that are
    challenging for suppliers to manage.

2.  It is unclear which Peppol field should be used for seller-assigned
    client / account number.


**Recommendation:**

1.  As per principle 1b in this document, invoice data should be mapped
    according to its semantic meaning. See UBL example 9.1 below.

2.  For seller-assigned client / account number:

     **a.** The Peppol semantic model supports using AccountingCustomerParty/Party `cac:PartyIdentification` for “a previously exchanged seller-assigned identifier of the buyer.”  
   
     **b.** If the supplier expects this will be used by the buyer for routing purpose, the supplier can use `cbc:BuyerReference`.  
   
     **c.** Alternatively a supplier may include this in `cbc:Note` as free text, noting this is not ideal for automation.

*UBL Example 9.1 (non-normative) – For organisational specific IDs, such
as a location ID for a construction site, or an office/service location,
use DeliveryLocation.*

*Note: this is the location where the goods/services are delivered to.*

```xml
<cac:DeliveryLocation>
  <cbc:ID>Location123</cbc:ID> <!-- scheme ID can be provided if applicable -->
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


<table width="100%" style="width: 100%; border-collapse: collapse; table-layout: fixed;">
  <colgroup>
    <col width="16%" />
    <col width="34%" />
    <col width="25%" />
    <col width="25%" />
  </colgroup>
  <thead>
    <tr>
      <td width="16%" valign="top" align="left" style="vertical-align: top; text-align: left;"><strong>Field Name</strong></td>
      <td width="34%" valign="top" align="left" style="vertical-align: top; text-align: left;"><strong>Definition</strong></td>
      <td width="25%" valign="top" align="left" style="vertical-align: top; text-align: left;"><strong>Rule</strong></td>
      <td width="25%" valign="top" align="left" style="vertical-align: top; text-align: left;"><strong>Notes and UBL examples</strong></td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">Endpoint ID</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">Seller or buyer’s electronic address</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">Mandatory<br>One occurrence only</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">
        <p>This is the digital delivery address for an entity.</p>
        <p>Although most businesses in A-NZ would use an ABN or NZBN as the endpoint ID, this does not need to match the entity’s legal identifier.</p>
        <p><code>&lt;cbc:EndpointID schemeID="0151"&gt;47555222000&lt;/cbc:EndpointID&gt;</code></p>
      </td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">Party Legal Entity</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">Information as an entity has been registered in an official registrar as a legal entity or person. In A-NZ, this group will include the ABN/NZBN and an entity’s legal name.</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">Mandatory<br>One occurrence only</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">
        <p>A Peppol eInvoice always includes an ABN or NZBN, if the seller or buyer is located in Australian or New Zealand.</p>
        <p><code>&lt;cac:PartyLegalEntity&gt;</code><br>
        <code>&lt;cbc:RegistrationName&gt;EntityName&lt;/cbc:RegistrationName&gt;</code><br>
        <code>&lt;cbc:CompanyID schemeID="0151"&gt;47555222000&lt;/cbc:CompanyID&gt;</code><br>
        <code>&lt;cbc:CompanyLegalForm&gt;Partnership&lt;/cbc:CompanyLegalForm&gt;</code><br>
        <code>&lt;/cac:PartyLegalEntity&gt;</code></p>
      </td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">Party Identification</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">Other identifiers (e.g. Australian company number, GLN) and business names of a seller or buyer.</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">Optional<br>Multiple occurrences</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">
        <p><code>&lt;cac:Party&gt;</code><br>
        <code>&lt;cbc:EndpointID schemeID="0151"&gt;47555222000&lt;/cbc:EndpointID&gt;</code><br>
        <code>&lt;cac:PartyIdentification&gt;</code><br>
        <code>&lt;cbc:ID&gt;47555222000&lt;/cbc:ID&gt;</code><br>
        <code>&lt;/cac:PartyIdentification&gt;</code><br>
        <code>&lt;cac:PartyName&gt;</code><br>
        <code>&lt;cbc:Name&gt;Trading Name Ltd&lt;/cbc:Name&gt;</code><br>
        <code>&lt;/cac:PartyName&gt;</code></p>
      </td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">Party Tax Scheme</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">The seller or buyer’s tax identifier</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">Conditional*<br>In AU, a seller must include GST branch number when a GST branch (i.e. specifically registered for GST) is making a taxable sale. In NZ when a GST registered organisation makes a taxable sale, the New Zealand GST number must be entered as the value.</td>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;">
        <p><code>&lt;cac:PartyTaxScheme&gt;</code><br>
        <code>&lt;cbc:CompanyID&gt;47555222000&lt;/cbc:CompanyID&gt;</code><br>
        <code>&lt;cac:TaxScheme&gt;</code><br>
        <code>&lt;cbc:ID&gt;GST&lt;/cbc:ID&gt;</code><br>
        <code>&lt;/cac:TaxScheme&gt;</code><br>
        <code>&lt;/cac:PartyTaxScheme&gt;</code></p>
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

2.  Peppol code list
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

<table width="100%" style="width: 100%; border-collapse: collapse; table-layout: fixed;">
  <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
  </colgroup>
  <tbody>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"></td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;"><strong>1</strong></td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;"><strong>2</strong></td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;"><strong>3</strong></td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Unit price</strong><br><em>cbc:PriceAmount</em></p></td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">$24</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">$24</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">$1</td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Base Quantity</strong><br><em>cbc:BaseQuantity</em></p></td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">1 or not included</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">24</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;"><em>not included</em></td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>unit of measure<br><em>@unitCode</em></p></td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">Carton (XCT) or not included</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">Can (XCX)</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;"><em>not included</em></td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Line quantity</strong><br><em>cbc:InvoicedQuantity</em></p></td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">1.625</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">39</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">39</td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p>unit of measure<br><em>@unitCode</em></p></td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">Carton (XCT)</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">Can (XCX)</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">Can (XCX)</td>
    </tr>
    <tr>
      <td valign="top" align="left" style="vertical-align: top; text-align: left;"><p><strong>Line net amount</strong><br><em>cbc:LineExtensionAmount</em></p></td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">$39</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">$39</td>
      <td valign="top" align="center" style="vertical-align: top; text-align: center;">$39</td>
    </tr>
    <tr>
      <td colspan="4" valign="top" align="left" style="vertical-align: top; text-align: left;">
        <p>Line net amount = Unit price / Base Quantity x Line Quantity.</p>
        <p><strong>Note:</strong> base quantity is optional. If it is provided, its UOM must match the UOM for line quantity.</p>
      </td>
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
