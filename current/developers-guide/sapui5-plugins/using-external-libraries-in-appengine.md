# Using External Libraries in AppEngine

The following example shows how to consume the external library in an AppEngine plugin (TypeScript). We will use the SheetJS library.

:::warning
To include an external library in production code only, you need to complete 1 to 5 points.
:::

## Requirements

1. Node JS (`https://nodejs.org/en/`).

2. Yeoman (`https://github.com/yeoman/yo`) .

yo

```
npm install --global yo
```

3. Easy UI5 ()

Easy UI5 ()

```
npm install -g yo generator-easy-ui5
```

## Step-by-step instruction

1. Install XLSX. Open your project (the www folder) and type in the terminal:

npm install

```
npm i xlsx
```

2. Use it somewhere in your code (code competition should work). For example:

Testxlsx.ts

```
import BaseController from "computec/appengine/core/BaseController";
import { utils } from "xlsx"
 
/**
 * @namespace extlibtest.controller
 */
export default class Testxlsx extends BaseController {
    onInit(): void {
        super.onInit();
        this.setPageName("Test XLSX");
    }
    onTestXLSX() {
        console.log(utils.book_new());
    }
}
```

3. Add UI5-tooling-modules that will pack external library into the build. In the terminal:

UI5 Tooling Extensions

```
# 1. Start Easy UI5 generator add-extension
/> yo easy-ui5 add-extension
# 2. Select only Tooling and hit enter
# 3. Select ui5-tooling-modulesadd-extension
# 4. Set verbose to n
# 5. Set prependPathMappings to y
 
It should look like this:
yo easy-ui5 add-extension
 
     _-----_
    |       |    ╭──────────────────────────╮
    |--(o)--|    │  Welcome to the easy-ui5 │
   `---------´   │     3.5.1 generator!     │
    ( _´U`_ )    ╰──────────────────────────╯
    /___A___\   /
     |  ~  |
   __'.___.'__
 ´   `  |° ´ Y `
 
(node:40568) ExperimentalWarning: The Fetch API is an experimental feature. This feature could change at any time
(Use `node --trace-warnings ...` to show where the warning was created)
? Which extension type would you like to add? Tooling
? Choose your tooling extensions? ui5-tooling-modules - UI5 tooling extensions to load and convert node modules as UI5 AMD-like modules
Set your variables for ui5-tooling-modules
? Set 'verbose' - Enables verbose logging (default to `false`) Yes
? Set 'prependPathMappings' - Prepends the path mappings for the UI5 loader to the `Component.js` which allows to run the Component using 3rd party libs in e.g. Fiori launchpad environments (default to
`false`) (Y/n) yt
```

4. Open ui5.yaml and fix name in builder → customTasks. Change ui5-tooling-modules to ui5-tooling-modules-task. Finally, it should look similar to this:

ui5.yaml

```
specVersion: '2.0'
metadata:
  name: extlibtest
type: application
framework:
  name: SAPUI5
  version: 1.90.0
  libraries:
    - name: sap.m
    - name: sap.ui.core
    - name: sap.ui.unified
    - name: themelib_sap_fiori_3
server:
  customMiddleware:
    - name: ui5-tooling-modules-middleware
      afterMiddleware: compression
      configuration:
        verbose: true
        prependPathMappings: true
    - name: ui5-middleware-livereload
      afterMiddleware: ui5-tooling-modules-middleware
      configuration:
        debug: true
        extraExts: xml,json,properties
        port: 35729
        path: webapp
builder:
  customTasks:
    - name: ui5-tooling-modules-task
      afterTask: replaceVersion
      configuration:
        verbose: false
        prependPathMappings: true
```

5. Build:

```
npm run build
```

6. Copy the resources folder from the dist folder to the webapp folder.

:::warning
This needs to be done only once during the development phase. Thanks to this and mapping from point 7, you can test your plugin that consumes external library from the webapp folder just after TypeScript transpilation – without a need to build each time.

It is possible that you will need to rebuild your solution after this step in order to copy this file to plugins folder.
:::

7. Add mapping to Component.ts:

Component.ts

```
sap.ui.loader.config(
            {
                paths: { "xlsx": sap.ui.require.Url("externallibs/resources/xlsx")}
            }n
        );
```

Finally, Comonent.ts should look similar to this:

Component.ts

```
import UIComponent from "computec/appengine/ui/core/UIComponent";
import { $UIComponentSettings } from "sap/ui/core/UIComponent";
 
/**
 * @namespace externallibs
*/
export default class Component extends UIComponent {
 
    constructor(mSettings?: $UIComponentSettings) {
        super(mSettings);
        sap.ui.loader.config(
            {
                paths: { "xlsx": sap.ui.require.toUrl("externallibs/resources/xlsx")}
            }
        );
    }
    public static metadata = {
        manifest: "json"
    }
 
    init() {
        super.init();
        super.onInit();
        this.getRouter().initialize();
    }
}
```