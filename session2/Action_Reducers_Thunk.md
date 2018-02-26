##Redux
###Actions
Actions are payloads of information that send data from your application to your store. They are the only source of information for the store.

In Redux, to actually initiate a dispatch, pass the result to the dispatch() function

~~~
dispatch(addTodo(text))
dispatch(completeTodo(index))
~~~

Refference: [https://redux.js.org/basics/actions]()

--

####Action Types
Action type are set of enums, each of which should have a corresposnding reducer part. In small projects you can directly pass them as strings, but in most cases it is easier to have all Action types defined seprately (sometimes in a seperate file).

~~~
const HomeActionTypes = {
	FETCH_DATA: 'HOME_PAGE/FETCH_DATA',
	FETCH_OTHER_DATA: 'HOME_PAGE/FETCH_OTHER_DATA',
}
~~~

Note: Remember redux combines all actiona and reducers together, so its very important to have all action types unique througout the project.

--

###Reducers
Reducers specify how the application's state changes in response to actions sent to the store. Remember that actions only describe the fact that something happened, but don't describe how the application's state changes.

**Just remember that the reducer must be pure. Given the same arguments, it should calculate the next state and return it. No surprises. No side effects. No API calls. No mutations. Just a calculation.**

~~~
function todoApp(state = initialState, action) {
  switch (action.type) {
    case SOME_ACTION_ENUM:
      return {
      		...state,
      		key: newValue,
      		key2: someUtilFunctionToComputeValue(someKey),
      }
    default:
      return state
  }
}
~~~

**Things to remember**

- We don't mutate the state. Use spread operator, create a new object and overwrite/add your new key values.
- We return the previous state in the default case. It's important to return the previous state for any unknown action.
- Do not call non-pure functions, e.g. Date.now() or Math.random().
- Do not Perform side effects like API calls and routing transitions;
- Do not Mutate its arguments. Look into **Immutable Update Patterns** section for that.

Note: Note that each of these reducers is managing its own part of the global state. The state parameter is different for every reducer, and corresponds to the part of the state it manages.

Refference: [https://redux.js.org/basics/reducers]()

--

###Thunk Middleware

Redux Thunk middleware allows you to write action creators that return a function instead of an action. The thunk can be used to delay the dispatch of an action, or to dispatch only if a certain condition is met. The inner function receives the store methods dispatch and getState as parameters.

Generally a action cooresponds to a reducer and looks like this:

~~~
const HomeActionTypes = {
	GOAL_SELECT: 'HOME/GOAL_SELECT',
}
const HomeActions = {
	setGoal: payload => ({ type: HomeActionTypes.GOAL_SELECT, payload }),
}
~~~

Now what if you want to make another action call from the setGoal function? Or what if you want to make an API call, and then call the reducer with the result? Thunk is used specifically to help in such cases.

~~~
setGoal: payload => ((dispatch) => {
	HomeServices.setGoalSelection(payload.value)
	.then(response => {
		dispatch(HomeActions.setGoalSelectedState(response)); // calls another action
	});
}),
~~~

You can also access the state from here, to get some value directly from store instead of passing with the payload.

~~~
setGoal: payload => ((dispatch, getState) => {
	HomeServices.setGoalSelection(payload.value, getState().storeName.keyName)
	.then(response => {
		dispatch(HomeActions.setGoalSelectedState(response)); // calls another action
	});
}),
~~~

Note: You cannot call a reducer with thunk. If you are using Thunk, create another Action to call the reducer.

Refference: [https://github.com/gaearon/redux-thunk]()