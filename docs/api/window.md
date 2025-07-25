---
title: Neutralino.window
toc_max_heading_level: 2
---

The `Neutralino.window` namespace contains methods related to the current native window instance.
This namespace's methods will work only for the [`window`](/docs/configuration/modes.md#window) mode.

## window.setTitle(title)
Sets the title of the native window.

### Parameters
- `title` String (optional): Title of the window. Clears the title, if the function was called without the parameter.

```js
await Neutralino.window.setTitle('New title');
```

## window.getTitle()
Returns the title of the native window.

### Return String (awaited):
The current title of the native window instance.

```js
let title = await Neutralino.window.getTitle();
console.log(`title = ${title}`);
```

## window.minimize()
Minimizes the native window.

```js
await Neutralino.window.minimize();
```

## window.unminimize()
Restores the native window from the minimized state.

```js
await Neutralino.window.unminimize();
```

## window.isMinimized()
Returns `true` if the native window is minimized.

### Return Boolean (awaited):
- `true` or `false` based on current minimized status.

```js
let status = await Neutralino.window.isMinimized();
```

## window.maximize()
Maximizes the native window.

```js
await Neutralino.window.maximize();
```

## window.unmaximize()
Restores the native window.

```js
await Neutralino.window.unmaximize();
```

## window.isMaximized()
Returns `true` if the native window is maximized.

### Return Boolean (awaited):
- `true` or `false` based on current maximized status.

```js
let status = await Neutralino.window.isMaximized();
```

## window.setFullScreen()
Enables the full screen mode.

```js
await Neutralino.window.setFullScreen();
```

## window.exitFullScreen()
Exits from the full screen mode.

```js
await Neutralino.window.exitFullScreen();
```

## window.isFullScreen()
Returns `true` if the native window is in the full screen mode.

### Return Boolean (awaited):
- `true` or `false` based on current full screen status.

```js
let status = await Neutralino.window.isFullScreen();
```

## window.show()
Shows the native window.

```js
await Neutralino.window.show();
```

## window.hide()
Hides the native window.

```js
await Neutralino.window.hide();
```

## window.isVisible()
Returns `true` if the native window is visible.

### Return Boolean (awaited):
- `true` or `false` based on current visibility status.

```js
let status = await Neutralino.window.isVisible();
```

## window.focus()
Focuses the native window.

```js
await Neutralino.window.focus();
```

## window.setAlwaysOnTop(onTop)
Activates or deactivates the always on top mode. 

### Parameters

- `onTop` Boolean (optional): Says whether the on top mode should be activated or not. The default value
is `true`.

```js
await Neutralino.window.setAlwaysOnTop(true); // or setAlwaysOnTop();
await Neutralino.window.setAlwaysOnTop(false);
```

## window.move(x, y)
Moves the native window into given coordinates. Neutralinojs's cross-platform coordinate system starts from top-left corner of the screen.
In other words, `x=0,y=0` point refers to the top-left corner of the device's main screen.

### Parameters
- `x` Number: An integer value for the horizontal position.
- `y` Number: An integer value for the vertical position.

```js
await Neutralino.window.move(200, 400);
```

## window.center()
Centers the native app window within the current display.

```js
await Neutralino.window.center();
```

## window.setIcon(icon)
Sets an icon for the native window or Dock. 

### Parameters

- `icon` String: Path of the icon. A `200x200` PNG image file works fine on all supported operating systems.

```js
const icon = '/resources/icons/appIcon.png';
await Neutralino.window.setIcon(icon);
```

