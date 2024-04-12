---
sidebar_position: 2
---

# Source Creator

This option allows advanced configuration of data presented in [Custom Reports and Analytics of the Analytical Page](../analytical-page/overview.md#usage).

---

To open the option, click the Analytical Page button (1.) in Launchpad and then the Go To Source Creator button:

![Screenshot](./media/source-creator/source-creator-button.png)

This leads to the Source List:

![Screenshot](./media/source-creator/source-list.png)

This is a list of sources currently used in the [Variants](/docs/appengine/appengine-users-guide/analytical-page/overview#variants) used in Analytical views.

You can add a new Variant by clicking the Add New Source button:

## Source tab

![Screenshot](./media/source-creator/source-configuration.png)

Here you can configure:

- the name of the Variant
- the source – an MS SQL query that will be a source of data for the Variant
available fields (for a specific query) – the list is available after clicking the Show - Preview button after entering a query. Here you can modify the Variant by changing values for specific lines. You can set:

        - Displayed Column Name
        - Column Description
        - Column Type
        - Set a Custom Collection (different than in related Table View)

          <details>
          <summary>Click here to find out more.</summary>
          <div>
          A collection is a group of vocabulary values available for some fields, e.g., Status - Started, Closed, etc.

          In the context of the Analytical Page, collections are used for filters. In this case, there is a special icon that you can click to open a list of values to choose from:

          ![Screenshot](./media/source-creator/document-type.png)

          ![Screenshot](./media/source-creator/document-type-options.png)

          You can either take the values from the related table (the Table/View Collection option) or set them manually (the Custom Collection option):

          ![Screenshot](./media/source-creator/choose-collection-type.png)

          The Table/View Collection:

          ![Screenshot](./media/source-creator/table-view.png)

          The Custom Collection option:

          ![Screenshot](./media/source-creator/custom-collection.png)
          </div>
          </details>

## Variants tab

In this tab, you can manage (add, edit, delete) variants for a source:

![Screenshot](./media/source-creator/variants.png)

Click the + Add Variant to add a Variant:

![Screenshot](./media/source-creator/variant-basic-settings-1.png)

Here you can define:

- Basic Settings: Name, View, Default, Accessibility (Public/Private);
- Table Startup Settings: settings related to the [Table view](../analytical-page/overview.md#table-options).
- Chart Startup Settings: settings related to the [Chart view](../analytical-page/overview.md#chart-options).
- Visual Filter Startup Settings: settings related to the [Charts](../analytical-page/overview.md#chart-options).
