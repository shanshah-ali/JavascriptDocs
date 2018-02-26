## Logging
The Console object provides access to the browser's debugging console (e.g. the Web Console in Firefox). The specifics of how it works varies from browser to browser, but there is a de facto set of features that are typically provided.

>The Console object can be accessed from any global object. Window on browsing scopes and WorkerGlobalScope as specific variants in workers via the property console. It's exposed as Window.console, and can be referenced as simply console. For example:

```
console.log("Failed to open the specified link")
```
### Methods
```
Console.assert()
Log a message and stack trace to console if the first argument is false.
```
```
Console.clear()
Clear the console.
```
```
Console.count()
Log the number of times this line has been called with the given label.
```
```
Console.debug()
An alias for log().
```
> Note: Starting with Chromium 58 this method only appears in Chromium browser consoles when level "Verbose" is selected.
```
Console.dir() 
Displays an interactive listing of the properties of a specified JavaScript object. This listing lets you use disclosure triangles to examine the contents of child objects.
```
```
Console.dirxml() 
Displays an XML/HTML Element representation of the specified object if possible or the JavaScript Object view if it is not possible.
```
```
Console.error()
Outputs an error message. You may use string substitution and additional arguments with this method.
```
```
Console.exception()  
An alias for error().
```
```
Console.group()
Creates a new inline group, indenting all following output by another level. To move back out a level, call groupEnd().
```
```
Console.groupCollapsed()
Creates a new inline group, indenting all following output by another level. However, unlike group() this starts with the inline group collapsed requiring the use of a disclosure button to expand it. To move back out a level, call groupEnd().
```
```
Console.groupEnd()
Exits the current inline group.
```
```
Console.info()
Informative logging of information. You may use string substitution and additional arguments with this method.
```
```
Console.log()
For general output of logging information. You may use string substitution and additional arguments with this method.
```
```
Console.profile() 
Starts the browser's built-in profiler (for example, the Firefox performance tool). You can specify an optional name for the profile.
```
```
Console.profileEnd() 
Stops the profiler. You can see the resulting profile in the browser's performance tool (for example, the Firefox performance tool).
```
```
Console.table()
Displays tabular data as a table.
```
```
Console.time()
Starts a timer with a name specified as an input parameter. Up to 10,000 simultaneous timers can run on a given page.
```
```
Console.timeEnd()
Stops the specified timer and logs the elapsed time in seconds since it started.
```
```
Console.timeStamp() 
Adds a marker to the browser's Timeline or Waterfall tool.
```
```
Console.trace()
Outputs a stack trace.
```
```
Console.warn()
Outputs a warning message. You may use string substitution and additional arguments with this method.
```

### Usage
> Outputting text to the console
The most frequently-used feature of the console is logging of text and other data. There are four categories of output you can generate, using the console.log(), console.info(), console.warn(), and console.error() methods respectively. Each of these results in output styled differently in the log, and you can use the filtering controls provided by your browser to only view the kinds of output that interest you.

>There are two ways to use each of the output methods; you can simply pass in a list of objects whose string representations get concatenated into one string, then output to the console, or you can pass in a string containing zero or more substitution strings followed by a list of objects to replace them.

Outputting a single object
The simplest way to use the logging methods is to output a single object:
```
var someObject = { str: "Some text", id: 5 };
console.log(someObject);
```
The output looks something like this:
```
[09:27:13.475] ({str:"Some text", id:5})
```
for more example [clickhere](https://developer.mozilla.org/en-US/docs/Web/API/console)


|  Log4js.Level   | Description   |
|---|---|
| OFF | fatal errors are logged  |
| FATAL | 	fatal errors are logged|
| ERROR  |  errors are logged|
| WARN |  warnings are logged|
| INFO |  infos are logged |
| DEBUG  |  debug infos are logged |
| TRACE | traces are logged |
|ALL |	everything is logged|

# LOGGING AND HISTORY IN EVIVE (CAMPAIGN) -
#### How to insert a log
```
Ea.addEvent('log', 'INFO', hqLogHistoryResolver.getLogHistoryData(payload, this.props.healthQuestViewStore), 'click');
```

#### How to insert history
```
 Ea.addEvent('history', 'health_quest', 'going_back_to_home_from_quest_page', 'click');
```
### Below are the defined params for ea.addEvent
#### 1. catagory : history/log
#### 2.  type: 
 - In case of log the type can be INFO , WARN ,ERROR, ERRORCRITICAL depending on the severity of the log
  - In case of history the type can be - gameday, history_download , insertUiActivityHistory , challenges , hhr , health_quest , ui_history in case you want to add a new type based on a product add it in [FrontEndLogger.java](https://github.com/EviveHealth/Campaigns/blob/master/src/main/java/com/evive/campaigns/controller/FrontEndLogger.java)  
  
 #### 3. event : 
 - In case of log this will be the logger message eg. user landed on gamecenter page
 - In case of history this will be theevent happening eg-started_playing_gameday
 ##### Note - history's event should not be space seprated prefer underscore

#### 4. action : 
- In case of log : Its usually empty
- in case of history : this is the action performed by the user eg- clicked , submitted

> There are two other params which we can use in this function those are 1 hermeStats(in case you want to send the browser info) 2 timeOfOrigin(actual time of the event occurence)
 
> whenever there are events  that fill the buffer the data is sent to elastic search (consulting file is [EA.js](https://github.com/EviveHealth/Campaigns/blob/master/frontend-v2/src/services/analytics/Ea.js))

  





