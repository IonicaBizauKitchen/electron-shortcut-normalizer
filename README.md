# electron-shortcut-normalizer

Normalize [electron keyboard shortcuts](https://github.com/atom/electron/blob/master/docs/api/accelerator.md#readme) so they work on different operating systems.

![shortcut](https://cloud.githubusercontent.com/assets/2289/14234573/0f3e0c52-f99b-11e5-9e59-804400e752d6.png)

- [x] is a function
- [x] makes your electron keyboard shortcuts platform-agnostic
- [x] can make them platform-specific too
- [x] converts <kbd>Option</kbd> to <kbd>Alt</kbd>, because <kbd>Alt</kbd> exists on all platforms
- [x] converts <kbd>CmdOrCtrl</kbd> modifier to <kbd>CommandOrControl</kbd>
- [x] supports mixed-case modifiers like <kbd>MediaPreviousTrack</kbd>
- [x] capitalizes first letter of each modifier
- [x] removes whitespace from shortcuts
- [x] converts hyphens (-) to plusses (+)

## Installation

```sh
npm install electron-shortcut-normalizer --save
```

## Usage

```js
const normalize = require("electron-shortcut-normalizer")

normalize('Ctrl+A')
// => 'CommandOrControl+A'

normalize('CommandOrControl+Z', process.platform)
// => 'Command+Z' on Mac OS X
// => 'Control+Z' on Windows and Linux

normalize('CmdOrCtrl+a', 'darwin')
// => 'Command+A'

normalize('CmdOrCtrl+a', 'win32')
// => 'Control+A'

// `Option` is unique to Mac OS X, so it's normalized to `Alt`:
normalize('Option+Up')
// => 'Alt+Up'
```

For more specific usage information, see [test.js](/test.js)

## See Also

- Electron [Accelerator](https://github.com/atom/electron/blob/master/docs/api/accelerator.md) docs
- Electron [Menu](https://github.com/atom/electron/blob/master/docs/api/menu.md) docs
- Electron [globalShortcut](https://github.com/atom/electron/blob/master/docs/api/global-shortcut.md) docs
- Node.js [process.platform](https://nodejs.org/api/process.html#process_process_platform) docs
- [electron-localshortcut](https://github.com/parro-it/electron-localshortcut), a module to register/unregister a keyboard shortcut locally to a BrowserWindow instance, without using a Menu.

## Tests

```sh
npm install
npm test
```

## Dependencies

None

## Dev Dependencies

- [tape](https://github.com/substack/tape): tap-producing test harness for node and browsers
- [tap-spec](https://github.com/scottcorgan/tap-spec): Formatted TAP output like Mocha&#39;s spec reporter


## License

MIT

_Generated by [package-json-to-readme](https://github.com/zeke/package-json-to-readme)_
