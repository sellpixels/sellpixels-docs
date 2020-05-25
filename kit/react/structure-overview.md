# Structure Overview

## Components Overview

Kit contains next files and folders: `kit/core`, `kit/vendors`, `kit/widgets`, `kit/mixins.scss`

| Folder | Description |
| :--- | :--- |
| **components/kit/core** | Contains mixins.scss, core, utils, measurement styles, etc |
| **components/kit/vendors** | Contains third-party plugin styles |
| **components/kit/widgets** | Contains widgets \(general, charts, etc...\) |
| **components/mixins.scss** | Shared mixins.scss files |

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
├─ app
│  ├─ Userlist        // your component
│  └─ BudgetChart     // your new component
│   
├─ layout
│  ├─ Topbar          // your new layout component
│  └─ Menu            // your new layout component
│
├─ kit                // KIT folder with core & vendors styles and demo widgets
└─ mixins.scss        // Shared mixins.scss

pages
├─ dashboard          // page with imports from "components" folder
└─ profile            // page with imports from "components" folder
```

