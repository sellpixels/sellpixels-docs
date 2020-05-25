# App Configuration

## Vue App Configuration Reference

* [https://cli.vuejs.org/config/](https://cli.vuejs.org/config/)

{% code title="vue.config.js" %}
```javascript
module.exports = {
  pwa: {
    iconPaths: {
      favicon32: './favicon.png',
      favicon16: './favicon.png',
      appleTouchIcon: './favicon.png',
      maskIcon: './favicon.png',
      msTileImage: './favicon.png',
    },
  },
  css: {
    loaderOptions: {
      less: {
        javascriptEnabled: true, // less loader was added for ant design customizations
      },
    },
  },
}

```
{% endcode %}

