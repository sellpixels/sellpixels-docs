# App Configuration

## Angular App Configuration Reference

* [https://angular.io/guide/workspace-config](https://angular.io/guide/workspace-config)

{% code title="angular.json" %}
```javascript
{
  "projects": {
    "templateName": {
      "architect": {
        "build": {
          "assets": [
            ... // assets configuration
          ],
          "styles": [
            ... // add styles here
          ],
          "scripts": [
            ... // third party js plugins
          ]
        }
      }
    }
  }
}
```
{% endcode %}

