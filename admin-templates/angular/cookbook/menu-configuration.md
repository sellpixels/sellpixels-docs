---
description: Main Menu overview
---

# Menu Configuration

By default menu `src/app/components/{templateName}/layout/Menu/` has few render variations: leftMenu \(with mobile drawer or not\) and topMenu, it depends on `isMenuTop` setting from global settings state.

### Menu items

Menu items configured in `src/app/services/menu.service.config.ts`

{% code title="src/app/services/menu.service.config.ts" %}
```javascript
export const getMenuData: any[] = [
  return [
    {
      category: true,           // render category
      title: 'Dashboards',      // category title
    },
    {
      title: 'Dashboards',      // item title
      key: 'dashboards',        // key (required by antd menu)
      icon: 'fe fe-home',       // icon class
      roles: ['admin'],         // set user roles with access to this route
      count: 4,                 // item badge
      children: [               // render submenu
        {
          title: 'Dashboard Alpha',
          key: 'dashboard',
          url: '/dashboard/alpha',
        },
        ...
      ]
    },
    ...
  ]
}
```
{% endcode %}

