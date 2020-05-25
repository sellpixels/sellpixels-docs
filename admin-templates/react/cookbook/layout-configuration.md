# Layout Configuration

All routes loaded through the default layout component `src/layouts/index.js`, which handles layout rendering and this rendering depends on the current route / user status.

Template has three layouts:

* Main
* Auth \(for Login, Lockscreen, etc.. pages\)
* Public \(empty layout\)

If you need a new layout, just add another one to the `src/layouts folder`, import it into `src/layouts/index.js` and add logic when it needs to be rendered.

See `BootstrappedLayout()` and `getLayout()` functions in `src/layouts/index.js`:

{% code title="src/layouts/index.js" %}
```javascript
import PublicLayout from './Public'
import LoginLayout from './Login'
import MainLayout from './Main'


// map layoyts
const Layouts = {
  public: PublicLayout,
  login: LoginLayout,
  main: MainLayout,
}

...

// getting the layout depends on route
const getLayout = () => {
  if (pathname === '/') {
    return 'public'
  }
  if (/^\/auth(?=\/|$)/i.test(pathname)) {
    return 'auth'
  }
  return 'main'
}

// set container
const Container = Layouts[getLayout()]

// render correct layout
const BootstrappedLayout = () => {
  // show loader when user in check authorization process, not authorized yet and not on login pages
  if (isUserLoading && !isUserAuthorized && !isAuthLayout) {
    return null
  }
  // redirect to login page if current is not login page and user not authorized
  if (!isAuthLayout && !isUserAuthorized) {
    return <Redirect to="/auth/login" />
  }
  // in other case render previously set layout
  return <Container>{children}</Container>
}

return (
  <Fragment>
    <Helmet titleTemplate="{templateName} | %s" title="React Admin Template" />
    {BootstrappedLayout()}
  </Fragment>
)

...
```
{% endcode %}

