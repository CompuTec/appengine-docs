---
sidebar_position: 5
---

# BOM to MOR Update

This function allows propagating changes made on a particular Bill of Materials to existing Manufacturing Orders based on criteria given in the configuration.

---

## Installation

The option is based on an AppEngine job installed automatically during the [BulkChange plugin installation](../bulk-changes-on-bills-of-materials/installation-and-configuration.md).

Send Events Job has to be active for a specific company. Click [here](/docs/appengine/administrators-guide/configuration-and-administration/overview) to find out more.

Background processing has to be configured for a specific company. Click [here](/docs/appengine/administrators-guide/configuration-and-administration/overview#activation) to find out more.

## Configuration

:::info Path
AppEngine → Administration Panel → Plugins → CompuTec BulkChange Plugin → Settings
:::

There are additional settings that allow to filter which related Manufacturing Order are to be updated. Set a true or false value to activate or deactivate any option. The default values are used when no System values are set by a user.

![Screenshot](./media/bulk-changes-of-bom/bom-to-mor-settings.png)

| Option | Description |
|--- | --- |
| <u>AllUpdatesInOneTransaction</u> |When it is set to true, all of the related updates have to be successful (otherwise no update is performed). <br/>If it is set to false, in case of failure on one of the Manufacturing Orders, the rest of them will be still updated.|
| <u>IncludeChanges</u>: <li>Items</li> <li>Coproducts</li> <li>Scraps</li> | These elements are taken under consideration during an update (each of the element can be switched off) |
| <u>ManufacturingOrdersStatuses</u>: <li>NotScheduled</li> <li>Scheduled</li> <li>Released</li> | Define Manufacturing Orders in which status are taken under consideration during an update (each of the element can be switched off). <br/>Other Manufacturing Order statuses are not available because of being not editable, e.g. the Closed status. |
| <u>Subproducts</u> | In this section, you can configure the plugin to work for cases when the Manufacturing Order for the subproduct already exists (meaning, there are Items that are BOMs and there can have related Manufacturing Orders). <br/><br/><u>**ManufacturingOrdersAlreadyExists**</u> <br/>If there are related Manufacturing Orders, then there are two options: <br/><u>Replace for Statuses</u> – a BOM Item line with related Manufacturing Orders in specific status is replaced in the Final Good Manufacturing Order <br/><u>AddForStatuses</u> – a new BOM Item line with related Manufacturing Orders in specific status is added in the Final Good Manufacturing Order <br/><br/><u>ReplacedManufacturingSubOrders</u> – related to the Replace for Statuses option; defines what happens upon the replace. <br/>FinishforStatuses – set status to Finish for the replaced Manufacturing Orders in specific statuses |
| <u>Alerts</u> | You can define whether user will get alerts upon successful or failed updates. |

## Usage

Make some changes to the Bill of Materials:

:::info Path
Production → Bill of Materials → Bill of Materials
:::

Set the MOR Update Status User-Defined Field to the U - Start Update option:

:::info Path
the upper menu → View → User-Defined Fields
:::

![Screenshot](./media/bulk-changes-of-bom/bom-to-mor-udf.png)

Click the Update button in the Bill of Materials form. Now the status of the related MOR Update is available in the MOR Update Status UDF:

**Processing** – While updating (the time of processing depends on the data structure and volume).

**Success** or **Failure** – The result of the update.
