# Localization

Localization component  `src/localization.js` bootstrapped in  `src/index.js` and handles `antd` and `react-intl` packages.

Additional info: [https://github.com/yahoo/react-intl](https://github.com/yahoo/react-intl) and [https://ant.design/components/locale-provider/](https://ant.design/components/locale-provider/)

## How To

Setting up the framework to a completed, translated web app in easy 3 steps:

#### Step 1: Adding translate config file

Add translate file to locales folder `src/locales/fr-FR.js` with some locale settings

{% code title="src/locales/fr-FR.js" %}
```javascript
import localeAntd from 'antd/es/locale/fr_FR'

const messages = {
  'topBar.issuesHistory': 'Histoire des problèmes',
  ...
}

export default {
  locale: 'fr-FR',
  localeAntd,
  messages,
}
```
{% endcode %}

#### Step 2: Register configuration

Register added previously configuration in `src/localization.js`

{% code title="src/localization.js" %}
```javascript
import french from 'locales/fr-FR'

addLocaleData(french.localeData)

const locales = {
  'fr-FR': french,
  ...
}
```
{% endcode %}

#### Step 3: Add formatter to any component

```javascript
import { FormattedMessage } from 'react-intl'

<Button type="danger">
  <FormattedMessage id="topBar.issuesHistory" />
</Button>
```

or use as string: 

```javascript
import { injectIntl } from 'react-intl'

const FavPages = ({ intl: { formatMessage } }) => {
  return (
    <Input
      placeholder={formatMessage({ id: 'topBar.issuesHistory' })}
      value={searchText}
      onChange={changeSearchText}
      allowClear
    />
  )
}

export default injectIntl(FavPages)
```

#### How to dynamically change the language?

Just dispatch `settings/CHANGE_SETTING` action for changing `locale` setting:

```javascript
dispatch({
  type: 'settings/CHANGE_SETTING',
  payload: {
    setting: 'locale',
    value: 'fr-FR',
  },
})
```

