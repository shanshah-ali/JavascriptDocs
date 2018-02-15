#Error handling in JS
##Categories of Errors
###Syntax Errors
~~~
var x = 2;
var y = 3;
console.log(x+y;
~~~
###Runtime Errors
~~~
alert(x);
   x is undefined
undefinedfunction()   
~~~
###Logical Errors
~~~
 function power(base, exponent) {
    var result = 1;
    for (var count = 0; count < exponent; count++)
      result *= base;
    return result;
  }
  power(5, 0)
  power('abc', 0.5)
~~~
###Try...Catch...Finally..Throw
~~~
try {
    // Code to run
    [
      break;
    ]
  } catch (e) {
    // Code to run if an exception occurs
    [
      break;
    ]
  }
  [
    finally {
      // Code that is always executed regardless of 
      // an exception occurring
    }
  ]
~~~
~~~
function getMonthName(mo) {
  mo = mo - 1; // Adjust month number for array index (1 = Jan, 12 = Dec)
  var months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul',
                'Aug', 'Sep', 'Oct', 'Nov', 'Dec'];
  if (months[mo]) {
    return months[mo];
  } else {
    throw 'InvalidMonthNo'; //throw keyword is used here
  }
}

try { // statements to try
  monthName = getMonthName(myMonth); // function could throw exception
}
catch (e) {
  monthName = 'unknown';
  logMyErrors(e); // pass exception object to error handler -> your own function
}
~~~
~~~
InputStream is = new FileInputStream("C://test.txt");
try {
    //code...
} catch (Exception e) {
    //code...
} finally {
    is.close();
}
~~~
 