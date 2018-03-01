# Unit Testing

### What is unit testing ?

>A unit test runs some code over a segment of your program checking the input and output. These tests allow developers to check individual areas of a program to see where(and why) errors occur.


```
Test tools can be divided into the following functionalities. 
Some provide us with only one functionality, and some provide us with a combination.
 	1. Test Runners
	2. Testing Frameworks
	3. Asssertion Libraries
	4. Testing Plugins
```
	
It’s common to use a combination of tools even if one can achieve the same using a single tool in order to get a more flexible functionality.

>
1. Provide a test environment (Mocha, Jasmine, Jest, Karma)
2. Provide a testing structure (Mocha, Jasmine, Jest, Cucumber)
3. Provide assertions functions (Chai, Jasmine, Jest, Unexpected)
4. Generate, display, and watch test results (Mocha, Jasmine, Jest, Karma)

Testing structure refers to the organization of your tests. Tests are usually organized in a BDD structure that supports [behavior-driven development](https://en.wikipedia.org/wiki/Behavior-driven_development) (BDD). It often looks like this:

### Testing Structure
```
describe('calculator', function() {
  // describes a module with nested "describe" functions
  describe('add', function() {
    // specify the expected behavior
    it('should add 2 numbers', function() {
       //Use assertion functions to test the expected behavior    
    })
  })
})
```

###Assertion Functions

Assertion functions are functions that make sure tests result as expected where the most popular are the first two :-

```
// Chai expect
expect(foo).to.be.a('string')
expect(foo).to.equal('bar')

// Jasmine expect
expect(foo).toBeString()
expect(foo).toEqual('bar')

// Chai assert
assert.typeOf(foo, 'string')
assert.equal(foo, 'bar')

// Unexpected expect
expect(foo, 'to be a', 'string')
expect(foo, 'to be', 'bar')
```

##What we use ?

1. **Mocha**, used as test enviornment, testing structure and displaying results.
2. **Chai**, used as an assertion function

## [Mocha](https://mochajs.org/#getting-started)
Mocha is a feature-rich JavaScript test framework running on Node.js and in the browser, making asynchronous testing simple and fun. Mocha tests run serially, allowing for flexible and accurate reporting, while mapping uncaught exceptions to the correct test cases.

## [Chai](http://chaijs.com/guide/styles)
Chai is a BDD / TDD assertion library for node and the browser that can be delightfully paired with any javascript testing framework.


## Example
```
describe('Deductibles Helpers', () => {
  it('Calculate progress', () => {
    expect(deductiblesHelpers.calculateProgress(20, 100)).toBe(0.2);
    expect(deductiblesHelpers.calculateProgress(500, 100)).toBe(5);
    expect(deductiblesHelpers.calculateProgress(240, 100)).toBe(2.4);
  });
  it('Format Value', () => {
    expect(deductiblesHelpers.formatValue(25)).toBe('25.00');
    expect(deductiblesHelpers.formatValue(5)).toBe('5.00');
    expect(deductiblesHelpers.formatValue()).toBe('NaN');
  });
  it('Is Fam present', () => {
    expect(deductiblesHelpers.isFamPresent(1, 1, 1, 1)).toBe(true);
    expect(deductiblesHelpers.isFamPresent(1, 1, 1, -1)).toBe(true);
    expect(deductiblesHelpers.isFamPresent(-2, -2, -2, -2)).toBe(false);
  });
});

```






