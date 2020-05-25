---
description: Clean UI HTML Admin Template layout structure overview
---

# Layout Configuration

{% hint style="info" %}
* Please check Layout Settings section for the information on the possible classes for layout transformation and theming
{% endhint %}

## Left Menu Configuration

Replace `{}` with the template prefix.  
{}\_\_layout--hasSider class is important for vertical menu configurations.

```markup
<!DOCTYPE html>
<html lang="en" data-kit-theme="default">
@@include('src/versions/head.html')

<body class="{}__layout--cardsShadow">
  <div class="initial__loading"></div>
  <div class="{}__layout {}__layout--hasSider">
    @@include('src/components/{templateName}/layout/support-chat/template.html')
    @@include('src/components/{templateName}/layout/sidebar/template.html')
    @@include('src/components/{templateName}/layout/menu-left/template.html')
    <div class="{}__layout">
      <div class="{}__layout__header">
        @@include('src/components/{templateName}/layout/topbar/template.html')
      </div>
      <div class="{}__layout__content">
        @@include('src/components/{templateName}/layout/breadcrumbs/template.html')
        <div class="{}__utils__content">
          <%= contents %>
        </div>
      </div>
      <div class="{}__layout__footer">
        @@include('src/components/{templateName}/layout/footer/template.html')
      </div>
    </div>
  </div>
</body>

</html>
```

## Top Menu Configuration

Replace `{}` with the template prefix.

```markup
<!DOCTYPE html>
<html lang="en" data-kit-theme="default">
@@include('src/versions/head.html')

<body class="{}__layout--cardsShadow">
  <div class="initial__loading"></div>
  <div class="{}__layout">
    @@include('src/components/{templateName}/layout/support-chat/template.html')
    @@include('src/components/{templateName}/layout/sidebar/template.html')
    @@include('src/components/{templateName}/layout/menu-top/template.html')
    <div class="{}__layout">
      <div class="{}__layout__header">
        @@include('src/components/{templateName}/layout/topbar/template.html')
      </div>
      <div class="{}__layout__content">
        @@include('src/components/{templateName}/layout/breadcrumbs/template.html')
        <div class="{}__utils__content">
          <%= contents %>
        </div>
      </div>
      <div class="{}__layout__footer">
        @@include('src/components/{templateName}/layout/footer/template.html')
      </div>
    </div>
  </div>
</body>

</html>
```

