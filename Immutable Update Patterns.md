# Immutable Update Patterns

--

### Introduction

Objects in javascript are storred by address, and we should be very carefull while changing certain properties of an object, as it might result in mutating the actual object rather than making a new copy of it. In redux the whole state is an object, and often complex state change requires you to change certain properties only. 


Here are some examples for some of the more common tasks you might have to implement.

--

### Updating nested object

The key to updating nested data is that every level of nesting must be copied and updated appropriately. This is often a difficult concept for those learning Redux, and there are some specific problems that frequently occur when trying to update nested objects. These lead to accidental direct mutation, and should be avoided.

**Common Mistake #1: New variables that point to the same objects**

Defining a new variable does not create a new actual object - it only creates another reference to the same object. An example of this error would be:

~~~Javascript
let nestedState = state.nestedState;

// ERROR: this directly modifies the existing object reference - don't do this!
nestedState.nestedField = action.data;

return {
    ...state,
    nestedState
};
~~~

This function does correctly return a shallow copy of the top-level state object, but because the nestedState variable was still pointing at the existing object, the state was directly mutated.

**Common Mistake #2: Only making a shallow copy of one level**

~~~Javascript
// Problem: this only does a shallow copy!
let newState = {...state};

// ERROR: nestedState is still the same object!
newState.nestedState.nestedField = action.data;

return newState;
~~~

Doing a shallow copy of the top level is not sufficient - the nestedState object should be copied as well.

**Correct Approach: Copying All Levels of Nested Data**

~~~Javascript
return {
        ...state,
        first : {
            ...state.first,
            second : {
                ...state.first.second,
                [action.someId] : {
                    ...state.first.second[action.someId],
                    fourth : action.someValue
                }
            }
        }
    }
~~~

Obviously, each layer of nesting makes this harder to read, and gives more chances to make mistakes. This is one of several reasons why you are encouraged to keep your state flattened, and compose reducers as much as possible.

--

**Inserting and Removing Items in Arrays**

Normally, a Javascript array's contents are modified using mutative functions like push, unshift, and splice. Since we don't want to mutate state directly in reducers, those should normally be avoided. Because of that, you might see "insert" or "remove" behavior written like this:

~~~
function insertItem(array, action) {
    return [
        ...array.slice(0, action.index),
        action.item,
        ...array.slice(action.index)
    ]
}

function removeItem(array, action) {
    return [
        ...array.slice(0, action.index),
        ...array.slice(action.index + 1)
    ];
}
~~~

Remember, as long as we make a copy first, we can safely mutate the copy.

~~~
function insertItem(array, action) {
    let newArray = array.slice();
    newArray.splice(action.index, 0, action.item);
    return newArray;
}

function removeItem(array, action) {
    let newArray = array.slice();
    newArray.splice(action.index, 1);
    return newArray;
}

// the above function can also be written as 

function removeItem(array, action) {
    return array.filter( (item, index) => index !== action.index);
}
~~~

--

**Updating an Item in an Array**

Updating one item in an array can be accomplished by using Array.map, returning a new value for the item we want to update, and returning the existing values for all other items:

~~~
function updateObjectInArray(array, action) {
    return array.map( (item, index) => {
        if(index !== action.index) {
            // This isn't the item we care about - keep it as-is
            return item;
        }

        // Otherwise, this is the one we want - return an updated value
        return {
            ...item,
            ...action.item
        };    
    });
}
~~~
--

###Immutable Update Utility Libraries
Because writing immutable update code can become tedious, there are a number of utility libraries that try to abstract out the process. 

* [dot-prop-immutable](https://github.com/debitoor/dot-prop-immutable)
* [immutability-helper](https://github.com/kolodny/immutability-helper)
* [other immutable-update-utilities](https://github.com/markerikson/redux-ecosystem-links/blob/master/immutable-data.md#immutable-update-utilities)

--

*Refference: https://redux.js.org/docs/recipes/reducers/ImmutableUpdatePatterns.html*