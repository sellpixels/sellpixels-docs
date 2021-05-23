# User Roles

User roles affects the `<ACL />`  and `<Menu />` components. Read the [basic-acl](Basic ACL) and [menu-configuration](Menu Configuration) sections for more details.

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



