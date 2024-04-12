---
sidebar_position: 3
---

# Example Usage: Clustering

The example on this page is for a clustering process using the SEC Unique Numbered Product (UNP) standard.

---

## SEC Standard

SEC is short for Single European Coding and it is a unique identifier standard for marking human tissues and cells distributed in the European Union. The SEC is a mandatory requirement for all tissue establishments in the EU effective 29 April 2017.

The SEC consists of a donation identification number (SEC-DI, 21 characters) and a product identification sequence (SEC-PI, 19 characters).

![Screenshot](./media/clustering/image2020-1-8-13-19-3.png)

    - ISO Country Identifier: identifies the country of the TE issuing the SEC. The code used is the ISO 3166-1 alpha-2 country identifier
    - TE Code: Tissue Establishment code of the manufacturer creating products out of the received human tissue. TEs are listed in the EU Tissue Establishment Compendium
    - Unique Donation Number: identifies an individual donor
    - Coding System Identifier: identifies a system which the Product Code is derived from. So far in the EU the following 3 coding systems are used:

        | ***Coding System*** | ***Identifier*** |
        | --- | --- |
        | ISBT 128 | A|
        | Eurocode | B | 
        | EUTC | E | 

    - Product Code: identifies the product created out of the donated tissue
    - Split number: used to uniquely identify each produced product, unique within each Donation Identification/Product Code combination
    - Expiry Date: Expiry date of the created/produced product in YYYYMMDD format.

## Clustering

On Goods Receipt PO, Supplier Batch AND Supplier Serial Numbers are recorded and Internal Batch numbers generated. The Receiver requires different scenario groups for Internal Batch number generation. The received items are clustered into Internal Batch numbers based on scenario group identifiers such as: same Item, same PO, same supplier DN/PL, same Supplier Batch, same Expiry Date.

It is required to define identifiers for clustering per organisation/Item group/Item. E.g. for Receiver 1 the scenario of clustering of a received product into one Internal Batch number has to be based on unique Item/PO/PackList/Supplier Batch combination, for Receiver 2 a scenario of clustering should be based on Item/PO/PackList/Expirydate. If these are all identical the same Internal Batch number can be assigned to the received product.

Because Supplier Serial numbers are only unique within the UDI Lot number, and multiple Lots can be received on one single PO-line, the serial number registration should not only have a link to the Internal Batch, but also a link to the Supplier Batch.

Below you can find an example of how Internal Batches from one company (Supplier) are received by the other company (Receiver) and what identifies the clustering into one single Internal Batch.

![Screenshot](./media/clustering/batch-clustering.jpg)

Clustering rule:

| ***GRPO type*** | ***DN/PL # supplier*** | ***PO*** | ***Item*** | ***Supplier Batch #*** | ***Expiry Date*** |
| --- | --- | --- | --- | --- | --- |
| Receiver SEC/Serial# GRPO | Y | Y | Y |  | Y |

### Item declaration for serialization

For Items (managed by Batch) to be serialized, set UDF: Serialization enabled=Yes in Item Master Data. Thanks to this, all revisions of this Item will be subject to Rules controlling the selection of SPT for a given Item/ Revision.

![Screenshot](./media/clustering/image2020-1-8-13-57-39.png)

### WEB application – log in

[Please check this section of the documentation](/docs/appengine/appengine-users-guide/launchpad/).

### Attributes Templates – definition

The first step is to define Attribute Templates that can be used to build various variants of the Serialization Parameter Template (SPT). Each UNP member has assigned a separate Attribute. It is also necessary to define Attributes that allow the clustering process to be carried out.

![Screenshot](./media/clustering/image2020-1-9-10-13-41.png)
![Screenshot](./media/clustering/attribute-templates-h.png)

Below you can check the list of attributes in accordance to the SEC standard and other attributes required for the clustering process. For clustering to work according to a defined rule, you have to define attributes according to the following list:

![Screenshot](./media/clustering/list-of-attributes.png)

SEC Standard – donation identification:

![Screenshot](./media/clustering/sec-standard-donation-identification.png)

SEC Standard – product identification:

![Screenshot](./media/clustering/2020-11-13-11-49-00.png)
![Screenshot](./media/clustering/Batch.png)

Clustering components:

![Screenshot](./media/clustering/2020-11-13-11-44-59.png)
![Screenshot](./media/clustering/exp-date.png)

SEC Serial Number component is obligatory and is a key to Track & Trace Table:

![Screenshot](./media/clustering/sec-serial-number-component.png)

Clustering is sensitive to Item changes by default. The rest of the parameters to which clustering is sensitive is determined at the Attribute level. These are the ones for which Clustering ID = Yes: SEC - Purchase Order, SEC - Delivery Note, SEC - Expiry Date.

![Screenshot](./media/clustering/attribute-templates-expiry-date.png)

---

