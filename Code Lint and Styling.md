# Code Lint and Styling
## ESLint: Static Analysis
### What is Lint?
A `Lint` or `Linter` is a static analysis tool that is used to analyze source code to flag programming errors, bugs, stylistic errors and suspicious construct.

The specific list of problems that lint checks varies by implementation and version of the tool. However, most flavors of lint will at least check for the following:

- Possible indexing beyond array bounds.
- Suspicious assignments (such as *if (a = b)*).
- Mismatches in variable types.
- Potentially dangerous data type combinations.
- Unused variables.
- Unreachable code.
- Multiple imports.
- Non-portable constructs.

### Why should I Lint?
Apart from the common checks mentioned above linting will run through the code and find
- Formatting discrepancy.
- Non-adherence to coding standards and conventions.
- Pinpointing possible logical errors in the program.
- Avoid scope conflicts.

Furthermore, it ensures that the source code is legible, readable, less polluted and easier to maintain.

Some common mistakes that javascript lint looks for
- Missing semicolons at the end of a line.
- Curly braces without an *if,* *for*, *while*, etc.
- Code that is never run because of a *return*, *throw*, *continue*, or *break*.
- Case statements in a *switch* that do not have a *break* statement.
- Leading and trailing decimal points on a number.
- A leading zero that turns a number into octal (base 8).
- Comments within comments.
- Ambiguity whether two adjacent lines are part of the same statement.
- Statements that don't do anything.

It also looks for the following less common mistakes

- Regular expressions that are not preceded by a left parenthesis, assignment, colon, or comma.
- Statements that are separated by commas instead of semicolons.
- Use of increment (++) and decrement (--) except for simple - statements such as "*i++;*" or "*--i;*".
- Use of the void type.
- Successive plus (e.g. *x+++y*) or minus (e.g. *x---y*) signs.
- Use of labeled *for* and *while* loops.
- *if*, *for*, *while*, etc. without curly braces.

### ESLint vs JSLint
#### JSLint

JSLint is the oldest linter available. Douglas Crockford created it in 2002 to enforce what, in his experience, are the good parts of JavaScript. If you agree with the good parts, JSLint can be a good tool—you install it and it’s ready to go.

The downsides are that JSLint is not configurable or extensible. You can’t disable many features at all, and some of them lack documentation. The official website is not very helpful, for example it lacks any information on how to integrate it with your editor.

#####  Pros
- Comes configured and ready to go.
##### Cons
- JSLint doesn’t have a configuration file, which can be problematic if you need to change the settings.
- Limited number of configuration options, many rules cannot be disabled.
- You can’t add custom rules.
- Undocumented features.
- Difficult to know which rule is causing which error.

#### ESLint
ESLint is the most recent of all the linters. It was designed to be easily extensible, comes with a large number of custom rules, and it’s easy to install more in the form of plugins. It gives concise output, but includes the rule name by default so you always know which rules are causing the error messages.

ESLint documentation can be a bit hit or miss. The rules list is easy to follow and is grouped into logical categories, but the configuration instructions are a little confusing in places. It does, however, offer links to editor integration, plugins and examples all in a single location.

##### Pros
- Flexible: any rule can be toggled, and many rules have extra settings that can be tweaked.
- Very extensible and has many plugins available.
- Easy to understand output.
- Includes many rules not available in other linters, making ESLint more useful for detecting problems.
- Best ES6 support, and also the only tool to support JSX.
- Supports custom reporters.
##### Cons
- Some configuration required.
- Slow, but not a hindrance.

### .eslintrc

ESLint can be configure in two ways.

 1. Configuration comments.
 2. Configuration Files.

