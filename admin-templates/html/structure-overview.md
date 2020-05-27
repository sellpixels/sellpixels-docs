# Structure Overview

## Structure Overview

#### Building Your App from Prebuilt Files

* Copy necessary html code to your app from `dist/versions/*`
* Add third-party plugin files to your app from `dist/vendors/*`
* Import styles to your app from `dist/components/**/*.css`
* Add necessary component js to your app from `dist/components/**/*.js`

#### Required styles

| Name | Entry Point |
| :--- | :--- |
| `kit/core` | `dist/components/kit/core/style.css` |
| `{templateName}/styles` | `dist/components/{templateName}/styles/style.css` |

## Layouts Management

{% page-ref page="cookbook/layout-configuration.md" %}

{% page-ref page="cookbook/layout-settings.md" %}

## Build From Sources Instruction

See Getting Started section to run development server

* Add or remove version files in `/src/versions`
* Add or remove pages in `/src/pages`
* Add your components in `/src/components/{anyfolder}`
* Import your components to pages `@@include('src/components/{anyfolder}/list.html')`
* Import you styles to `src/versions/head.html`
* Run `gulp` build task

Build task will make the build into `dist` folder. The compiler will go through the `src/pages` folder, wrap the internal files with each `src/versions` file, then `@@include` all components into the pages. 

## Files Tree

```text
├─ dist/                     .. prebuilt app files by gulp after "gulp" run
│  ├─ components/            .. component files
│  ├─ vendors/               .. vendors files
│  └─ versions/              .. versions files (layout variations)
├─ node_modules/             .. node.js modules installed after "npm install" run
├─ src/                      .. source files
│  ├─ components/            .. components files
│  ├─ pages/                 .. page files
│  ├─ vendors/               .. vendors files installed by bower after "bower install" run
│  └─ versions/              .. layout files (wrappers)
├─ *                         .. system npm, gulp, and git files
└─ README.md                 .. git readme file
```

