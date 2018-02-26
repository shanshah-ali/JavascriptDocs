### React development tools
React Development Tools is a Chrome plugin that provides handy ways to inspect and debug your React components.
React Developer Tools lets you inspect the React component hierarchy, including component props and state. It exists both as a browser extension (for Chrome and Firefox), and as a standalone app (works with other environments including Safari, IE, and React Native).

##### Installation
The official extensions represent the current stable release.
<https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi>(Chrome extension)
<https://addons.mozilla.org/en-GB/firefox/addon/react-devtools/>(firefox extesnion)

##### Usage
The extension icon will light up on the websites using React
On such websites, you will see a tab called React in Developer Tools:

##### Tree View
- Arrow keys or hjkl for navigation
- Right click a component to show in elements pane, scroll into view, show source, etc.
- Differently-colored collapser means the component has state/context

##### Side pane
- Right-click to store as global variable
- Updates are highlighted

##### Search Bar
- Usse the search bar to find components by name


**You may include the transform-react-jsx-source Babel plugin to see the source file and line number of React elements. This information appears in the bottom of the right panel when available.**