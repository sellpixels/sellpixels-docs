# Basic ACL

`<ACL />` is authorization component with redirect and roles feature. Path: `src/components/{templateName}/system/ACL/index.js`

| Prop | Type | Default Value | Description |
| :--- | :--- | :--- | :--- |
| redirect | Bool \|\| String | false | Applying redirect if user role not authorize to view it |
| roles | Array | \[\] | Authorize next roles |

#### Examples

```javascript
// Redirect to "/404" (default value) if your role differs from "admin"
// in other case show content
<ACL roles={['admin']} redirect>
  // ...content
</ACL>
```

```javascript
// Redirect to "/dashboard/beta" if your role differs from "admin"
// in other case show content
<ACL roles={['admin']} redirect="/dashboard/beta">
  // ...content
</ACL>
```

```javascript
// Show content if your role is "admin" or "user"
<ACL roles={['admin', 'user']}>
  // ...content
</ACL>
```



