# Firebase

Our templates uses `firebase` service for default app authorization.

### Configuring

Replace `firebase` configuration with yours in `src/services/firebase/index.js`

{% code title="src/services/firebase/index.js" %}
```javascript
const firebaseConfig = {
  apiKey: '',
  authDomain: '',
  databaseURL: '',
  projectId: '',
  storageBucket: '',
  messagingSenderId: '',
}
```
{% endcode %}

### Authorization Methods

Check `src/services/firebase/index.js`  file for next functions:

{% code title="src/services/firebase/index.js" %}
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

{% code title="src/redux/user/.js" %}
```javascript
import * as firebase from 'services/firebase'

export function* LOGIN() {
  yield call(firebase.login, email, password)
  ...
}

export function* REGISTER() {
  yield call(firebase.register, email, password)
  ...
}

export function* LOAD_CURRENT_ACCOUNT() {
  yield call(firebase.currentAccount, email, password)
  ...
}

export function* LOGOUT() {
  yield call(firebase.logout, email, password)
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

