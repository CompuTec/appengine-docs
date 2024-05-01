---
sidebar_position: 1
---

# Overview

Batch Traceability 360 plug-in allows to trace Item Batches through all its life in a company: from production (or purchase), being a part of a production process of other Item, to delivery to a client. Instant access to batches records is very useful, e.g. in complaint management or recall process.

[Batch Traceability Scenario - A Guided Tour](https://youtu.be/ZHUswSIKTu0)

## Installation and Configuration

### Prerequisites

ProcessForce and CompuTec Licence Server is installed and configured. For more information, click [here](/docs/processforce/administrator-guide/licensing/license-server/overview/)

### AppEngine and Plug-in Installation and Configuration

For AppEngine installation please follow this link: [Installation](../../administrators-guide/installation.md)

For Plug-in installation please follow this link: [Configuration and Administration](../../administrators-guide/configuration-and-administration/overview.md).

### ProcessForce

As an option you can call Serialization plug-in from inside the Process Force:

![Batch Traceability 360](./media/overview/batch-traceability-360.png)

To do this, check the following checkbox:

![Batch Traceability 360](./media/overview/bt360-image2020-1-18-8-33-41-720.png)

Enter AppEngine url, e.g. `http://{host}:54000`, click Update and restart SAP Business One.

## Start points for function opening

You can reach ProcessForce Batch Traceability 360 by:

- AppEngin launchpad
- Modules Menu (check the path below)

:::info Path
        Inventory > Item Management > Batches > Batch Traceability 360
:::

- Transaction tab on Complaint form:
![Complaint Form](./media/overview/complaint-form.png)

Click [here](/docs/processforce/user-guide/complaint-management/complaint/) to find out more about Complaint function.

- Batch Master Data form context menu
![Batch Master Data](./media/overview/batch-master-data.png)

Click [here](/docs/processforce/user-guide/inventory/batch-control/batch-master-data/overview/) to find out more about Batch Master Data.

## Batch List

You can compose filter using Adapt Filters:
![Batch List Adapt Filters](./media/overview/adapt-filters.png)

Select a Batch line and you will be redirected to its Overview.

## Overview

On this screen you can find some tiles that bring you analytical information. The Selected Batch is a start point for analysis. Prepared information is related to the Batch and products (Batches) affected by the Batch. That means, information is prepared for all nodes on the right from selected node in the trace graph.

![Batch Traceability 360 Overview](./media/overview/new-overview.jpg)

**Note**: If you open Batch Traceability from SAP Business One, you will be able to use yellow arrow functionality as in SAP Business One.

To see extended view of header please select ![Down Arrow](./media/overview/down-arrow.png)

![Header](./media/overview/image2020-4-2-14-30-17.png)

Select button ![Trace Button](./media/overview/trace-button.png) and you will be redirected to Batch Trace graph.

## Batch Trace Graph

![Batch Trace Graph](./media/overview/batch-trace-graph.png)

On this graph specific Batches are represented by boxes (nodes) with its details. You can zoom in or zoom out the view by using a mouse roll or ![Zoom In](./media/overview/zoom%20in.png) and ![Zoom Out](./media/overview/zoom-out.png). You can show or hide legend by using ![Hide Legend](./media/overview/hide-legend.png). You can expand view by using ![Expand Legend](./media/overview/expand-legend.png).

### Going forward and backward

The Batch Trace visualization form shows what a specific Item was made of. It looks back on every Batch that was used in production process to the point of a chosen Batch.

![Batch Trace visualization form](./media/overview/going-backward-and-forward.png)
You can also choose a Batch and go forward to see where the Items from a specific Batch were used. To do that, hold Shift and left-click on a desired Batch:
![Going Backward and Forward](./media/overview/going-backward-and-forward-01.png)

In history list you can find your tracing history.You can switch to another batch from the list at any time in any form: Overview, Trace, Action.

### Transactions

Left-click on a specific box to select it and than select ![BT 360 Transactions](./media/overview/image2020-4-2-15-52-7.png) button to see all activities and transactions connected to the Batch:

![Batch Traceability 360 Transactions](./media/overview/image2020-4-2-15-51-4.png)
![Batch Traceability 360 Transactions](./media/overview/image2020-4-2-15-52-43.png)

Click the yellow arrow in a specific document row to get more information about it.

## Action

To navigate to Action view, please select ![Action Button](./media/overview/action-button.png) button. In Action view you can manage Batches' statuses. To change batch status chose the line in the list and than select checkbox in the first column and finally select button ![Change Status Button](./media/overview/change-status-button.png)

![Batch Traceability 360 Change Status](./media/overview/change-status.png)
