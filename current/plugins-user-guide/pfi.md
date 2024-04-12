---
sidebar_position: 8
---

# PFI

PFI (short for ProcessForce Import) is a plugin that allows importing/updating data to ProcessForce objects. The idea behind this plugin is to be a simplifier, swifter, and more adjustable alternative for [PowerShell updates](/docs/processforce/developer-guide/data-import/overview/).

(The video was recorded on a pre-release version and the interface differs slightly in the released version.)

## Start

### Prerequisites

The ProcessForce plugin has to be installed and enabled for the company you want to use ProcessForce Import with.

If a new UDF is added to a ProcessForce object, the AppEngine service has to be restarted in order to see UDF as a column in a PFI template.

### Installation

Click [here](/docs/appengine/administrators-guide/configuration-and-administration/overview#plugins) to get to know more about AppEngine plugin installation.

## Usage

Once the plugin is installed, its tile is available in the [Launchpad](/docs/appengine/appengine-users-guide/launchpad/) Upon opening the plugin you can see a the ProcessForce objects represented by tiles. Choose the one you want to work with (scroll to get to other objects):

    ![Screenshot](./media/pfi/pfi-main.png)

The example view (Bill of Materials in this case):

![Screenshot](./media/pfi/pfi-bill-of-materials.png)

### Header

Here you can see the object's name (upper-left corner). On the right from it you can find all the objects related to the main one. Click the name (of the main or related objects) to display all the columns of the object (properties of the database table) in the table below. The numbers in the brackets represents object's level, e.g. Bill of Materials 0 > Routing 1 > Routing Operations 2 > Routing Operations Properties 3.

<u>Download Excel</u> – download the content of the table (with the columns names) displayed after clicking any object as a Microsoft Excel file. If you did not load any sample (check the Load Sample option below), you can download an empty file (just with column names). You can then add or update the content of the file in Microsoft Excel, save it and then upload it to the plugin with the next option (Import from Excel).

<u>Download with advanced settings</u> – option available from the arrow down next to Download Excel option:

    ![Screenshot](./media/pfi/pfi-advanced-download.png)

<u>Include Error Messages</u> – after importing entries, system returns results. With this setting user can download import results and see error description.

<u>Upload data from Excel</u> – import previously downloaded Microsoft Excel file (see the option above), updated with data. Blank Excel cell in does not update the related property as blank. Use slash (/) to set property to blank. Leaving a cell blank means that the property will not be updated. It will be skipped during import (populated by system if new entry/line or values will stay the same if there were values there already) and marked with the following symbol:  .

<u>Load Sample</u> – using this option you can load data from the database to the table, download it (using the Download Excel Template), update it and upload it again to the table (using Import from Excel). This option allows to mass update of records. Usage: click the option, filter by choosing values in fields related to a specific form (optional), choose how many records you want to load, and click Load. A a specific object is loaded with all the lower level objects (e.g. Bill of Materials with Items, CoProducts, Scraps etc.)

<u>Import to SAP</u> – this option imports data from the matrix to a database

<u>Download Template CSV</u> – downloads a template for a specific, currently displayed object, e.g. Bill of Materials' Items (unlike the Download with advanced settings, Export data to CSV file which exports templates for the displayed object and all the lower level objects).

<u>Upload data from CSV</u> – this option is similar to the Upload data from Excel, but for CSV files use.

### Filters

You can filter the result table by putting values in specific fields. You can also adapt the filters section: choose which fields are displayed to be used.

<u>Read-only fields</u> – If it is not checked, only fields that can be updated will be displayed. If checkbox is checked, you can see all the objects. Read-only objects are marked with a padlock icon then. Example: ![Screenshot](./media/pfi/pfi-padlock.png)

### Table

Here you can find a table of data related to an object chosen in the header: all the columns followed by the UDFs (the far right columns of the table). This data can be then import to SAP (using an option in the header). The table has to be populated with data first (by using option in the header).

<u>Import Key</u> – the first column in the PFI matrix. It is a link column for the template (e.g. links Bill of Materials with its lower level objects).

<u>The key icon</u> – marks primary field for this object. If you leave this field empty during edition, it will be considered as adding a record. If there is any value here, this record will be updated.

<u>Action</u> – after uploading an Excel, the Action column determines manipulation type: Add/Update.

<u>Import Status</u> – indicator of successful/failed import of a specific line to SAP Business One.