At Evive, everything related to eslint configuration is in the file `.eslintrc`. More on configuring ESLint over [here](https://eslint.org/docs/user-guide/configuring).

## Code Styling

Below are the styling guidelines that should be consciously.

1. Component file names and should be PascalCase.
	* *biometricScreening, documentsearch* :x:
	
	*  *BiometricScreening, DocumentSearch* :white_check_mark:

2. Variables and Function names should be in camelCase.
	*  *totalsteps, activity_start_date, SanitizeToObject* :x:
	
	*  *totalSteps, activityStartDate, sanitizeToObject* :white_check_mark:

3. Constants and exported Enums should be capitalized snake case. 
	* *ModeOfContact, amountatretirmentage, expectedAnnualrate* :x:
	
	* *MODE_OF_CONTACT, AMOUNT_AT_RETIREMENT_AGE, EXPECTED_ANNUAL_RATE* :white_check_mark:

4. Directory names should be spinal-case.
	* *biometricscreening, Health-Quest, IncentiveManagement* :x:
	* *biometric-screening, health-quest, incentive-management* :white_check_mark:

5. Use destructuring assignment syntax when the data object is accessed multiple times.
	```
	const myObject = {
		first: 1,
		second: 2,
		third: 3,
	};
	
	printMyObject = () => {
		// Do not do this
		console.log(myObject.first);
		console.log(myObject.second);
		console.log(myObject.third);
	}

	printMyObjectAgain = () => {
		// Do this
		const { first, second, third } = myObject;
		console.log(first);
		console.log(second);
		console.log(third);
	}
	```

## Evive IntelliJ Setup
### Copyright and File Headers
#### Copyright
Follow the steps to insert the copyright text in your files.
The description for the text can be found here.
##### Step 1
![enter image description here](https://lh3.googleusercontent.com/mrmHlajhtbV2zEu6pGzs2cmPv8syfFJmgaviIPGyXcqcx0KfQzOfdkwEeg6mF51HhUYwTmbwy7U3)
##### Step 2
![enter image description here](https://lh3.googleusercontent.com/1i3C5di9Nk1vfj5luHxacf7uzrxHnEjLJNKSze6Z0yCjlYmf6krt1JKOTrbtqIS4BrN_niuQssYh)

##### Step 3
![enter image description here](https://lh3.googleusercontent.com/Dnmw9iGMcH7eXBF9qHCN1Mua27AOn-tvl7CQcX9L6xPfIrQpMy6cWeSoQXZgp7ivZu4WoyUbpOEw)

##### Step 4
![enter image description here](https://lh3.googleusercontent.com/lW_fiiykUKyS69JlyZx7DYGFXBYqSUFs_HjJCfS_NTYD68E9p8uy_rF99DTDlSQFmiB5xoa1Q91m)

##### Step 5
![enter image description here](https://lh3.googleusercontent.com/YKmt2IDR728pAtHb_6-IQYaKGKlYyHkSH4BdO-1HB-cCqHheGASpEwxnkDQiPZJTMM-klV0DeiJh)

##### Step 6
![enter image description here](https://lh3.googleusercontent.com/cq3zBo6YE3nTVnON1pgvylnJ866tTb0c7DPE2Bs8Cxd4y6lrrAut9Z4PMnwEWzmVqPrA4Mnpt6RF)
##### Step 7
![enter image description here](https://lh3.googleusercontent.com/s1NgG_73_fEOpO4W4ixxcI3h4UonEISTVTjCgCNGGo3usgbRiOPaqTpd-CfhUbL5_snI8ih08y20)

#### File Header
Follow the steps to insert the File Header in your files.
The text to add for file header is here.

##### Step 1
![enter image description here](https://lh3.googleusercontent.com/SxLGiCSEKlfxQDZRxjLU-ixaHIuz-gmUAfQ2qewjY1ja6KAK84gCupErKZmcmPlE8guse3fsgp56)

##### Step 2
![enter image description here](https://lh3.googleusercontent.com/Lano89Ro19BSTKyFVDnGhzMRcKnjse_d5kAv-SDK4DBfSmOZq5Ff59WMnj0iQnOlMxQLFyupRKve)

##### Step 3
![enter image description here](https://lh3.googleusercontent.com/zm8fAxu-ER8Kzj7CJb0fD60qejgspWnfVQi-6F1GxDLqmRYCgv6gTr1Yg8tY7VV2lf3PhisxY5sp)

### ESLint Setup

##### Step 1
![enter image description here](https://lh3.googleusercontent.com/69RedaE6TVsi2CmFbJz54gohbIQSP8nWwyUL9Wopxqa9ZhjP_0466M9Rm79UcLhZEUvVhYqLYjtJ)

##### Step 2
![enter image description here](https://lh3.googleusercontent.com/N1MOd2fD-JaGgH0LCx-ERFsyYvG8b-Y23KDm3NPFNo13iongvWqMTnBS47zAYlbrcXZTK6rZrhIS)

##### Step 3
![enter image description here](https://lh3.googleusercontent.com/eciMZaqBHD-iLbcD4QHIDJYTHe8ZwR6bf1A8HAphRJCiPTifm7ICJz45V7ow8yEFm6AaBgGywkHU)

## JSDoc 
### What is JSDoc ?
JSDoc is an API documentation generator for JavaScript.
Documentation comments added directly to the source code is scanned and an HTML documentation website is generated.

JSDoc's purpose is to document the API of your JavaScript application or library. 

JSDoc comments should generally be placed immediately before the code being documented. Each comment must start with a 
`/**` sequence in order to be recognized by the JSDoc parser. 

Comments beginning with `/*`, `/***`, or more than 3 stars will be ignored. 

###### Example 1
```
/* Sanitizes raw html and return an object */
const sanitizeToObject = dirtyHtml => {
	// Do Something
}
```

Adding a description is simple—just type the description in the documentation comment.

Special "JSDoc tags" can be used to give more information. For example `@params` tags can be used to further describe the parameters.

###### Example 2
```
/**
* Validates if phone and confirm phone fields are the 
* same
* @param phoneParam {number} Phone no provided by user in phone no input field
* @param confirmPhoneParam {number} Phone no provided by user in  confirm phone input field
* @returns {object} Returns the validation status and error message
*/
validateAndConfirmPhone = (phoneParam, confirmPhoneParam) => {
	// Do Something
}
```

### Generating a website
Once the code is commented, JSDoc can be used to generate an HTML website from the source files.

By default, JSDoc uses the built-in "default" template to turn the documentation into HTML. This template can be edited to suite one's needs or create a new template entirely.

Running the documentation generator on the command line
```
jsdoc Validations.js
```
This command will create a directory named out/ in the current working directory. Within that directory, will be the generated HTML pages.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcwMzgzMzY3XX0=
-->