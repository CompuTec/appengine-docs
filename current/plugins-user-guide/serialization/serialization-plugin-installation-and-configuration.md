---
sidebar_position: 2
---

# Serialization Plugin Installation and Configuration

The standard plugin installation and configuration is described in the AppEngine documentation here.

Here you can find information about additional action that you have to take on top of the standard plugin installation be able to fully use the Serialization plugin.
Please remember to install versions of the components according to the version table available here.

---

## Prerequisites

### ProcessForce and CompuTec License Server is installed and configured

For more information click [here](/docs/processforce/administrator-guide/licensing/license-server/overview).

### CompuTec WMS is installed and configured

For installation please follow this link: Installation.

For configuration please follow this link: [Custom Configuration](/docs/wms/administrator-guide/custom-configuration/overview/).

## AppEngine and serialization plugin installation and configuration

For AppEngine installation please follow this link: [Installation](/docs/appengine/administrators-guide/installation/).

For plugin installation please follow this link: [Configuration and Administration](/docs/appengine/administrators-guide/configuration-and-administration/overview/).

Please note: after updating the Serialization plugin and restarting the App Engine, remember to update the schema as per the procedure here.

## Enabling Serialization

### CompuTec WMS

    1. Enter (10) Computec AppEngine address in [WMS Server](/docs/wms/administrator-guide/installation/wms-server/overview/) settings:

    ![CompuTec AppEngine Address (in WMS server settings)](./media/serialization/wms-settings.png)

    2. Enable Serialization in [Custom Configuration](/docs/wms/administrator-guide/custom-configuration/overview/):

    ![Serialization](./media/serialization/image2020-1-14-16-40-22.png)

    3. Remember to customize main menu options to prepare and set menu with Serialization workflow. For this purpose please follow Custom Config Function: [Manager](/docs/wms/administrator-guide/custom-configuration/custom-configuration-functions/manager/overview/) and sub-function: [Interface Design Manager](/docs/wms/administrator-guide/custom-configuration/custom-configuration-functions/manager/interface-design-manager):

    ![Serialization](./media/serialization/image2020-1-14-16-51-11.png)

### ProcessForce

As an option you can call Serialization plugin from inside the Process Force:

![Serialization Plugin (from inside the ProcessForce)](./media/serialization/image2020-1-18-8-44-13.png)

To do this, check the following checkbox:

![Serialization Plugin (from inside the ProcessForce)](./media/serialization/image2020-1-18-8-33-41.png)

Enter AppEngine URL, e.g. `http://{host}:54000`, click Update and restart SAP Business One.
