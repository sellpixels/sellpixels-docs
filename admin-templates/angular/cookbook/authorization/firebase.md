# Firebase \(default\)

Our templates uses `firebase` service for default app authorization \(simplest variant\).

Check `src/app/services/firebase.auth.service.ts` file for next functions:

#### Injection

{% code title="src/app/services/firebase.auth.service.ts" %}
```javascript
async SignIn(email: string, password: string) { ... } // auth procedure
get getUser() { ... } // get current user
async SignOut() { ... } // logout user
```
{% endcode %}

#### Auth Method on Login Page

{% code title="src/app/pages/auth/login/login.component.ts" %}
```javascript
submitForm(): void {
  ...
  this.authService.SignIn(this.email.value, this.password.value)
}
```
{% endcode %}

