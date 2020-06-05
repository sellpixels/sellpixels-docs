# Code Splitting

Implement routing-level code splitting & async loading with `React.lazy`.

{% code title="src/router.js" %}
```javascript
import React, { lazy, Suspense } from 'react'

// routes config
const routes = [
  // System Pages
  {
    path: '/user/login',
    component: lazy(() => import('pages/user/login')),
    exact: true,
  },
  ...
]

// mapping routes config to routes
{routes.map(({ path, Component, exact }) => (
  <Route
    path={path}
    key={path}
    exact={exact}
    render={() => {...}}
  />
))}
```
{% endcode %}

