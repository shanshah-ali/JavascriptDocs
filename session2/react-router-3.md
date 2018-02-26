#### Introduction
React Router is a package that allows us to
React Router provides component called *Route*.

#### Installation
We need to install react-router package before start using it. To install react-router:
```
-> open terminal and run $ npm install --save react-router

-> $ npm install --save react-router@package-version to install specific version.
```
###### Example:
```
-> $ npm install --save react-router@3.0.2
```
#### Usage

Now lets start using react-router package.

-> Create APP.jsx file in your project directory and add bellow code.

```
// App.jsx

import React, { Component} from 'react';
import { render } from 'react-dom';

class App extends Component {
  render () {
    return <div>Welcome to react router</div>
  }
}

export default App;
```

-> Create index.js file in your project directory and add bellow code.
```
// index.js

import { Router, Route, browserHistory } from 'react-router'

render((
  <Router history={browserHistory}>
    <Route path="/" component={App}/>
  </Router>
), document.getElementById('app'))
```
Above code will show 'Welcome to react router' in browser.

Now it is time to see what is going on in index.js file. Here we have imported
Router, Route and browserHistory from react-router package.

#### Router
Router is a component provided by react-router package. The main job of a <Router> component is to create a history object to keep track of
the location (URL). When the location changes because of a navigation action, the child component (in this case <App>) is re-rendered.

#### Route
The Route component is perhaps the most important component
in React Router to understand and learn to use well. Its most basic
responsibility is to render some UI when a location matches the
route’s path.

#### Histories
React Router is built with history. In a nutshell, a history knows how to listen to the browser's address bar for changes and parses the URL into a location object that the router can use to match routes and render the correct set of components.

There are three types of histories you'll come across most often, but note that anyone can build a custom history implementation for consumption with React Router.

* browserHistory
* hashHistory
* createMemoryHistory

###### browserHistory

Browser history is the recommended history for browser application with React Router. It uses the History API built into the browser to manipulate the URL, creating real URLs that look like example.com/some/path.
###### hashHistory

