# Auth0

Auth0 auth provider implementation is a little complex than JWT or Firebase. It uses Auth0 app wrapper and React context for handling current state. Follow this article to add this provider to template: 

[https://auth0.com/blog/authenticating-your-first-react-app/](https://auth0.com/blog/authenticating-your-first-react-app/)

The differences between this article and our templates is just in user state handled by Redux in our templates. That's mean you should additionally set user state by dispatching `user/SET_STATE` action:

```javascript
// initialize the auth0 library
initializeAuth0 = async () => {
    const auth0Client = await createAuth0Client(this.config);
    const isAuthenticated = await auth0Client.isAuthenticated();
    const user = isAuthenticated ? await auth0Client.getUser() : null;

    this.setState({ auth0Client, isLoading: false, isAuthenticated, user });
    
    // should update user state in Redux
    dispatch({
      type: 'user/SET_STATE',
      payload: {
        loading: false,
        authorized: isAuthenticated,
        // id: user.name,
        // name: user.name,
        // role: user.role,
        // email: user.email,
        // avatar: user.avatar,
      },
    })
};
```

{% hint style="info" %}
Any sagas from `src/redux/user/sagas.js` should not be used for auth0 provider. It used for Firebase or JWT auth providers.
{% endhint %}



