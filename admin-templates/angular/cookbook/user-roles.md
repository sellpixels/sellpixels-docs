# User Roles

User role affects on `<ACL />`  and `<Menu />` components. Read Basic ACL and Menu Configuration section for detailed information.

Currently user role simply set to localStorgae onAuth :

{% code title="src/app/services/firebase.auth.service.ts" %}
```javascript
// TODO: Add User Model to NgRx Store
this.afAuth.authState.subscribe(user => {
  if (user) {
    const _user = JSON.parse(JSON.stringify(user))
    // TODO: modify this code for your needs
    localStorage.setItem(
      'user',
      JSON.stringify({
        ...
        role: 'admin',
      }),
    )
  } else {
    localStorage.setItem('user', null)
  }
})
```
{% endcode %}

