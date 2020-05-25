# Layout Settings

All layout settings handled in Redux store, see `src/redux/settings/reducers.js`  file. Edit this to change default look of the app.

{% code title="src/redux/settings/reducers.js" %}
```javascript
const initialState = {
  ...STORED_SETTINGS({
    logo: '{templateName}',
    locale: 'en-US',
    isSidebarOpen: false,
    isSupportChatOpen: false,
    isMobileView: false,
    isMobileMenuOpen: false,
    isMenuCollapsed: false,
    menuLayoutType: 'left', // left, top, nomenu
    routerAnimation: 'slide-fadein-up', // none, slide-fadein-up, slide-fadein-right, fadein, zoom-fadein
    menuColor: 'white', // white, dark, gray
    theme: 'default', // default, dark
    authPagesColor: 'white', // white, gray, image
    primaryColor: '#4b7cf3',
    leftMenuWidth: 256,
    isMenuUnfixed: false,
    isMenuShadow: false,
    isTopbarFixed: false,
    isGrayTopbar: false,
    isContentMaxWidth: false,
    isAppMaxWidth: false,
    isGrayBackground: false,
    isCardShadow: true,
    isSquaredBorders: false,
    isBorderless: false,
  }),
}
```
{% endcode %}

### Dispatch Examples

```javascript
dispatch({
  type: 'settings/SET_PRIMARY_COLOR',
  payload: {
    color: '#ff0000',
  },
})

dispatch({
  type: 'settings/CHANGE_SETTING',
  payload: {
    setting: 'menuColor',
    value: 'dark',
  },
})
```

