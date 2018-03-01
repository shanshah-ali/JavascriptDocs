## Default Parameters in function 
**Default function parameters** allow formal parameters to be initialized with default values if no value or undefined is passed.

    function multiply(a, b = 1) {
	    return a * b;
	}
	
	console.log(multiply(5, 2));
	// expected output: 10
	console.log(multiply(5));
	// expected output: 5

> Here, in this function call, we can observer that in first call we are sending both the parameters and we are getting output as 10, which is working as expected. In the second function call we are passing only one parameter (param **a**) and we are not sending second parameter **b**, as we are not sending second param, default value would be taken for second param, if it had not, then when we multiply param **a** and **b** (be being undefined), it would have thrown NAN.

[Read more about default parameters in function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)

----------

## Class and Inheritance 

### class
Classes are in fact "special functions", and just as you can define function expressions and function declarations, the class syntax has two components: class expressions and class declarations.

#### declaring class:
One way to define a class is using a class declaration. To declare a class, you use the class keyword with the name of the class ("Rectangle" here).

    class Rectangle {
		constructor(height, width) {
		    this.height = height;
		    this.width = width;
		}
	}

#### Constructor
The constructor method is a special method for creating and initializing an object created with a class. There can only be one special method with the name "constructor" in a class. A SyntaxError will be thrown if the class contains more than one occurrence of a constructor method.

> A constructor can use the super keyword to call the constructor of the super class.


#### Sub classing with extends
The extends keyword is used in class declarations or class expressions to create a class as a child of another class.

	class Animal { 
	  constructor(name) {
	    this.name = name;
	  }
  
	  speak() {
	    console.log(this.name + ' makes a noise.');
	  }
	}

	class Dog extends Animal {
	  speak() {
	    console.log(this.name + ' barks.');
	  }
	}
	
	var d = new Dog('Mitzie');
	d.speak(); // Mitzie barks.

> If there is a constructor present in sub-class, it needs to first call super() before using "this"

[Read more about class](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

----------

## Import / Export

### import 
The **import** statement is used to import bindings which are exported by another module.

##### syntax
    import defaultExport from "module-name";
	import * as name from "module-name";
	import { export } from "module-name";
	import { export as alias } from "module-name";
	import { export1 , export2 } from "module-name";
	import { export1 , export2 as alias2 , [...] } from "module-name";
	import defaultExport, { export [ , [...] ] } from "module-name";
	import defaultExport, * as name from "module-name";
	import "module-name";

#### defaultExport
Name that will refer to the default export from the module.

#### module-name
The module to import from. This is often a relative or absolute path name to the .js file containing the module, excluding the .js extension. Certain bundlers may permit or require the use of the extension; check your environment. Only single quotes and double quotes Strings are allowed.

#### name
Name of the module object that will be used as a kind of namespace when referring to the imports.

#### export, exportN
Name of the exports to be imported.

#### alias, aliasN
Names that will refer to the named imports. 

[Read more about Imports](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)

### Export

The export statement is used when creating JavaScript modules to export functions, objects, or primitive values from the module so they can be used by other programs with the import statement.

##### syntax

    export { name1, name2, …, nameN };
	export { variable1 as name1, variable2 as name2, …, nameN };
	export let name1, name2, …, nameN; // also var
	export let name1 = …, name2 = …, …, nameN; // also var, const
	export function FunctionName(){...}
	export class ClassName {...}
	
	export default expression;
	export default function (…) { … } // also class, function*
	export default function name1(…) { … } // also class, function*
	export { name1 as default, … };

	export * from …;
	export { name1, name2, …, nameN } from …;
	export { import1 as name1, import2 as name2, …, nameN } from …;

#### nameN
Identifier to be exported (so that it can be imported via **import** in another script). 

[Read more here](https://developer.mozilla.org/en-US/docs/web/javascript/reference/statements/export)


----------