For field description please check [here](/docs/appengine/plugins-user-guide/serialization/fields-description#attribute-templates)

### Serialization Parameters Templates – definition

Attributes associated to SPT are a parameter of the rules that determine the use of a given SPT for clustering a given Item.
SPT is created by combining previously defined attribute templates. The user can modify Attribute's parameters.
When defining SPT, it is required to assign a given attribute to predefined Field (from Track & Trace Table) of a type compatible with the type of the given Attribute. This action allows you to create a dedicated Track & Trace Table for each Item in accordance to the defined SPT.

![Screenshot](./media/clustering/image2020-1-9-12-20-23.png)
![Screenshot](./media/clustering/image2020-1-9-12-21-51.png)

Please create a new SPT and add the predefined Attributes Templates to it, assigning them to predefined Field from Track & Trace Table.

![Screenshot](./media/clustering/serialization-parameters-templates.png)

---

### Rules – definition

In order to be able to carry out the clustering process for a given Item/Revision, it is necessary to define at least one Rule that will cover this Item.

![Screenshot](./media/clustering/image2020-1-9-12-54-7.png)

If in the Rule you specify only the Item Group, the SPT selected in the Result SPT column will be used for all of the Items in this Group. <br/>If you specify Item Code, then the Result SPT will be applied to all Revisions of the Item. <br/>If for a given Item you provide its revision, then Result SPT will be used only for this Item's Revision. <br/>The above applies to Items that have UDF set: Serialization enabled = Yes in Item Master Data. <br/>In our example, we will define a rule that specifies that previously defined SPT is applied to all of the revisions of a given Item.

![Screenshot](./media/clustering/image2020-1-9-12-52-22.png)

### Start the clustering process

The clustering process is saved in a serialization document. This document is a subject to approval and verification. Serialization documents are visible in the WMS's Packing Hierarchy tile: [here](/docs/appengine/plugins-user-guide/serialization/fields-description#serialization-results).

For testing purposes, you can use the scanner simulator available here: WMSScannerSymulator.exe.

For sample test data you can use the attached file: [SEC Clustering Test Case 09.01.2020 - 01.xlsx.]

Attributes that have a GS1-ID defined must be preceded by it in the simulator, e.g. SEC - Purchase Order must be preceded (99).

![Screenshot](./media/clustering/image2020-1-9-14-58-21.png)

Enable Serialization in CompuTec WMS (check [here](/docs/appengine/plugins-user-guide/serialization/serialization-plugin-installation-and-configuration#computec-wms)). Log in to CompuTec WMS (check [here](/docs/wms/user-guide/starting/)).

Start Serialisation Document:
![Screenshot](./media/clustering/image2020-1-15-12-19-29.png)![Screenshot](./media/clustering/image2020-1-9-15-38-42.png)
![Screenshot](./media/clustering/screenshot-2.png)![Screenshot](./media/clustering/image2020-1-9-15-4-52.png)

Start scanning data for the first serial number:

    1. Purchase Order.
    2. Delivery Note.
    3. Serial Number.
    4. Supplier Batch.

After scanning the data of the first serial number you will be redirected to scan the next one.

(You can also choose the New Goods Receipt option to receipt goods serialized Items without a Purchase Order)

If you want to cancel scanning, select ![Screenshot](./media/clustering/tick.png), and then ![Screenshot](./media/clustering/cross.png) . You will be able to return to this document.

![Screenshot](./media/clustering/image2020-1-9-15-20-38.png)
![Screenshot](./media/clustering/image2020-1-9-15-24-52.png)

Return to editing the serialization document.

![Screenshot](./media/clustering/image2020-1-9-15-38-1.png)
![Screenshot](./media/clustering/image2020-1-15-12-27-40.png)

Continue scanning serial numbers.vTo finish the serialization document, select ![Screenshot](./media/clustering/image2020-1-9-15-23-9.png) , and then ![Screenshot](./media/clustering/image2020-1-9-15-25-44.png).

**Deleting SN in CompuTec WMS**

When receiving a serialised item the SN is generated directly at GRPO scanning. When an employee notices it was received on a wrong PO, or wrong Pack List, it is possible to delete it.

![Screenshot](./media/clustering/delete-serial-number.png)

    1. Clear Common Fields.
    2. Clear SU List.
    3. Delete Serial Numbers.

### Check serialisation document

The unfinished document is in Open status. The finished document is in the status of Ready To Accept. The document has to be accepted for further processing. Document in status Ready To Accept can be edited to make corrections. To do this, go to the WEB application and select:

![Screenshot](./media/clustering/image2020-1-915-59-50.png)
![Screenshot](./media/clustering/image2020-1-9-16-55-31.png)

Add or remove batch – RMBM option on batch line:

![Screenshot](./media/clustering/image2020-1-9-17-8-8.png)

Change of SN assignment to batch:

![Screenshot](./media/clustering/image2020-1-9-17-8-59.png)

Finally, accept the serialization document:

![Screenshot](./media/clustering/image2020-1-9-17-10-24.png)

Once accepted, the status of the document changes to Verification.

![Screenshot](./media/clustering/image2020-1-9-17-20-8.png)

### Verification Document

The accepted serialization document is subject to verification in WMS:

![Screenshot](./media/clustering/image2020-1-9-17-13-43.png)![Screenshot](./media/clustering/image2020-1-15-12-51-44.png)
![Screenshot](./media/clustering/image2020-1-9-17-14-54.png)

To confirm verification, select ![Screenshot](./media/clustering/image2020-1-9-15-25-44.png).

The document status changes to Closed which is visible in the WEB application in the document list.

![Screenshot](./media/clustering/image2020-1-9-17-30-36.png)

### Receipt Document

Go to Receipt Document and enter Vendor, Warehouse and Bin Location (if applicable) and optionally Remarks, and then select ![Screenshot](./media/clustering/image2020-1-9-15-25-44.png). The GRPO document is saved and is now visible in SAP B1.

![Screenshot](./media/clustering/image2020-1-9-17-21-28.png)![Screenshot](./media/clustering/image2020-1-15-12-51-44-1.png)
![Screenshot](./media/clustering/image2020-1-9-17-25-51.png)

Goods Receipt PO in SAP B1:

![Screenshot](./media/clustering/goods-receipt-po-in-sapb1.png)

Batch Number Transactions Report:

![Screenshot](./media/clustering/batch-no-transaction-report.png)

### Track & Trace Report

![Screenshot](./media/clustering/track-trace.png)

By selecting Track & Trace Report in the WEB application it is possible to trace the Serial Number history:

![Screenshot](./media/clustering/serial-no.png)
![Screenshot](./media/clustering/serial-no-1.png)

## Example transactions in WMS using SN

### Stock Transfer

Source Warehouse selection

![Screenshot](./media/clustering/stock-transfer.png)![Screenshot](./media/clustering/transfer-operations.png)![Screenshot](./media/clustering/warehouse-3.png)

Item selection

![Screenshot](./media/clustering/document-details-7.png)![Screenshot](./media/clustering/new-item-3.png)

Batch and quantity to transfer selection

![Screenshot](./media/clustering/document-details-6.png)![Screenshot](./media/clustering/options.png)![Screenshot](./media/clustering/batches-7.png)![Screenshot](./media/clustering/quantity-4.png)

Serial numbers to transfer selection

![Screenshot](./media/clustering//search-serialization-4.png)![Screenshot](./media/clustering/search-serialization-3.png)![Screenshot](./media/clustering/quantity-5.png)

Destination warehouse selection

![Screenshot](./media/clustering/document-details-5.png)![Screenshot](./media/clustering/destination-warehouse.png)

Items confirmation and transfer document confirmation

![Screenshot](./media/clustering/put-items.png)![Screenshot](./media/clustering/remarks-4.png)

### Goods Issue

Warehouse selection

![Screenshot](./media/clustering/warehouse-1.png)![Screenshot](./media/clustering/warehouse-2.png)

#### Item selection

![Screenshot](./media/clustering/document-details-4.png)![Screenshot](./media/clustering/new-item-4.png)

#### Batch and quantity selection

![Screenshot](./media/clustering/document-details-2.png)![Screenshot](./media/clustering/batches-1.png)
![Screenshot](./media/clustering/quantity-2.png)

#### Serial numbers selection

![Screenshot](./media/clustering/image2020-1-13-11-9-2.png)![Screenshot](./media/clustering/image2020-1-13-11-43-57.png)
![Screenshot](./media/clustering/image2020-1-13-11-22-38.png)

#### Issue document confirmation

![Screenshot](./media/clustering/document-details-1.png)![Screenshot](./media/clustering/remarks.png)

### Delivery

#### Warehouse selection

![Screenshot](./media/clustering/delivery.png)![Screenshot](./media/clustering/delivery-1.png)
![Screenshot](./media/clustering/warehouse.png)

#### Customer selection

![Screenshot](./media/clustering/customer-selection.png)

#### Item selection

![Screenshot](./media/clustering/document-details.png)![Screenshot](./media/clustering/new-item.png)

#### Batch and quantity selection

![Screenshot](./media/clustering/image2020-1-13-11-2-10.png)![Screenshot](./media/clustering/image2020-1-13-12-8-18.png)
![Screenshot](./media/clustering/batches.png)![Screenshot](./media/clustering/quantity-1.png)

#### Serial number selection

![Screenshot](./media/clustering/search-serialization.png)![Screenshot](./media/clustering/search-serialization-1.png)
![Screenshot](./media/clustering/quantity.png)![Screenshot](./media/clustering/storage-info.png)

#### Delivery document confirmation

![Screenshot](./media/clustering/document-details-3.png)![Screenshot](./media/clustering/image2020-1-13-12-27-46.png)
