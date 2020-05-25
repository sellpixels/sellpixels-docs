# Router

## Router Configuration

Reference: [https://reacttraining.com/react-router/web/guides/quick-start](https://reacttraining.com/react-router/web/guides/quick-start)

Configure routes in `"src/router.js"` and add page components to `"src/page/*"` folder.

{% code title="src/router.js" %}
```javascript
// routes config
const routes = [
  // System Pages
  {
    path: '/user/login',
    Component: lazy(() => import('pages/dashboard/alpha')),
    exact: true,
  },
  ...
]
```
{% endcode %}

## History Mode \(removing /\#/ hash from Url\)

{% hint style="info" %}
Don't forget configure rewrites on your server. Read more: [https://create-react-app.dev/docs/deployment/](https://create-react-app.dev/docs/deployment/)
{% endhint %}

Replace 

{% code title="src\\index.js" %}
```javascript
import { createHashHistory } from 'history'
...
const history = createHashHistory()
```
{% endcode %}

With

{% code title="src\\index.js" %}
```javascript
import { createBrowserHistory } from 'history'
...
const history = createBrowserHistory()
```
{% endcode %}

