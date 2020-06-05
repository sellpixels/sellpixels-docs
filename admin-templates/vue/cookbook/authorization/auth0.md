# Auth0

Auth0 auth provider implementation is a little complex than JWT or Firebase. It uses Auth0 app wrapper and React context for handling current state. Follow this article to add this provider to template: 

[https://auth0.com/docs/quickstart/spa/vuejs/01-login](https://auth0.com/docs/quickstart/spa/vuejs/01-login)

The differences between this article and our templates implementation is just in that user state handled by Redux in our templates. That's mean you should additionally set user state by dispatching `user/SET_STATE` action:

```javascript
// initialize the auth0 library
async created() {
  // Create a new instance of the SDK client using members of the given options object
  this.auth0Client = await createAuth0Client({
    ...
  })

  try {
    ...
  } catch (e) {
    ...
  } finally {
    ...
    
    // should update user state in store
    this.$store.commit('user/SET_STATE', {
      loading: false,
      authorized = await this.auth0Client.isAuthenticated(),
      // id: user.name,
      // name: user.name,
      // role: user.role,
      // email: user.email,
      // avatar: user.avatar,
    })
  }
}

```

{% hint style="info" %}
Any actions from `src/store/user/indes.js` should not be used for auth0 provider. It used for Firebase or JWT auth providers.
{% endhint %}

