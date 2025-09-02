# A-NZ Industry Practice Statement
**Guidance and Recommendations for Consistent Data Mapping**  
**Version:** 1.0  
**Publication Date:** 9 September 2022  

---

## PURPOSE

This document aims to assist with consistent interpretation and implementation of the A-NZ invoice specification.  

A number of mapping questions and issues were raised and addressed by the Data Mapping focus group (the group), which was formed as part of the A-NZ Peppol All-Stakeholders Working Group and represents end-users and solution providers (access points and providers of accounting solutions/ERP/FMIS).  

This document has been developed by the group and includes a problem statement, a summary and recommended approach for each mapping issue, and UBL examples.

> **Note:**  
> - This is a living document that will be updated as further data mapping resolutions are determined.  
> - The UBL samples provided through this document are non-normative and the specification takes precedence. Please refer to the principles and guidance (Recommendations).  

---

## CONTEXT

Issues and questions were raised that invoice data is not always conveyed appropriately and caused processing issues (delays or rejections). Issues include:

- Invoice data is not mapped according to its semantic meaning.  
- The same invoice data is mapped differently by different sending entities.  
- Lack of guidance/consistency for how complex invoice information should be conveyed (e.g., utility bills).  

The full Problem Statement, examples and descriptions of data mapping issues can be found here.

---

## PRINCIPLES

Consistent mapping and usage of the specification is key to ensure automation and realisation of network efficiency.

A joint industry working group developed the Invoice Contents Industry Practice Statement (IPS) in 2020, which discussed buyers’ common data requirements and different systems capabilities. A few overarching principles from the IPS documents were reiterated by the Consistent Data Mapping focus group and it was agreed that the following principles should be adhered to by all participants:

### 1. When sending invoices:

- **a.** When the seller (corner 1, or C1) has the data, it should be provided in the invoice XML message.  
- **b.** The seller and the sending solution should ensure invoice business terms are used according to their semantic definitions, as per the A-NZ Peppol Invoice Specification.  
  - The sending solution may not support some invoice data, such as complex item identification information. Peppol supports a number of multi-purpose, free-text fields and users should refer to the Mapping Questions and Guidance section in this document for recommendations.  

### 2. When receiving invoices:

- **a.** When the buyer (corner 4, or C4) has been provided with the required information on the invoice, they should endeavour to ‘search for’ this information in all reference and contact fields to process the invoice where possible.  
- **b.** The receiving solutions (both access points and buyer/receiver’s solution) should ensure the full Peppol message is accessible.  
  - The receiving solutions should be able to receive attachments that are transmitted with a Peppol eInvoice.  

> It is acknowledged that:  
> - Businesses have different processes and data requirements, e.g., some buyers require a purchase order number or product identifiers for certain types of goods/supplies in order to process an invoice.  
> - Large entities may issue tailored supplier onboarding materials to specify data requirements and provide mapping guidance. These materials should align with the guidance in this document.  

---

## MAPPING QUESTIONS AND GUIDANCE

This section lists the mapping questions that were discussed by the group and the recommended fields / approach for mapping.

### 1. Using legislated GST rate

**Issue statement:**  
There are cases when an invoice contains a GST rate that is different from the legislated tax rate. This could occur if the seller provides a gross total amount (GST inclusive), and the system calculates the GST amount and GST rate.

**Recommendation:**  
The invoice must always include the legislated tax rate (e.g., 10% for GST) as the tax rate for an invoiced item. It should not be a percentage that is calculated from the item price or from any other invoice element.

See UBL example 1.1

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
