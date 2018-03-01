### Map() function

The map() method creates a new array with the results of calling a provided function on every element in this array.
* the length of the resulting array is always same.
* it does not change the original array.

Examples:

```
const myArray = [1, 2, 3 ,4];

const myNewArray = myArray.map(element  => element + 1);

console.log(myArray); // [1, 2, 3, 4]
console.log(myNewArray); // [2, 3, 4, 5]
```

```
let names = [{
  firstName: 'John',
  lastName: 'Smith',
}, {
  firstName: 'Nick',
  lastName: 'Walls',
}];

const joinedNames = names.map((currentName, i) => {
  return {
    name: currentName.firstName + ' ' + currentName.lastName,
  };
});

console.log(joinedNames); // [ { name: 'John Smith' }, { name: 'Nick Walls' } ]
```

### Filter() function

The filter() method creates a new array filled with all array elements that pass a test (provided as a function).

* it does not execute the function for array elements without values.
* the length of the resulting array may or may not be same.
* it does not change the original array.

Exmaples:
```
const ages = [32, 33, 16, 40];

const newAges = ages.filter(currentAge => age >= 18);

console.log(ages); // [32, 33, 16, 40]
console.log(newAges); // [32, 33, 40]
```

### Reduce() function

The reduce() method reduces the array to a single value by executing a provided function for each value of array.
* the return value of the function is stored in an accumulator (result/total).
* returns the accumulated result from the last call of the callback function

Example: 
```
const numbers = [65, 44, 12, 4];
const getSum = numbers.reduce((total, num) => total + num);

console.log(getSum); // 125
}
```
```
const numbers = [65, 44, 12, 4];
const getSum = numbers.reduce((total, num) => total + num, 30); // 30 is passed as initial value to the function

console.log(getSum); // 155
```
