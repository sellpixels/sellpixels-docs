# App Configuration

## Create React App Configuration Reference

* [https://facebook.github.io/create-react-app/docs/getting-started](https://facebook.github.io/create-react-app/docs/getting-started)
* Config overrides: [https://github.com/timarney/react-app-rewired](https://github.com/timarney/react-app-rewired) and [https://github.com/arackaf/customize-cra](https://github.com/arackaf/customize-cra)

Create-react-app can be configured in `"/config-overrides.js"`  with react-app-rewired extension. 

{% code title="config-overrides.js" %}
```javascript
// Overriding CreateReactApp settings, ref: https://github.com/arackaf/customize-cra
const {
  override,
  // fixBabelImports,
  addLessLoader,
  useEslintRc,
  addDecoratorsLegacy,
  useBabelRc,
} = require('customize-cra')

// eslint config
const eslintConfig = require('./.eslintrc.js');
const useEslintConfig = configRules => config => {
  // load .eslintrc.js config
}

module.exports = override(
  addDecoratorsLegacy(),
  useEslintRc(),
  addLessLoader({
    javascriptEnabled: true,
  }),
  useEslintConfig(eslintConfig),
  useBabelRc(),
)

```
{% endcode %}

