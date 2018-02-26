# [Redux](https://redux.js.org/)

### What is Redux? 
Redux is a predictable state container for JavaScript apps. 
### What does it mean? 
It means that you can describe your application as a plain javascript object. This approach provides reasonable and predictable ways of maintaining application state in one place and making tweaks to it. 
### Why should I use it?
It helps you write applications that behave consistently, run in different environments (client, server, and native), and are easy to test. On top of that, it provides a great developer experience, such as live code editing combined with a time traveling debugger.

## Concept

Redux describes the app in terms of plain javascript object. For example, the state of a todo app might look like this:

```
{
  todos: [
  {
    text: 'Eat food',
    completed: true
  }, 
  {
    text: 'Exercise',
    completed: false
  }
  ],
  visibilityFilter: 'SHOW_COMPLETED'
}
```

To change something in the state, an action needs to be dispatched. Below are a few examples:

```
{ type: 'ADD_TODO', text: 'Go to swimming pool' }
{ type: 'TOGGLE_TODO', index: 1 }
{ type: 'SET_VISIBILITY_FILTER', filter: 'SHOW_ALL' }
```

An action is a plain JavaScript object  that describes what happened. It will always have a `type`. For example the `type` for above actions are, 

```
ADD_TODO
TOGGLE_TODO
SET_VISIBILITY_FILTER
```

and it may or may not have a `payload`. A `payload` is nothing but the intended change for the application state.
In the above example the `payload` for the actions are ,

```
{ text: 'Go to swimming pool' }
{ index: 1 }
{ filter: 'SHOW_ALL' }
```

## Setup

To use redux with react install the following dependencies

1. redux
2. react-redux

### Installation

#### NPM

```
npm install --save redux
npm install --save react-redux
```

#### YARN
```
yarn add redux
yarn add react-redux
```
### Additional Dev Setup

To use `@connect` decorator provided by `react-redux` to connect to the store babel plugins are required to be added to `.babelrc`.

Alternately `mapStateToProps` can be used to connect to the store.

Add the following packages as dev dependencies:

1. babel-plugin-transform-class-properties
2. babel-plugin-transform-decorators-legacy

To install as dev dependency follow the steps below.

#### NPM

```
npm install --save-dev babel-plugin-transform-class-properties
npm install --save-dev babel-plugin-transform-decorators-legacy
```

#### YARN
```
yarn add --dev babel-plugin-transform-class-properties
yarn add --dev babel-plugin-transform-decorators-legacy
```

#### .babelrc

Add the following to `.babelrc`  in the plugins section.
*Note: `transform-decorators-legacy` should always precede `transform-class-properties`*

```
{
	"plugins": ["transform-decorators-legacy","transform-class-properties"]
}

```

## Store

A store holds the whole state tree of your application.
The only way to change the state inside it is to dispatch an action on it.

A store is not a class. It's just an object with a few methods on it.

### Store Methods
-  getState() 
-  dispatch(action) 
- subscribe(listener) 
- replaceReducer(nextReducer) 


#### getState()

Returns the current state tree of your application.
It is equal to the last value returned by the store's reducer.

##### ***Returns***: (any)
The current state tree of your application.

For instance,
```
const auth = getState();
```

Will return the last state by auth reducer.

####  dispatch(action)
Dispatches an action. This is the only way to trigger a state change.

The store's reducing function will be called with the current `getState()` result and the given `action` synchronously. Its return value will be considered the next state. It will be returned from `getState()`.

##### ***Arguments***: action (Object)

A plain object describing the change that makes sense for your application.

##### ***Returns***: The dispatched action 

##### Example
```
const action = { type: 'ADD_TODO', payload };

dispatch(action)
```

####  subscribe(listener) 

Adds a change listener. It will be called any time an action is dispatched, and some part of the state tree may potentially have changed.

##### ***Arguments***: listener (Function)

The callback to be invoked any time an action has been dispatched, and the state tree might have changed. 

##### ***Returns*** : (Function)

##### Example
A function that unsubscribes the change listener.

```
function select(state) {
  return state.some.deep.property
}
 
let currentValue
function handleChange() {
  let previousValue = currentValue
  currentValue = select(store.getState())
 
  if (previousValue !== currentValue) {
    console.log(
      'Some deep nested property changed from',
      previousValue,
      'to',
      currentValue
    )
  }
}
 
let unsubscribe = store.subscribe(handleChange)
unsubscribe()
```

####  replaceReducer(nextReducer)
Replaces the reducer currently used by the store to calculate the state.

It is an advanced API. You might need this if your app implements code splitting, and you want to load some of the reducers dynamically. You might also need this if you implement a hot reloading mechanism for Redux.

##### ***Arguments***: nextReducer (Function) 
The next reducer for the store to use.

Details about the store can be found [here](https://redux.js.org/api-reference/store).

### Using with react

To use react with redux the steps below need to implemented in your project.

##### Create Actions
Define actions which will mirror the different states you application can possibly have.
###### Example
Sample Code
```
const ActionTypes = {
  LOAD_DATA: 'Care/LOAD_DATA',
};

const Actions = {
  loadData: payload => ({ type: CareActionTypes.LOAD_DATA, payload }),
};

export {
  Actions,
  ActionTypes,
};

```
##### Create Reducers

Create a reducer to manage the change in application state in a predictable manner.

###### Example
Sample Code
```
import { ActionTypes } from 'actions';

const initialState = {
  data: {},
};

const reducer = (state = initialState, action) => {
  switch (action.type) {
    case ActionTypes.LOAD_DATA:
      return { ...state, data: action.payload };
    default:
      return state;
  }
};

export default reducer;

```

##### Create `store` and `reducers` 
Create a `store` using `createStore` method provided by redux and pass the reducer in the method.

###### Example
Sample Code
```
import { createStore } from 'redux';
import reducer from 'reducers';

const store = createStore(reducer);

export default store;
```

##### Use `Provider` to pass the store in `App.jsx`

Assuming `App.jsx` is the root component wrap it in `Provider` component and pass the `store` as props.

###### Example
Sample Code
```
import React, { Component } from 'react';
import { Provider } from 'react-redux';
import store from 'store';

class App extends Component {
	render() {
		return(<div>My Components</div>)
	}
}

render(<Provider store={store}><App /></Provider>, document.getElementById('app'));
```
##### Connecting to the Store

To connect to the store from within a component. We can use `@connect` from `react-redux` package.

###### Example
Sample Code
```
import React, { Component } from 'react';
import PropTypes from 'prop-types';
import { connect } from 'react-redux';

import { Actions } from 'actions';

@connect(store => ({ app: store.reducer }))
class MyComponent extends Component {

  static propTypes = {
    app: PropTypes.object.isRequired,
    dispatch: PropTypes.func.isRequired,
  };

  componentDidMount() {
    this.props.dispatch(Actions.loadData());
  }
  
  render() {
	  const { data } = this.props.app;
	  return (
		<div>{data.keyName}</div>
		);
	}
}

export default MyComponent;

```
