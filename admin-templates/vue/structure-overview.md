# Structure Overview

## Components Overview

Template contains next component files and folders:

| Folder | Description |
| :--- | :--- |
| **components/kit/core** | KIT mixins.scss, core, utils, measurement styles, etc |
| **components/kit/vendors** | KIT third-party plugin styles |
| **components/kit/widgets** | KIT demo widgets \(general, charts, etc...\) |
| **components/{templateName}/layout** | Template layout components \(Menu, Topbar, etc...\) |
| **components/{templateName}/styles** | Template styles & mixins |
| **components/{templateName}/system** | Template system components \(404, Auth pages\) |
| **components/mixins.scss** | Shared mixins.scss files |

## Layouts Management

{% page-ref page="cookbook/layout-configuration.md" %}

{% page-ref page="cookbook/layout-settings.md" %}

## Best Practices

### Building Your App

There are some tips for creating an architecture for your application:

* Copy the KIT widget to the `components/{app}` folder and rename the widget as you need it
* Place your layout components \(such as `Menu`, `Footer`, ...\) to `components/{layout}`
* Import the shared mixins file `components/mixins.scs` into your new components
* Import the new widget to any place in your project

{% hint style="info" %}
It is recommended not to edit the `kit/core` and `kit/vendors` folders, this will prevent problems when updating widgets and applications from future releases.

Instead, redefine the mixins variables in the shared `mixins.scss` file or import the redefined styles into `global.scss`
{% endhint %}

### Recommended folder structure:

```text
components
├─ app                // your components folder, name it as you want
│  ├─ Userlist
│  └─ BudgetChart
│   
├─ layout             // your layout components folder, name it as you want
│  ├─ Topbar
│  └─ Menu
│
├─ {templateName}     // Folder with Template components
├─ kit                // KIT folder with core & vendors styles and demo widgets
└─ mixins.scss        // Shared mixins.scss

views
├─ dashboard          // page with imports from "components" folder
└─ profile            // page with imports from "components" folder
```