Hash history uses the hash (#) portion of the URL, creating routes that look like example.com/#/some/path.

###### createMemoryHistory

Memory history doesn't manipulate or read from the address bar. This is how we implement server rendering.
It's also useful for testing and other rendering environments (like React Native).

It's a bit different than the other two histories because you have to create one, it is this way to facilitate testing:
```
const history = createMemoryHistory(location)
```
#### Navigation
React Router provides a <Link> component to create links in our application.
Wherever our render a <Link>, an anchor tag will be rendered in your application’s HTML.

Now let us create few more components to implement navigation using react-router's <Link /> component.

```
// Home.jsx

import React from 'react';

const Home = () => {
  return (
    <h2>Home Page</h2>
  );
};

export default Home;
```

```
// Resources.jsx

import React from 'react';

const Resources = () => {
  return (
    <h2>Resources Page</h2>
  );
};

export default Resources;
```
```
// Benefits.jsx

import React from 'react';

const Benefits = () => {
  return (
    <h2>Benefits Page</h2>
  );
};

export default Benefits;
```

```
// HelpCenter.jsx

import React from 'react';

const HelpCenter = () => {
  return (
    <h2>Help Center</h2>
  );
};

export default HelpCenter;
```

Modify index.js as follows:

```
// index.js

import React, {Component} from 'react';
import { Router, Route, IndexRoute,  browserHistory } from 'react-router';

import App from './App';
import Home from './Home';
import Resources from './Resources';

ReactDOM.render(
  <Router history={browserHistory}>
    <Route path="/" component={Home} />
    <Route path="/resources" component={Resources} />
  </Router>, document.getElementById('app')
);
```

Now reload your browser window and enter 'resources' after '/', you will see Resources Page in browser window.

#### Nested Routes

React Router provides supports for routes nesting, routes can be nested inside another route.

Again modify App.jsx and index.js as follows:

```
// App.jsx

import React, { Component } from 'react';
import { Link } from 'react-router';

class App extends React.Component {
  render () {
    return (
      <div>
        <div style={{display: 'flex', justifyContent: 'center'}}>
          <Link to="/home" style={{padding: 10}}>
            Home
          </Link>
          <Link to="/resources" style={{padding: 10}}>
            My Resources
          </Link>
          <Link to="/benefits" style={{padding: 10}}>
            Benefits
          </Link>

          <Link to="/help-center" style={{padding: 10}}>
            Help Center
          </Link>
        </div>
        <div style={{padding: 40, textAlign: 'center'}}>
          // child component will be rendered here
          { this.props.children }
        </div>
      </div>);
  }
}
export default App;
```
```
// index.js

import React, {Component} from 'react';
import { Router, Route, IndexRoute,  browserHistory } from 'react-router';

import App from './src/App';
import Home from './src/Home';
import Resources from './src/Resources';
import Benefits from './src/Benefits';
import HelpCenter from './src/HelpCenter';

ReactDOM.render(
  <Router history={browserHistory}>
    <Route path="/" component={App}>
      <Route path="/home" component={Home} />
      <Route path="/resources" component={Resources} />
      <Route path="/benefits" component={Benefits} />
      <Route path="/help-center" component={HelpCenter} />
    </Route>
  </Router>, document.getElementById('app')
);
```
If you hit http://localhost:3000 in your browser window, you will only see navigation bar on top of the page.

#### Index routes

An <IndexRoute> allows you to provide a default "child" to a parent route when visitor is at the URL of the parent.

```
// index.js

import React, {Component} from 'react';
import { Router, Route, IndexRoute,  browserHistory } from 'react-router';

import App from './src/App';
import Home from './src/Home';
import Resources from './src/Resources';
import Benefits from './src/Benefits';
import HelpCenter from './src/HelpCenter';

ReactDOM.render(
  <Router history={browserHistory}>
    <Route path="/" component={App}>
      <IndexRoute component={Home} />
      <Route path="/home" component={Home} />
      <Route path="/resources" component={Resources} />
      <Route path="/benefits" component={Benefits} />
      <Route path="/help-center" component={HelpCenter} />
    </Route>
  </Router>, document.getElementById('app')
);
```
Now if you hit http://localhost:3000 in your browser window,
you will see navigation bar as well as Home Page bellow navigation bar.

#### Navigating Programatically
While most navigation happens with Link, we can programmatically navigate around an application in response to form submissions, button clicks, etc.

Let's modify our App.jsx as follows:

```
// App.jsx

import React, { Component } from 'react';
import LoginForm from './routes/login/LoginForm';
import { browserHistory } from 'react-router';

class App extends React.Component {

  handleNavigation = (componentPath) => {
    browserHistory.push(componentPath);
  };

  render () {
    return (
      <div>
        <div style={{display: 'flex', justifyContent: 'center'}}>
          <button onClick={() => {this.handleNavigation('/home')}} style={{padding: 10, margin: 5}}>
            Home
          </button>
          <button onClick={() => {this.handleNavigation('/resources')}} style={{padding: 10, margin: 5}}>
            My Resources
          </button>
          <button onClick={() => {this.handleNavigation('/benefits')}} style={{padding: 10, margin: 5}}>
            Benefits
          </button>
          <button onClick={() => {this.handleNavigation('/help-center')}} style={{padding: 10, margin: 5}}>
            Help Center
          </button>
        </div>
        <div style={{padding: 40, textAlign: 'center'}}>
          { this.props.children }
        </div>
      </div>);
  }
}
export default App;
```

All the links are changed as buttons and added a click 'handleNavigation' handler to all the buttons.

handleNavigation method takes path as an argument and passes this argument to push method of browserHistory.  

Read more here :https://github.com/reactjs/react-router-tutorial
