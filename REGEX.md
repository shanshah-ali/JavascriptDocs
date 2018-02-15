# Regex

[![N|Solid](http://onlineregextester.jareblinux.com/assets/og.png )](https://regexr.com/)

Regular expressions are patterns used to match character combinations in strings. In JavaScript, regular expressions are also objects. These patterns are used with the exec and test methods of RegExp, and with the match, replace, search, and split methods of String. 
There are 12 characters with special meanings: the backslash \, the caret ^, the dollar sign $, the period or dot ., the vertical bar or pipe symbol |, the question mark ?, the asterisk or star *, the plus sign +, the opening parenthesis (, the closing parenthesis ), the opening square bracket [, and the opening curly brace {, These special characters are often called "metacharacters". Most of them are errors when used alone.
### syntax
```
/pattern/modifiers;
```
- /pattern/    '/' this a delimiter. the expression should be written between two delimiter's
### Some basic examples

 ```
/evive/g
```
#### *click image's to go to code.*

 [![N|Solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/regex%20evive%201.png)](https://regexr.com/3kkqe)
 - 'g' here means global and is a modifier/flag.
 - 'Evive' doesn't match the expression because 'E' is capital . So it shows regex is case         sensitive (unless you turn on ignore case sensitive flag).

 #### Character clases
|  Expression   | Result   |
|---|---|
| .  | any character except newline  |
|  \w \d \s | 	word, digit, whitespace  |
| \W \D \S  |  	not word, digit, whitespace |
| [abc]  |  any of a, b, or c |
|  [^abc] |  not a, b, or c |
| [a-g]  |  character between a & g |
 
 
 ```
 /./g
 ```
 
 [![N|Solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/regex%20evive%202%20..png)](https://regexr.com/3kkr3)
### Optional
```
/bananas?/g
```

[![N|solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/regex%20evive%203%20banana.png)](https://regexr.com/3kkrl)

- '?' in expression tells the regex engine that we want the character before '?' is optional hence 'bananas?' matches with both banana and bananas. 

```
/foo(bar)?/g
```
- The ( ) makes 'bar' a group. so in this case expression will match 'foo' as well as foobar.

[![N|solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/regex%20evive%204%20foobar.png)](https://regexr.com/3kkru)

#### Q.1  Match both british(colour) spelling of color and american(color)?
![N|solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/regex%20evive%20color%205%20.png)


### Character set
##### Suppose we want to match any number 
we can make every number optional but that is not a practical approach.
so we will use a character class and range. syntax-  
```
/[range]/g
```
For example if we want to match number's 1 to 5 . so the range will be 1-5 which means - 1,2,3,4,5 in any order
```
/[1-5]/g
 ```
 [![N|solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/regex%20evive%206%201-5.png)](https://regexr.com/3kkt5)
 
 So to match all the numbers.The range will be [0-9] .
 
 #### If we want to match alphabets [a-z] will only match lower case letters and [A-D] will match all the capital letters. To match both smaller and capital alphabets the range will be [a-zA-Z].
 
### Plus '+'
'+' - Matches 1 or more of the preceding token.
 Example
 we can use plus to match the text starting from same expression.
 
 Expression
 ```
 /foo+/g
 ```
Text
```
fo
foo
fooooooooooooooooooooooooo
foooooooooooooooooooooooooooooooooooooooooooooooo
```
Result
 [![N|solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/regex%20foo+.png)](https://regexr.com/3kktt)

 
### Alternations

if the given text is 
```
bad bud bod bed bid
```
and we only want to match the words bad,bed,bid.

######  In this case we will use alterations we will use pipe symbol '|' - Acts like a boolean OR. Matches the expression before or after the '|'.It can operate within a group, or on a whole expression. The patterns will be tested in order.


[![N|solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/regex%20pipe.png)](https://regexr.com/3kkuf)
### How to select words which have alphabets on first three index value->
Quantifier - Matches the specified quantity of the previous token. {1,3} will match 1 to 3. {3} will match exactly 3. {3,} will match 3 or more.
[![N|solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/max%203.png)](https://regexr.com/3kldf)

 #### how to match words starting with foo? 
 we will use ^
 ```
 /^foo/gm
 ```
  /gm here is g stands for global and m stands for multile flag .there are total 5 flags used in regex
[![N|solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/%5Efoo.png)](https://regexr.com/3kleg)

 #### how to match ending starting with foo?
 we will use $
```
/foo$/
```
[![N|solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/foo$.png)](https://regexr.com/3kles)




## REGEX in JavaScript

Html file
```
<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />
<title>JavaScript program to calculate multiplication of two numbers </title>
</head>
<body>

1st Number : <input type="text" id="firstNumber" /><br>
2nd Number: <input type="text" id="secondNumber" /><br>
<input type="button" onClick="multiplyBy()" Value="Multiply" />

<p>The Result is : <br>
<span id = "result"></span>
</p>

</body>
<script type="text/javascript" src='./regex.js'></script>
</html>
```
Js file
```
function multiplyBy()

{
        num1 = document.getElementById("firstNumber").value;
        num2 = document.getElementById("secondNumber").value;
        if(num1.match(/\d+/g) && num2.match(/\d+/g) ){
          document.getElementById("result").innerHTML = num1 * num2;
      }
      else{
        document.getElementById("result").innerHTML = 'wrong input' ;
      }
}
```
### [Try the code](https://codepen.io/GAVISHSETHI/pen/gvRKpZ?editors=1010)
>This code checks the input should be a number. 
> '\d' - Matches any digit character (0-9). Equivalent to [0-9].

![N|solid](https://047f018102c8c8f717a6-1efb167bc857a9871c34d9fa1ea1cbde.ssl.cf1.rackcdn.com/regex%20images/regex%20%5Cd%20etc.png)


### Validation's which are being used in evive -

- *valid name*  /^([a-zA-Z-]|([a-zA-Z]\s[a-zA-Z]))+$/g
-  *mobile n0*  /^[1-9]{1}[0-9]{9}$/
-  Rest of the validation can be viewed in Campaigns/frontend-v2/src/scripts/Validation.js or [click here]


### References
* [regexr] - Practiceonline
* [cheatsheet]  - Quick-Start

   [cheatsheet]: <http://www.rexegg.com/regex-quickstart.html>
   [regexr]: <https://regexr.com/>
   [click here]: <https://github.com/EviveHealth/Campaigns/blob/master/frontend-v2/src/scripts/Validation.js>
  
 