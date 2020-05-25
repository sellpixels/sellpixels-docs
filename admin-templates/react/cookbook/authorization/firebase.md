# Firebase \(default\)

Our templates uses `firebase` service for default app authorization.

Check `src/services/firebase.auth.service.js`  file for next functions:

{% code title="src/services/firebase.auth.service.js" %}
```javascript
export async function login(email, password) { ... } // auth procedure
export async function currentAccount() { ... } // get current authorized user data
export async function logout() { ... } // logout user
```
{% endcode %}

 `src/redux/user/sagas.js` file handles app authorization process. 

{% code title="src/models/user.js" %}
```javascript
import { login, currentAccount, logout } from 'services/firebase.auth.service'

export function* LOGIN() {
  ...
}

export function* LOAD_CURRENT_ACCOUNT() {
  ...
}

export function* LOGOUT() {
  ...
}

export default function* rootSaga() {
  yield all([
    takeEvery(actions.LOGIN, LOGIN),
    takeEvery(actions.LOAD_CURRENT_ACCOUNT, LOAD_CURRENT_ACCOUNT),
    takeEvery(actions.LOGOUT, LOGOUT),
    LOAD_CURRENT_ACCOUNT(), // run once on app load to check user auth
  ])
}
```
{% endcode %}

#### Auth Method on Login Page

{% code title="src/components/{templateName}/system/Auth/Login/index.js" %}
```javascript
const onFinish = values => {
  dispatch({
    type: 'user/LOGIN',
    payload: values,
  })
}
```
{% endcode %}

