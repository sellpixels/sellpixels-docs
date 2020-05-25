# Layout Settings

All layout settings handled in Redux store, see `src/store/settings/index.js`  file. Edit this to change default look of the app.

{% code title="src/store/settings/index.js" %}
```javascript
export default {
  state: {
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
  },
  ...
}
```
{% endcode %}

### Dispatch Examples

```javascript
this.$store.commit('SET_PRIMARY_COLOR', {
  color: '#ff0000'
})

this.$store.commit('CHANGE_SETTING', {
  setting: 'menuColor',
  value: 'dark',
})
```

