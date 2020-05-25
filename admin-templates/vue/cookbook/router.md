# Router

## Router Configuration

Reference: [https://router.vuejs.org/](https://router.vuejs.org/)

Configure routers in `src/router.js`

{% code title="src/router.js" %}
```javascript
routes: [
  {
    path: '/',
    redirect: 'dashboard/alpha',
    component: MainLayout,
    meta: {
      authRequired: true,
      hidden: true,
    },
    children: [
      // Dashboards
      {
        path: '/dashboard/alpha',
        meta: {
          title: 'Dashboard Alpha',
        },
        component: () => import('./views/dashboard/alpha'),
      },
      ...
    ],
  },
]
```
{% endcode %}

## History Mode \(removing /\#/ hash from Url\)

{% hint style="info" %}
Don't forget configure rewrites on your server. Read more: [https://router.vuejs.org/guide/essentials/history-mode.html](https://router.vuejs.org/guide/essentials/history-mode.html)
{% endhint %}

Uncomment `mode: 'history'` in `src/router.js`

{% code title="src/router.js" %}
```javascript
const router = new Router({
  base: process.env.BASE_URL,
  // mode: 'history',
  scrollBehavior() {
    return { x: 0, y: 0 }
  },
  ...
}
```
{% endcode %}

## Routes Guard

See `src/router.js` for `router.beforeEach` method. On every route change the app checked authorization and if user is not authorized will redirect him to `/user/login` route.

Details: [https://router.vuejs.org/guide/advanced/navigation-guards.html](https://router.vuejs.org/guide/advanced/navigation-guards.html)

