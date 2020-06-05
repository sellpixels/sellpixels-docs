# Auth0

Auth0 auth provider implementation is a little complex than JWT or Firebase. It uses Auth0 service for handling current state. Follow this article to add this provider to template: 

[https://auth0.com/docs/quickstart/spa/angular2/01-login](https://auth0.com/docs/quickstart/spa/angular2/01-login#restoring-login-state-with-social-providers)

The differences between this article and our templates implementation is just in that user state handled by NgRx in our templates. That's mean you should additionally set user state by dispatching `UserActions.LoadCurrentAccountSuccessful`action:

```javascript
authComplete$.subscribe(([user, loggedIn]) => {
  this.store.dispatch(
    new userActions.LoadCurrentAccountSuccessful({
      loading: false,
      authorized: loggedIn,
      // id: user.id,
      // name: user.name,
      // role: user.role,
      // email: user.email,
      // avatar: user.avatar,
    }),
  )
});
```

{% hint style="info" %}
Any effects from `src/app/store/user/effetcs.ts` should not be used for auth0 provider. It used for Firebase or JWT auth providers.
{% endhint %}

