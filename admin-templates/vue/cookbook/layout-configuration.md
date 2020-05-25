# Layout Configuration

Template has three layouts:

* Main
* Auth \(for Login, Lockscreen, etc.. pages\)
* Public \(empty layout\)

You can set for any routes separately in `src/router.js` 

{% code title="src/router.js" %}
```javascript
import AuthLayout from '@/layouts/Auth'
import MainLayout from '@/layouts/Main'

routes: [
  // Main Layout
  {
    path: '/',
    redirect: 'dashboard/alpha',
    component: MainLayout,
    meta: {
      authRequired: true,
      hidden: true,
    },
    children: [
      ...
    ]
  },
  ...
  // Auth Layout
  {
    path: '/auth',
    component: AuthLayout,
    redirect: 'auth/login',
    children: [
      {
        path: '/auth/404',
        meta: {
          title: 'Error 404',
        },
        component: () => import('./views/auth/404'),
      },
    ],
  },
]

```
{% endcode %}

