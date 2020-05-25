# Themes & Font

## Font

Our templates use fonts loaded from Google Fonts. You can change it in the index.html file.

```markup
<link href="//fonts.googleapis.com/css?family=Mukta:400,700,800&display=swap" rel="stylesheet">
```

## Theme Primary Color

We used CSS variables to set primary color & font family globally. This variable can be set in the `components/kit/core/css/core.scss` file.

```css
:root {
  --kit-color-primary: #4b7cf3;
  --kit-font-family: 'Mukta', sans-serif;
}
```

Some third-party plugins also used this variable. See the `components/kit/vendors` folder.

#### Dynamically change by Color Picker

On color change event in Color Picker component next code will be added to the end of the document, which will set `--kit-color-primary` variable to a new statement:

```markup
<style id="primaryColor">:root { --kit-color-primary: #f35847;}</style>
```

## Switching Light / Dark Theme

Basically switching light theme to dark theme will change `data-kit-theme` on html tag. 

* Light theme: `<html data-kit-theme="default">`
* Dark theme: `<html data-kit-theme="dark">`

All affected files have dark styles section in the end of file:

```css
// dark theme
[data-kit-theme='dark'] { ... }
```

You can use this approach to use dark components inside light \(pay attention to the order in which the styles are loaded!\):

```markup
<div data-kit-theme="default">
    <div class="card">...</div> // this card inherit light styles
    <div data-kit-theme="dark">
        <div class="card">...</div> // this card inherit dark styles
    </div>
</div>
```

## Ant Design Theming

Switching the Ant Design theme in a live application is more complex than just adding variables. To do this, we created a LESS plugin \(`components/kit/vendors/antd/themes/AntdThemeLoader.js`\).

To use LESS variables, the `addLessLoader` plugin was added to the application configuration, check the `config-overrides.js` file.

Ant Design styles loaded in `src/index.js` :

```javascript
import 'antd/lib/style/index.less' // antd core styles
import './components/kit/vendors/antd/themes/default.less' // default theme antd components
import './components/kit/vendors/antd/themes/dark.less' // dark theme antd components
```

