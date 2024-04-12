---
sidebar_position: 6
---

# MOWizard Plugin

## MOWizard 1.10.11 - 17 October 2023

| Issue Type | Release Note | Related Issue |
| --- | --- | --- |
| Bug | Cannot change the description of the jobs. | - |
| Bug | Incorrect label of the form for creating a New Scenario. | SPROC-14723 |
| Bug | It is not possible to generate a Manufacturing Order for a Bill of Materials containing a Phantom Bill of Materials. | - |
| Bug | Planning tab: Document Numbering Series is not available from the drop-down list. | - |
| Bug | The classification value is not copied to child MOs (the issue fixed in ProcessForce). | - |

---

## MOWizard 1.10.9 - 28 April 2023

| Type | Note |
| --- | --- |
| Improvement | A loading screen was added upon choosing a job from the list. |
| Improvement | Classification field added for document lines. |
| Improvement | Create Time and Update Time columns added to the job list. It is now possible to sort the records by Date and Time. |
| Improvement | If Manufacturing Orders are generated using MRP Order Recommendations as the source, it will update open quantity and their status. |
| Improvement | If the generated scenario does not have a document numbering series defined, the user default series is set. |
| Improvement | MOWizard has a group graph and a regular graph. Now, graphs are hidden in the dialog; you can access them by clicking the Show graph button. |
| Improvement | Wiard Job window: now it is possible to filter by the Partially Completed option. Partially completed means that not all Manufacturing Order has been created. |
| Improvement | <li>Planning tab: it is now possible to change Routing and Warehouse.</li><li>Document tab: it is now possible to change Revision.</li> |
| Improvement | Selected quantities can now be modified. |
| Improvement | Summary: Manufacturing Order child is by default. |
| Improvement | Classification can now be modified in MOWizard. |
| Improvement | When: When MRP Order Recommendations are used, a change of Selected Quantity results in an opening dialog that will help the user recalculate child recommendations. |
| Improvement | When rescheduling is needed to run a job, information about it and instructions on what the client should do is shown. |
| Improvement | When you select Order Recommendation, it automatically selects its children. |
| Bug | Planning tab: Document Numbering Series is not available from the drop-down list. |
| Bug | After deleting a scenario, the scenario is also removed from the list. |
| Bug | Before creating Manufacturing Orders documents, the user needs to reschedule Manufacturing Orders to be created. After this rescheduling, Manufacturing Order Documents are cached for a given user session and thus can be added as scheduled. |
| Bug | Sales Order tab: multiple selections by using Shift supported. |
