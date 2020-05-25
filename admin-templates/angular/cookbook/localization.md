# Localization

Localization component  `src/localization.vue` bootstrapped in  `src/main.js` and handles `antd` and `vue-i18n` packages.

## How To

Setting up the framework to a completed, translated web app in easy 3 steps:

#### Step 1: Adding translate config file

Add translate file to locales folder `src/app/locales/fr-FR.js` with some locale settings

{% code title="src/app/locales/fr-FR.js" %}
```javascript
export default {
  'topBar.issuesHistory': 'Histoire des problèmes',
  'topBar.projectManagement': 'Gestion de projet',
  'topBar.typeToSearch': 'Chercher...',
  'topBar.findPages': 'Trouver des pages...',
  'topBar.actions': 'Actes',
  'topBar.status': 'Statut',
  'topBar.profileMenu.hello': 'Bonjour',
  'topBar.profileMenu.billingPlan': 'Plan de facturation',
  'topBar.profileMenu.role': 'Rôle',
  'topBar.profileMenu.email': 'Email',
  'topBar.profileMenu.phone': 'Téléphone',
  'topBar.profileMenu.editProfile': 'Editer le profil',
  'topBar.profileMenu.logout': 'Connectez - Out',
}

```
{% endcode %}

#### Step 2: Register configuration

Register added previously configuration in `src/app/app.component.ts`

{% code title="src/app/app.component.ts" %}
```javascript
import french from './locales/fr-FR'

const locales = {
  ...,
  'fr-FR': french,
}
```
{% endcode %}

#### Step 3: Add formatter to any component

```javascript
<span class="d-none d-xl-inline">{{ 'topBar.findPages' | translate }}</span>
```

or use as string: 

```javascript
<input placeholder="{{ 'topBar.findPages' | translate }}" />
```

#### How to dynamically change the language?

Just commit `CHANGE_SETTING` action for changing `locale` setting:

```javascript
this.store.dispatch(
  new SettingsActions.SetStateAction({
    locale,
  }),
)
```

