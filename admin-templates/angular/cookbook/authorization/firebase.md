# Firebase

Our templates uses `firebase` service for default app authorization.

### Configuring

Replace `firebase` configuration with yours in `src/services/firebase/index.ts`

{% code title="src/services/firebase/index.ts" %}
```javascript
export const firebaseConfig = {
  apiKey: 'AIzaSyBJVhr2WZshEGR7egcxoygQIphKOkKVIYQ',
  authDomain: 'sellpixels-7d5d4.firebaseapp.com',
  databaseURL: 'https://sellpixels-7d5d4.firebaseio.com',
  projectId: 'sellpixels-7d5d4',
  storageBucket: 'cleanui-72a42.appspot.com',
  messagingSenderId: '338219933237',
}
```
{% endcode %}

### Inject service to app

{% code title="src/app/app.module.ts" %}
```javascript
import { AngularFireModule } from '@angular/fire'
import { AngularFireAuthModule } from '@angular/fire/auth'
import { AngularFirestoreModule, SETTINGS } from '@angular/fire/firestore'
import { firebaseConfig, firebaseAuthService } from './services/firebase'

@NgModule({
  declarations: [AppComponent],
  imports: [
    ...,
    AngularFireModule.initializeApp(firebaseConfig),
    AngularFireAuthModule,
    AngularFirestoreModule,
  ],
  providers: [
    ...,
    firebaseAuthService,
    { provide: SETTINGS, useValue: {} },
  ]
})
```
{% endcode %}

### Authorization Methods

Check `src/services/firebase/index.js`  file for next functions:

{% code title="src/app/services/firebase/index.ts" %}
```javascript
export class firebaseAuthService {
  constructor(
    ...
  ) {
    ...
    this.firebaseAuth.authState.subscribe(user => {
      // save user state to ngrx store on firebase user state udpate
      ...
    }
  }
  
  async login(email: string, password: string) { ... }
  async register(email: string, password: string, name: string) { ... }
  async logout() { ... }
```
{% endcode %}

 For switching app to authorized state you should set `authorized` prop to `true`

{% code title="src/app/store/user/reducers.ts" %}
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

`src/app/store/user/effects.ts` file handles app authorization process. The app should get user data from firebase API and save user state to store.

{% code title="src/redux/user/.js" %}
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

