# Layout Settings

All layout settings handled in Redux store, see `src/app/store/settings/reducers.ts`  file. Edit this to change default look of the app.

{% code title="src/app/store/settings/reducers.ts" %}
```javascript
export const initialState: object = {
  // default settings, if not exist in localStorage
  ...STORED_SETTINGS({
    logo: '{templateName}',
    locale: 'en-US',
    isSidebarOpen: false,
    isSupportChatOpen: false,
    isMobileView: false,
    isMobileMenuOpen: false,
    isMenuCollapsed: false,
    menuLayoutType: 'left', // left, top, nomenu
    routerAnimation: 'slideFadeinUp', // none, slideFadeinUp, slideFadeinRight, Fadein, zoomFadein
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
this.store.dispatch(
  new SettingsActions.SetStateAction({
    primaryColor: '#ff0000',
  }),
)

this.store.dispatch(
  new SettingsActions.SetStateAction({
    menuColor: 'dark',
  }),
)
```