## window.setDraggableRegion(domId, options)
Converts a given DOM element to a draggable region. The user will be able to drag the native window by dragging the given DOM element. This feature is suitable to make custom window bars along with the [borderless mode](../configuration/neutralino.config.json#modeswindowborderless-boolean).

### Parameters

- `domId` String | HTMLElement: A DOM element identifier.
- `options` DraggableRegionOptions (optional): Customize the behavior of the draggable region.

### DraggableRegionOptions

- `exclusions` String[] | HTMLElement[] (optional): DOM element identifiers that should be excluded from the draggable region surface, i.e., window control buttons 


### Return Object (awaited):
- `exclusions` DraggableRegionExclusions: Add or remove draggable region exclusions.

### DraggableRegionExclusions

- `add(...domIds: String | HTMLElement)`: Add new elements to exclusions. 
- `remove(...domIds: String | HTMLElement)`: Remove elements from exclusions. 
- `removeAll()`: Clear exclusions. 

```js
await Neutralino.window.setDraggableRegion('myCustomTitleBar');

await Neutralino.window.setDraggableRegion('myCustomTitleBar', {
    exclusions: ['closeButton', 'helpButton']
});

const d = await Neutralino.window.setDraggableRegion('myCustomTitleBar', {
    exclusions: ['windowControls', 'tags']
});

d.exclusions.add('notifications');
d.exclusions.remove('tags');
```

## window.unsetDraggableRegion(domId)
Converts a draggable region to a normal DOM elements by removing drag event handlers.

### Parameters

- `domId` String | HTMLElement: A DOM element identifier.

```js
await Neutralino.window.unsetDraggableRegion('myCustomTitleBar');
```

## window.setSize(Options)
This method sets the size of the window.

### Options

- `width` Number (optional): Window width in pixels.
- `height` Number (optional): Window height in pixels.
- `minWidth` Number (optional): Minimum width of the window in pixels.
- `minHeight` Number (optional): Minimum height of the window in pixels.
- `maxWidth` Number (optional): Maximum width of the window in pixels.
- `maxHeight` Number (optional): Maximum height of the window in pixels.
- `resizable` Boolean (optional): A boolean value to make the window resizable or fixed.

This method always expects width and height couples.
For example, if you are setting `minWidth`, you should set `minHeight` too.

```js
await Neutralino.window.setSize({
    width: 500,
    height: 200,
    maxWidth: 600,
    maxHeight: 400
});

await Neutralino.window.setSize({
    resizable: false
});
```

## window.getSize()
Returns window size information.

### Return Boolean (awaited):

- `width` Number: Window width in pixels.
- `height` Number: Window height in pixels.
- `minWidth` Number Minimum width of the window in pixels.
- `minHeight` Number: Minimum height of the window in pixels.
- `maxWidth` Number: Maximum width of the window in pixels.
- `maxHeight` Number: Maximum height of the window in pixels.
- `resizable` Boolean: Says whether the window resizable or fixed.


```js
let sizeInfo = await Neutralino.window.getSize();

console.log(sizeInfo);
```

## window.getPosition()
Returns window position coordinates.

### Return Boolean (awaited):

- `x` Number: Horizontal coordinate of the left edge of the window.
- `y` Number: Vertical coordinate of the top edge of the window.


```js
let position = await Neutralino.window.getPosition();

console.log(position);
```

## window.snapshot(path)
Takes a snapshop of the current window client area (without the window frame) and stores as a PNG image file. 

### Parameters

- `path` String: Path where the snapshot PNG file should be stored.

```js
await Neutralino.window.snapshot(NL_PATH + '/images/window.png');
```

## window.create(url, WindowOptions)
Creates a native window. You can use this method to create new window for your multi-window Neutralinojs app.
Neutralinojs spawns a new process for each native window. Therefore, the new window works as an isolated app once the window is created.

However, you can build communication streams between windows with the [storage API](./storage.md).

### Parameters

- `url` String: URL to be loaded. Eg: `/resources/aboutWindow.html`. Supports loading both local and remote app resources. Local resource paths need to begin with `/`.
- `options` (optional): an instance of `WindowOptions` type.

### WindowOptions

- `title` String: Window title.
- `icon` String: Window icon path.
- `fullScreen` Boolean: Sets full screen mode.
- `alwaysOnTop` Boolean: Activates the top-most mode.
- `enableInspector` Boolean: Activates developer tools and opens the web inspector window.
- `borderless` Boolean: Makes the window borderless.
- `maximize` Boolean: Launches the window maximized.
- `hidden` Boolean: Hides the window.
- `maximizable` Boolean: Makes the window maximizable or not.
- `exitProcessOnClose` Boolean: Exits the application process when the user clicks the window's close button.
- `width` Number: Window width.
- `height` Number: Window height.
- `x` Number: Window `x` position.
- `y` Number: Window `y` position.
- `minWidth` Number: Minimum width of the window.
- `minHeight` Number: Minimum height of the window.
- `maxWidth` Number: Maximum width of the window.
- `maxHeight` Number: Maximum height of the window.
- `extendUserAgentWith` String: Extends the user agent string of the webview instance.
- `injectGlobals` Boolean: Injects global variables directly to the webview instance.
- `injectClientLibrary` Boolean: Injects the client library source directly to the webview instance.
- `injectScript` Boolean: A preload JavaScript source file that executes before web app resources.
- `processArgs` String: Additional command-line arguments for the new window process. Check all supported
internal command-line arguments from [here](../cli/internal-cli-arguments.md).

### Return Object (awaited):
- `pid` Number: Process identifier.
- `stdOut` String: Standard output. This value is always empty since the new window process starts asynchronously.
- `stdErr` String: Standard error. This value is always empty since the new window process starts asynchronously.
- `exitCode` Number: Exit code of the process.

```js
await Neutralino.window.create('/resources/aboutWindow.html', {
    icon: '/resources/icons/aboutIcon.png',
    enableInspector: false,
    width: 500,
    height: 300,
    maximizable: false,
    exitProcessOnClose: true,
    processArgs: '--window-id=W_ABOUT'
});
```

## window.setMainMenu(menu)
Creates/updates the main window menu on GNU/Linux and Windows and application menu on macOS.

### Parameters
- `menu` WindowMenuItem[]: An array of `WindowMenuItem` objects.

#### WindowMenuItem

- `id` String (optional): A unique identifier for each menu item.
- `text` String: Label of the menu item. This field is a mandatory field. Use `-` (hyphen) character for a menu separator.
- `isDisabled` Boolean (optional): A boolean flag to disable/enable a specific menu item.
- `isChecked` Boolean (optional): A boolean flag to mark a specific menu item as selected.
- `menuItems` WindowMenuItem[]: Submenu for the current menu item.
- `shortcut` String (optional): Sets a key accelerator on macOS (e.g., `c` for `Command + C`) and only displays the shortcut on GNU/Linux and Windows, e.g., `Ctrl + C`.
- `action` String (optional): Pre-defined window action for macOS, i.e., `cut:`, `copy:`, `paste:`, etc.  

```js
const menu = [
  {id: 'file', text: 'File',
    menuItems: [
    {id: 'open', text: 'Open'},
    {text: '-'},
    {id: 'quit', text: 'Quit'},
  ]},
  {id: 'edit', text: 'Edit',
    menuItems: [
    {id: 'cut', text: 'Cut'},
    {id: 'copy', text: 'Copy'},
    {id: 'paste', text: 'Paste'},
  ]}
];

await Neutralino.window.setMainMenu(menu);
await Neutralino.on('mainMenuItemClicked', (evt) => {
    console.log('Menu item:', evt.detail);
}); 
```

## window.print()
Displays the native print dialog for the current page. Developers can use this function instead of the built-in web `window.print()` function as a cross-platform solution
since macOS webview doesn't pre-implement `window.print()`.

```js
await Neutralino.window.print();
```

## window.beginDrag()
Starts dragging the native window if the left mouse button is pressed. The draggable region API in the Neutralinojs client library uses this function internally to move
the window with the pointer events web API. 

```js
await Neutralino.window.beginDrag();
```
