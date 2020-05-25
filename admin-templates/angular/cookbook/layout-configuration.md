# Layout Configuration

Template has three layouts:

* Main
* Auth \(for Login, Lockscreen, etc.. pages\)
* Public \(empty layout\)

You can set for any routes separately in `app-routing.module.ts` 

{% code title="src/router.js" %}
```javascript
import { LayoutAuthComponent } from 'src/app/layouts/Auth/auth.component'
import { LayoutMainComponent } from 'src/app/layouts/Main/main.component'

const routes: Routes = [
  // Main Layout
  {
    path: '',
    component: LayoutMainComponent,
    children: [
      {
        path: 'dashboard',
        canActivate: [AuthGuard],
        loadChildren: () =>
          import('src/app/pages/dashboard/dashboard.module').then(m => m.DashboardModule),
      },
    ],
  },
  ...
  // Auth Layout
  {
    path: 'auth',
    component: LayoutAuthComponent,
    children: [
      {
        path: '',
        loadChildren: () => import('src/app/pages/auth/auth.module').then(m => m.AuthModule),
      },
    ],
  },
]
```
{% endcode %}

