---
sidebar_position: 1
---

# Release Notes

:::info
The latest Installer is available to download from [here](/docs/appengine/download/pfi/).
:::

## PFI 1.10.6 - 22 April 2024

| Issue Type | Release Note | Related issue/s |
| --- | --- | --- |
| Bug | After loading sample data from SAP for Bill of Materials there were empty lines in scraps and coproducts in some cases. | - |
| Bug | Error during BOM import through PFI in some cases | - |
| Bug | PFI - issues with refreshing data after import from file | - |
| Improvement | Validating imported data types | - |

## PFI 1.10.5 - 5 June 2023

| Issue Type | Release Note | Related issue/s |
| --- | --- | --- |
| Improvement | A new button in the filter to open a dialog. The Dialog can get keys in various formats (you can also get elements from MS Excel,) and also you can change separators of the keys and, after accepting data, the keys we have on the filter input so you get in table elements only with the given keys. | - |

---

## PFI 1.10.4 - 15 December 2022

| Issue Type | Release Note | Related issue/s |
| --- | --- | --- |
| Bug | A default value was removed from the filter properties. | SPROC-14164 |
| Improvement | A progress bar is displayed during import from a file. | - |
| Improvement | It is now possible to cancel loading sample data, importing from MS Excel as well as importing to SAP. | - |
| Improvement | The default number of entries to load is now set to 1000. | - |
| Bug | The problem with loading a large number of entries has been fixed. A progress bar was added that shows the progress of data. | - |

---

## PFI 1.10.3 - 10 October 2022

| Issue Type | Release Note | Related issue/s |
| --- | --- | --- |
| Bug | Additional Batch Details: cannot import values set for User Defined Fields. | SPROC-13855 |
| Bug | Downtime Reason: no Name column displayed in the plugin for this form. | - |
| Bug | Improved field type recognition. | - |
| Bug | Resource: no matching Records found for filtering by U_RscCode, even though the related values are present in the database. | - |

---

## PFI 1.10.2, 1.93.2 - 4 July 2022

| Issue Type | Release Note | Related issue/s |
| --- | --- | --- |
| Improvement | PFI is now accessible from the SAP Business One Menu. | - |
| Bug | An error occurs upon attempts to Load Sample Data From SAP for objects with Reason in its name. Error message: 'select' and 'expand' cannot be both null or empty. | SPROC-13396 |
| Bug | Downloading a CSV file, making changes, and uploading again causes an error in specific cases. Error message: Data import from file failed. Exception while checking keys: A binary operator with incompatible types was detected. | SPROC-13443 |
| Bug | Load Sample Data From SAP: Bill of Materials: the system clears filtering fields for UDFs in the Sample selection settings. | SPROC-13450 <br/>SPROC-13456 |
| Bug | The plugin freezes upon clicking Import to SAP, during loading data. A data preparation progress bar has been added to indicate the process. | SPROC-13450 <br/>SPROC-13456 |
| Bug | Some of the UI tables (e.g. in the Bill of Materials object) do not list any records. | - |
| Bug | The scroll bar does not go to the bottom of a UI table (e.g. for the Task object), which results in a lack of access to the lowest lines. | - |
