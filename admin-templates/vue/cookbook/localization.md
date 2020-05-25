# Localization

Localization component  `src/localization.vue` bootstrapped in  `src/main.js` and handles `antd` and `vue-i18n` packages.

## How To

Setting up the framework to a completed, translated web app in easy 3 steps:

#### Step 1: Adding translate config file

Add translate file to locales folder `src/locales/fr-FR.js` with some locale settings

{% code title="src/locales/fr-FR.js" %}
```javascript
import localeAntd from 'ant-design-vue/lib/locale-provider/fr_FR'

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

Register added previously configuration in `src/localization.vue`

{% code title="src/localization.vue" %}
```javascript
import french from 'locales/fr-FR'

addLocaleData(french.localeData)

const locales = {
  'fr-FR': french,
  ...
}

export const i18n = new VueI18n({
  locale: 'en-US', // default locale
  fallbackLocale: 'en-US', // locale if message not found
  messages: {
    'en-US': locales['en-US'].messages,
    'fr-FR': locales['fr-FR'].messages, // fr-FR locale was added
    'ru-RU': locales['ru-RU'].messages,
    'zh-CN': locales['zh-CN'].messages,
  },
})
```
{% endcode %}

#### Step 3: Add formatter to any component

```javascript
<span class="d-none d-xl-inline">{{ $t('topBar.projectManagement') }}</span>
```

or use as string: 

```javascript
<a-input
  :placeholder="$t('topBar.findPages')"
/>
```

#### How to dynamically change the language?

Just commit `CHANGE_SETTING` action for changing `locale` setting:

```javascript
this.$store.commit('CHANGE_SETTING', {
  setting: 'locale',
  value: 'fr-FR'
})
```

