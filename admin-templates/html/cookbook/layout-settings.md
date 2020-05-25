---
description: Clean UI HTML Admin Template layout configuration overview
---

# Layout Settings

The template has some classes which are activated by adding certain classes to the `body` tag.  
Replace `{}` with the theme prefix.

| Class | Applies to | Used for |
| :--- | :--- | :--- |
| {}\_\_sidebar--toggled | `body` | Toggles Sidebar |
| {}\_\_menuLeft--toggled | `body` | Toggels Left Menu |
| {}\_\_menuLeft--mobileToggled | `body` | Toggels Left Menu \(Mobile Viewport\) |
| {}\_\_menuLeft--unfixed | `body` | Makes Left Menu unfixed |
| {}\_\_menuLeft--shadow | `body` | Adds shadow to Left Menu |
| {}\_\_menuLeft--gray  | `body` | Left Menu in gray colors |
| {}\_\_menuLeft--dark | `body` | Left Menu in dark colors |
| {}\_\_menuTop--gray | `body` | Top Menu in gray colors |
| {}\_\_menuTop--dark | `body` | Top Menu in dark colors |
| {}\_\_menuTop--mobileToggled | `body` | Toggels Top Menu \(Mobile Viewport\) |
| {}\_\_auth--gray | `body` | Auth pages gray background |
| {}\_\_auth--img | `body` | Auth pages with bg image |
| {}\_\_topbar--fixed | `body` | Fixed Topbar |
| {}\_\_topbar--gray | `body` | Gray Topbar |
| {}\_\_layout--contentMaxWidth | `body` | Adds max-width to content area |
| {}\_\_layout--appMaxWidth | `body` | Add max-width to app |
| {}\_\_layout--grayBackground | `body` | App gray background |
| {}\_\_layout--squaredBorders | `body` | Squared card borders |
| {}\_\_layout--borderless | `body` | Borderless cards |
| etc... |  | This list changes from theme to theme  |

### Example

This will configure the compact horizontal menu on top with the fixed width of content-area 

```markup
<body class="{}__layout--cardsShadow {}__layout--grayBackground {}__menuLeft--toggled">
```

