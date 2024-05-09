---
sidebar_position: 1
---

# Release Notes

:::info
The latest Installer is available to download from [here](/docs/appengine/download/mrp/).
:::

## MRP 1.10.11 - 6 February 2024

| Issue Type | Release Note | Related issue/s |
| --- | --- | --- |
| Improvement | It is now possible to show/hide columns in Order Recommendations | - |
| Improvement | Information's about Project, Classification and Dimensions are now shown in Wizard Recommendations | - |
| Improvement | Dimensions added to filters in Order Recommendations | - |
| Improvement | Added possibility to change Gantt view using selection menu (previously change was only possible using range input).  Added short value notation ex: 2000 -> 2k, modification for decimal places from 0 to 6. | - |
| Improvement | It is now possible for user to export data from Order Recommendations | SPROC-15063 |
| Bug | Not able to add item if there is lead time | SPROC-15067 |
| Bug | Relationship map not working | SPROC-15067 <br/>SPROC-15529 |
| Bug | Fixed sorting and adding Item | SPROC-15067 |
| Bug | Show warning in relationship map if demand can't be fulfilled on time | SPROC-15067 |

---

## MRP 1.10.10 - 3 August 2023

| Issue Type | Release Note | Related issue/s |
| --- | --- | --- |
| Improvement | Result, Graph, and Consumed Forecast options added to the debug mode. | - |
| Improvement | Result: Settings button added to show the Graph option: <br/>Now the graph option has two variants: <br/>- Show Short Number Value: 19,000,123 -> 19k, <br/>- Decimal Places (change the number of decimal places to show): you can choose from 0 to 6 or disable the option. <br/>The data is stored in the cookies on a browser. | SPROC-13411 |
| Bug | An error occurs upon starting a Scenario in specific cases. <br/><br/>Error message: <br/><blockquote>Query:CALL "CT_PF_OMRB_FillData" (N'COS309', N'c2ba07fa-483b-458e-8714-eff7f00ff888');<br/>execution aborted by timeout</blockquote> | SPROC-14766 |
| Bug | An object reference error occurs upon attempts to save Recommendations in specific cases. | SPROC-14874 |
| Bug | Forecast: incorrect scaling of the window cause a lack of the scroll bar. Also, cannot close the window. | - |
| Bug | Projects: a lack of Recommendation representation in the relationship graph, even though the related Recommendation is on the list. | - |
| Bug | Recommendations: duplicated values in the Due Date column. | - |

---

## MRP 1.10.9

11 May 2023

| Issue Type | Custom field (Release Note) | Related issue/s |
| --- | --- | --- |
| Improvement | A button has been added that enables access to the Order Recommendation window directly from the MRP 2.5 Order recommendation form. | - |
| Bug | Changing the purchase unit on the recommendation changes the selected Quantities and Products per Unit to text with a dot. | - |
| Bug | Improvement: it is now possible to add documents when only Include Demand  is selected | - |
| Bug | New Scenario, Forecast & Recom tab: an error occurs upon attempts to add a forecast. | SPROC-14626 <br/>SPROC-14670 |
| Bug | No possibility to search by Project number when adding documents | - |
| Bug | Recommendations tab: now clicking Go to Order Recommendation displays elements from the last run. | - |
| Bug | Result tab: incorrect display of elements in specific screen resolutions (e.g., 1920x1080): no bottom scroll bar, Item Code displayed on top of Item Name. | SPROC-14371 |
| Bug | Order Recommendation: quantities are incorrectly recalculated when Base Quantity is changed a second time. | - |
| Bug | Order Recommendation: the Relation Map is now opened in a new window due to precious problems with the unstable display of it in the Order Recommendation. | - |
| Bug | Results: scrolling does not work (works after clicking Expand and then Collapse All). | - |
| Improvement | The calling of Relationship Map on Order Recommendation (while working in the browser) requires re-login. | - |

---

## MRP 1.10.7

28 September 2022

| Issue Type | Release Note | Related issue/s |
| --- | --- | --- |
| Improvement | Pegging Information form: Item Code from the related Manufacturing Order added. | - |
| Improvement | Planning horizon tab, Advance Settings section: Processing Method option added (Synchronous, Asynchronous). | - |
| Improvement | Scenario progress percentage and progress bar added. | - |
| Bug | Documents tab: cannot restrict a Manufacturing Order in the Scheduled status. | - |
| Bug | Filtering in the Debug mode improved. | - |
| Bug | Incorrect encoding of the ' character in the Italian translation. | - |
| Bug | MRP Wizard: Saving Recommendations more than one time makes them disappear (they are not visible in Order Recommendation). | - |
| Bug | Typos in the field descriptions corrected. | - |

---

## MRP 1.10.6, 1.93.6

28 March 2022

| Issue Type | Release Note | Related issue/s |
| --- | --- | --- |
| Improvement | MRP Scenario: a new combo box added: Processing Method | - |
| Improvement | MRP Wizard, Report tab: rounding of the values now works based on SAP Business One setting: General Settings, Display, Decimal Places | - |
| Improvement | Order Recommendation: change of the button name from 'Save and create documents' to 'Save'. If no Create checkbox is selected, saves all recommendations. If any button is selected, it creates documents for the selected (dialogue window) and saves all recommendations. | SPROC-12864 |
| Improvement | rder Recommendation: now, the Base Quantity field is non-editable, the Planned Quantity field added (editable, replaces Base Quantity in calculations, at the start Planned Quantity = Base Quantity). | SPROC-12864 |
| Improvement | Order Recommendation: the saving option is blocked when Revision is not selected. | - |
| Improvement | Recommendation tab: Item Description and Revision name columns added. | - |
| Improvement | The Advance Settings section is hidden in the Planning Horizon tab. | - |
| Bug | All Items: results are not readable when quantities are too big. | - |
| Bug | Issues related to calculation of selected quantity and open quantity after the document generation. | - |
| Bug | Order Recommendation: an error occurs upon saving a document after changing Order Type in specific cases. | SPROC-12864 |
| Bug | Order Recommendation: <li>it is not possible to save Release Date, Unit Price and Discount.</li><li>saving a Due Date does not save the exact chosen date</li> | - |
| Bug | Order Recommendation: quantities are incorrectly recalculated when Base Quantity is changed a second time. | - |
| Bug | Order Recommendation: the Relation Map is now opened in a new window due to precious problems with the unstable display of it in the Order Recommendation. | - |
| Bug | Results: scrolling does not work (works after clicking Expand and then Collapse All). | - |
| Improvement | The calling of Relationship Map on Order Recommendation (while working in the browser) requires re-login. | - |
