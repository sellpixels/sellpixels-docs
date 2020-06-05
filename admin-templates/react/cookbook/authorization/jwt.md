# JWT

JWT auth uses `axios` for handling auth process. Configure `axios` headers \(Authorization or AccessToken, depends on what accept your backend\) in `src/services/axios/index.js` `axios` will hook accessToken from localStorage

### Authorization Methods

Check `src/services/jwt/index.js`  file for next functions:

{% code title="src/services/jwt/index.js" %}
```javascript
export async function login(email, password) { ... } // sign in procedure
export async function register(email, password, name) { ... } // sign up procedure
export async function currentAccount() { ... } // get current authorized user data
export async function logout() { ... } // logout user
```
{% endcode %}

 For switching app to authorized state you should set `authorized` prop to `true`

{% code title="src/redux/user/reducers.js" %}
```javascript
const initialState = {
  id: 'USER_ID',
  name: 'USER_NAME',
  role: 'USER_ROLE',
  email: 'USER@EMAIL.COM',
  avatar: '',
  authorized: true, // user is authorized
  loading: false, // handles user fetching state, eg. set Sign In button to loading state
}
```
{% endcode %}

`src/redux/user/sagas.js` file handles app authorization process. The app should get user data from firebase API and save user state to store.

{% code title="src/redux/user/sagas.js" %}
```javascript
import * as jwt from 'services/jwt'

export function* LOGIN() {
  yield call(jwt.login, email, password)
  ...
}

export function* REGISTER() {
  yield call(jwt.register, email, password)
  ...
}

export function* LOAD_CURRENT_ACCOUNT() {
  yield call(jwt.currentAccount, email, password)
  ...
}

export function* LOGOUT() {
  yield call(jwt.logout, email, password)
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

### Dispatching Auth Methods

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

{% code title="src/components/{templateName}/system/Auth/Register/index.js" %}
```javascript
const onFinish = values => {
  dispatch({
    type: 'user/REGISTER',
    payload: values,
  })
}
```
{% endcode %}

{% code title="src/components/{templateName}/layout/TopBar/UserMenu/index.js" %}
```javascript
const logout = e => {
  e.preventDefault()
  dispatch({
    type: 'user/LOGOUT',
  })
}
```
{% endcode %}

