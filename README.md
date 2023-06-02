# Plugin development

It is possible to develop your own widget plugins with only minor app development skills.

## Plugin content

A plugin consists of two separate HTML documents. These files must also contain all CSS styles and JavaScript application code. In addition you have to include the title and icon of the header, while embedding the content of the icon SVG file. You can find samples in the following sample files.

### Widget HTML content

A sample widget HTML file can be found [here](widget-test.html). Noteworthy is that it contains a style tag with all the required CSS styling. It contains the default font Roboto from Google Fronts, which is referenced from the FONT_PATH. The FONT_PATH is resolved from the widget host, instead of loading it from Google servers. This is, among other reasons, due to data protection regulations.

The sample file also contains a header section, which is comprised of a title text and an icon. The icon is directly embedded into the svg-tag.

The widget HTML sample also contains two examples of how to use the window.gugg object to access functions, which interact with the widget host. More information can be found in the [Widget host API](#widget-host-api).

### Detail HTML content

A sample detail HTML file can be found [here](widget-test-detail.html). Like the widget HTML file, it embeds all the CSS styles and JavaScript application code. It also makes use of the default font Roboto.

The file does not need to contain any type of document header. The header is fixed to the widget name, which can be defined, when submitting the widget. You can pass data from the widget to the detail HTML document. More information can be found in the [Widget host API](#widget-host-api).

## Widget host API

| Feature                                     | Type          | Description                                                      | Accessible         |
| ------------------------------------------- | ------------- | ---------------------------------------------------------------- | ------------------ |
| [window.gugg.alert](#windowguggalert)       | Function      | Allows to show alert messages to the user.                       | Only widget page.  |
| [window.gugg.toDetail](#windowguggtodetail) | Function      | Allows to navigate to the corresponding details page.            | Only widget page.  |
| [window.gugg.state](#windowguggstate)       | Object        | Allows access to the state after a call to window.gugg.toDetail. | Only details page. |

### window.gugg.alert

This function allows to show short messages to the user. See [this sample file](widget-test.html) for reference.

```javascript
  window.gugg.alert({title: 'Lorem ipsum', message: 'Dolor sit amet.'});
```

| Parameter | Description                      |
| --------- | -------------------------------- |
| title     | The title to show in the popup   |
| message   | The message to show in the popup |

### window.gugg.toDetail

This function allows to navigate to the details page of the same widget. See [this sample file](widget-test.html) for reference.

```javascript
  window.gugg.toDetail({ info: 'Lorem ipsum' });
```

The object, that you pass to the function will be passed to the details page application code.

### window.gugg.state

This object contains the state object, that was passed to the toDetail function. See [this sample file](widget-test-detail.html) for reference.