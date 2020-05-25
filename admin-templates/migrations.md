---
description: Guides for major version updates
---

# Migrations

## \[25 May 2020\] Update to KIT v2 codebase 

#### Affected templates:

| Name | Versions | From | To |
| :--- | :--- | :--- | :--- |
| Clean UI KIT | react, vue, angular, html | 1.x | 2.x |
| Clean UI Admin Template | react, vue, angular, html | 2.x | 3.x |
| Air UI Admin Template | react, vue, angular, html | 1.x | 2.x |

#### Update Information:

{% tabs %}
{% tab title="React" %}
As this is major change it breaks some components in the app.  
Take a look into:

* **config-overrides.js**: Added `.eslintrc.js` loader;
* **kit-base**: All Sellpixels templates will now work on a universal architecture using KIT as a base. The components of the template have been moved to a separate folder. This will prevent problems with widgets and applications update in future releases;
* **antd**: Old loader removed from `config-overrides.js`, now theme variables applies direct in less files with `apply()` function, check `kit/vendors/antd/themes/dark.less`. Antd styles now imported in `src/index.js`
* **themes:** Default and dark theme styles applied by ****`data-kit-theme=""` attribute on html tag
* **mixins.scss**: All components now import the shared `src/components/mixins.scss` file
* **deps**: Updated to latest versions
* **redesign**: Layout components was redesigned a little
{% endtab %}

{% tab title="Vue" %}
As this is major change it breaks some components in the app.  
Take a look into:

* **kit-base**: All Sellpixels templates will now work on a universal architecture using KIT as a base. The components of the template have been moved to a separate folder. This will prevent problems with widgets and applications update in future releases;
* **antd**: Old loader removed from `babel.config.js`, now theme variables applies direct in less files with `apply()` function, check `kit/vendors/antd/themes/dark.less`. Antd styles now imported in `src/index.js`
* **themes:** Default and dark theme styles applied by ****`data-kit-theme=""` attribute on html tag
* **mixins.scss**: All components now import the shared `src/components/mixins.scss` file
* **deps**: Updated to latest versions
* **redesign**: Layout components was redesigned a little
{% endtab %}

{% tab title="Angular" %}
As this is major change it breaks some components in the app.  
Take a look into:

* **ng9:** Updated to v9, reference [https://angular.io/guide/updating-to-version-9](https://angular.io/guide/updating-to-version-9)
* **kit-base**: All Sellpixels templates will now work on a universal architecture using KIT as a base. The components of the template have been moved to a separate folder. This will prevent problems with widgets and applications update in future releases;
* **antd**: Old loader removed from `babel.config.js`, now theme variables applies direct in less files with `apply()` function, check `kit/vendors/antd/themes/dark.less`. Antd styles now imported in `src/index.js`
* **themes:** Default and dark theme styles applied by ****`data-kit-theme=""` attribute on html tag
* **mixins.scss**: All components now import the shared `src/components/mixins.scss` file
* **deps**: Updated to latest versions
* **redesign**: Layout components was redesigned a little
{% endtab %}

{% tab title="Html" %}
The Html version has no major changes in prebuilt files, only a dark theme & redesign related changes. In a few words, it is an old good html code. Just copy the right code from the distribution folder and replace yours.

* Some layout components was redesigned
* Added some Extra Apps \(GitHub Explore, Jira Dashboard, etc...\)
* `mixins.scss` variables additions
* New css naming convention - BEM \(block\_\_element--modifier\)
* `gulpfile.js` completely refactored to v4.x
* `rigger` plugin replaced with `gulp-file-include`
* Dependencies update, see `bower.json`
{% endtab %}
{% endtabs %}



