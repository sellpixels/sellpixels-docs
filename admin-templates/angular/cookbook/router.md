# Router

## Router Configuration

References: [https://angular.io/guide/router](https://angular.io/guide/router)

Configure routers in `src/router.js`

{% code title="src/app/app-routing.module.ts" %}
```javascript
const routes: Routes = [
  {
    path: '',
    redirectTo: 'dashboard/alpha',
    pathMatch: 'full',
  },
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
      ...
    ],
  },
]
```
{% endcode %}

## History Mode \(removing /\#/ hash from Url\)

{% hint style="info" %}
Don't forget configure rewrites on your server. Read more: [https://router.vuejs.org/guide/essentials/history-mode.html](https://router.vuejs.org/guide/essentials/history-mode.html) \(from vue docs\)
{% endhint %}

Set `useHash: false` in `src/app/app-routing.module.ts`

{% code title="src/app/app-routing.module.ts" %}
```javascript
RouterModule.forRoot(routes, {
  useHash: true,
  preloadingStrategy: AppPreloader,
}),
```
{% endcode %}

## Routes Guard

Simple routes guard path `src/app/components/{templateName}/layout/Guard/auth.guard.ts`. 

This component simply return true or false in case if user logged in or not. In our case User will be redirected to Login page if he is not logged in.

Details: [https://angular.io/guide/router](https://angular.io/guide/router)

