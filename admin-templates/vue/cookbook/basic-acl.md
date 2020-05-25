# Basic ACL

`<{templatePrefix}-acl />` is authorization component with redirect and roles feature. Path: `src/components/{templateName}/system/ACL/index.vue`

| Prop | Type | Default Value | Description |
| :--- | :--- | :--- | :--- |
| redirect | Bool \|\| String  | false | Applying redirect if user role not authorize to view it |
| roles | Array | \[\] | Authorize next roles |

#### Examples

```javascript
// Redirect to "/404" (default value) if your role differs from "admin"
// in other case show content
<{templatePrefix}-acl :roles="['admin']" redirect>
  // ...content
</{templatePrefix}-acl>
```

```javascript
// Redirect to "/dashboard/beta" if your role differs from "admin"
// in other case show content
<{templatePrefix}-acl :roles="['admin']" redirect="/dashboard/beta">
  // ...content
</{templatePrefix}-acl>
```

```javascript
// Show content if your role is "admin" or "user"
<{templatePrefix}-acl :roles="['admin', 'user']">
  // ...content
</{templatePrefix}-acl>
```

