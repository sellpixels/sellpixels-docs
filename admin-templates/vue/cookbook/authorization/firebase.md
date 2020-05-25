# Firebase \(default\)

Clean UI uses `firebase` service for default app authorization. In the app Firebase Auth registered as a plugin and available as  `$auth` object.

#### Injection

{% code title="src/main.js" %}
```javascript
import FirebaseAuthService from './services/firebase.auth.service'
...
Vue.use(FirebaseAuthService)
```
{% endcode %}

#### Firebase Plugin

{% code title="src/services/firebase.auth.service.js" %}
```javascript
...
const config = {
  apiKey: ...,
  authDomain: ...,
  databaseURL: ...,
  projectId: ...,
  storageBucket: ...,
  messagingSenderId: ...,
}

export default {
  install: (Vue, options) => {
    const firebaseApp = firebase.initializeApp(config)
    const auth = firebaseApp.auth()
    Vue.prototype.$auth = {
      login: async (username, pass) => {
        return auth.signInWithEmailAndPassword(username, pass)
      },
      logout: async () => {
        router.push('/user/login')
        await auth.signOut()
      },
    }
    auth.onAuthStateChanged(user => {
      store.commit('UPDATE_USER', { user })
    })
  },
}
```
{% endcode %}

#### Auth Method on Login Page

{% code title="src/components/{templateName}/system/Auth/Login/index.vue" %}
```javascript
methods: {
  handleSubmit(e) {
    e.preventDefault()
    this.form.validateFields((err, values) => {
      if (!err) {
        this.$nprogress.start()
        this.$auth.login(values.email, values.password)
          .then(() => {
            this.$nprogress.done()
            this.$notification['success']({
              message: 'Logged In',
              description: 'You have successfully logged in to Clean UI Vue Admin Template!',
            })
          })
          .catch((error) => {
            this.$nprogress.done()
            this.$notification['warning']({
              message: error.code,
              description: error.message,
            })
          })
      }
    })
  },
},
```
{% endcode %}

