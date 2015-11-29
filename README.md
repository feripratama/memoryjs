# memoryjs
Node add-on for memory reading and writing! (finally!)

# Features

- open a process

TODO:
- list all open processes
- list modules associated with a process
- read memory
- write to memory
- pattern scanning

# Install

This is a Node add-on and therefore requires [node-gyp](https://github.com/nodejs/node-gyp) to use.
This is currently in development, therefore to test the add-on you must:

- clone/download the repository
- open `compile.bat` or run `node-gyp rebuild` (or `node-gyp configure` followed by `node-gyp build`)
- then just run `node index.js` to run the exemplar

# Usage

To simply open a process:
``` javascript
var memoryjs = require('./build/Release/memoryjs');
var processName = "chrome.exe";

// open the process, callback parameter is the HANDLE cast to an integer
// and will equal 0 if unable to open the process
memoryjs.openProcess(processName, function(process){
  if(process){
    console.log("Successfully opened handle on", processName);

    // closes the handle on the process
    memoryjs.closeProcess(process);
    console.log("Closed handle on", processName)
  } else {
    console.log("Unable to open handle on", processName);
  }
});
```
