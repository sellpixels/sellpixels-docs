# User Roles

User role affects on `<ACL />`  and `<Menu />` components. Read Basic ACL and Menu Configuration section for detailed information.

{% code title="src/redux/user/reducers.js" %}
```javascript
const initialState = {
  id: '',
  name: '',
  role: '', // user role which should be set on user auth trigger
  email: '',
  avatar: '',
  authorized: false, // authorize user
  loading: false,
}
```
{% endcode %}



