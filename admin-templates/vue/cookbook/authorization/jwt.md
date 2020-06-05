# JWT

JWT auth uses `axios` for handling auth process. Configure `axios` headers \(Authorization or AccessToken, depends on what accept your backend\) in `src/services/axios/index.js` `axios` will hook accessToken from localStorage

### Configuring

Replace `firebase` configuration with yours in `src/services/firebase/index.js`

{% code title="src/services/jwt/index.js" %}
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
state: {
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

`src/store/user/index.js` file handles app authorization process. The app should get user data from  API and save user state to store.

{% code title="src/store/user/index.js" %}
```javascript
import * as jwt from '@/services/jwt'

actions: {
  LOGIN({...}, { payload }) {
    const { email, password } = payload
    jwt.login(email, password).then(success => {...}
  },
  REGISTER({...}, { payload }) {
    const { email, password, name } = payload
    jwt.register(email, password, name).then(success => {...}
  },
  LOAD_CURRENT_ACCOUNT({...}) {
    jwt.currentAccount().then(success => {...}
  },
  LOGOUT({...}) {
    jwt.logout().then(success => {...}
  },
}
```
{% endcode %}

On first app load `App.vue` triggers `user/LOAD_CURRENT_ACCOUNT` for checking user state:

```javascript
mounted() {
  this.$store.dispatch('user/LOAD_CURRENT_ACCOUNT')
}
```

### Dispatching Auth Methods

{% code title="src/components/{templateName}/system/Auth/Login/index.vue" %}
```javascript
methods: {
  handleSubmit(e) {
    e.preventDefault()
    this.form.validateFields((err, values) => {
      if (!err) {
        this.$store.dispatch('user/LOGIN', { payload: values })
      }
    })
  },
}
```
{% endcode %}

{% code title="src/components/{templateName}/system/Auth/Register/index.vue" %}
```javascript
methods: {
  handleSubmit(e) {
    e.preventDefault()
    this.form.validateFields((err, values) => {
      if (!err) {
        this.$store.dispatch('user/REGISTER', { payload: values })
      }
    })
  },
}
```
{% endcode %}

{% code title="src/components/{templateName}/layout/Topbar/UserMenu/index.vue" %}
```javascript
methods: {
  logout() {
    this.$store.dispatch('user/LOGOUT')
  },
},
```
{% endcode %}



