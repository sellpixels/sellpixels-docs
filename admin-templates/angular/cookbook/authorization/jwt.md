# JWT

JWT auth uses `HttpClient` for handling auth process. Pass authToken to requests in `src/app/services/jwt/index.ts`

### Authorization Methods

Check `src/app/services/jwt/index.ts`  file for next functions:

{% code title="src/app/services/jwt/index.ts" %}
```javascript
@Injectable()
export class jwtAuthService {
  login(email: string, password: string): Observable<any> {
    return this.http.post('/api/auth/login', { email, password })
  }

  register(email: string, password: string, name: string): Observable<any> {
    return this.http.post('/api/auth/register', { email, password, name })
  }

  currentAccount(): Observable<any> {
    const accessToken = store.get('accessToken')
    const params = accessToken
      ? {
          headers: {
            Authorization: `Bearer ${accessToken}`,
            AccessToken: accessToken,
          },
        }
      : {}

    return this.http.get('/api/auth/account', params)
  }

  logout(): Observable<any> {
    return this.http.get('/api/auth/logout')
  }
}
```
{% endcode %}

 For switching app to authorized state you should set `authorized` prop to `true`

{% code title="src/app/store/user/reducers.ts" %}
```javascript
export const initialState: object = {
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

`src/app/store/user/effects.ts` file handles app authorization process. The app should get user data from API and save user state to store.

{% code title="src/app/store/user/effects.ts" %}
```javascript
import * as firebase from 'services/firebase'

@Injectable()
export class UserEffects implements OnInitEffects {

  // fetch user data on app init
  ngrxOnInitEffects(): Action {
    return { type: UserActions.LOAD_CURRENT_ACCOUNT }
  }

  @Effect()
  login: Observable<any> = this.actions.pipe( ... )
  
  @Effect()
  register: Observable<any> = this.actions.pipe( ... )
    
  @Effect()
  loadCurrentAccount: Observable<any> = this.actions.pipe( ... )
  
  @Effect()
  logout: Observable<any> = this.actions.pipe( ... )
}
```
{% endcode %}

### Dispatching Auth Methods

{% code title="src/app/components/{templateName}/system/Auth/login/login.component.ts" %}
```javascript
submitForm(): void {
  const payload = {
    email: this.email.value,
    password: this.password.value,
  }
  this.store.dispatch(new UserActions.Login(payload))
}
```
{% endcode %}

{% code title="src/app/components/{templateName}/system/Auth/login/register.component.ts" %}
```javascript
submitForm(): void {
  const payload = {
    email: this.email.value,
    password: this.password.value,
    name: this.name.value,
  }
  this.store.dispatch(new UserActions.Register(payload))
}
```
{% endcode %}

{% code title="src/app/components/{templateName}/layout/Topbar/UserMenu/user-menu.component.ts" %}
```javascript
logout() {
  this.store.dispatch(new UserActions.Logout())
}
```
{% endcode %}

