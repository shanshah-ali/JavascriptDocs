## Webpack
**Server side Templating:-** Black end creates a HTML docuemnt and send it to user.
This document is full renderd HTML document.
**Single Page App:-** Server side a bare-bones(skeleton) of HTML doc to user. Javascript runs on the user machineto assemble a full page.
##### What is webpack?
In server side templating world we rely on our server to gether HTML document and in Single page application we rely on big pile of Javasrcipt code that is being executed on the users machine.
![alt text](https://i.imgur.com/iaVa6t3.png) ![alt text](https://i.imgur.com/p6Xk1mB.png)
##### Popularity
![alt text](https://i.imgur.com/GcJAnau.png)

> In SPA world we are relying on javascript code that is executed of our user browser to assemble the entire web application.
![Javscript Modues](https://i.imgur.com/4i0dYeg.png)

***Javscript Modues:-*** A CommonJS module is essentially a reusable piece of JavaScript which exports specific objects, making them available for other modules to require in their programs. If you've programmed in Node.js, you'll be very familiar with this format.
![alt text](https://i.imgur.com/Yqy3IGi.png)
**Problems starts to rise with seprating our code into sperate files**
**Load order:-** order in which our code is executed
![Load Order](https://i.imgur.com/NigPtCt.png)
**Load Time:-** Loading many JS files over http connection is generally consider to be bad idea from a performace stand point.More files we have the slower lower time for our page.
![Load time](https://i.imgur.com/hSoFn1i.png)

### WEBPACK
So purpose of webpack is to take big collection of tiny little JS modules and merge then all into one big JS file while also assuring that each module is executed in the correct order.
![webpack](https://i.imgur.com/3fOwVqW.png)
***By this we solve two issues:-***
1. Final output will deal with load order of a bunch of different modules.
2. Loading up tone of JS modules over a network connection.

![laodTIme](https://i.imgur.com/F8LfBJF.png)
 
