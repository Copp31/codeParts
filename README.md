# :computer: FasterWeb functions and testing interface 
> In this project, you will find a repository for FasterWeb script functions and a testing interface.

### Table of Contents
1. [Introduction](#introduction)
2. [Script functions](#script-function)
    1. [Folder location](#folder-location)
    2. [Script files configuration](#configuration)

3. [Testing comand-line interface](#testing-CLI)
    1. [Technologies](#technologies)
    2. [CLI](#cli)

4. [Write a test](#test)
    1. [Step 1 : variable name](#variable-name)
    2. [Step 2 : write your tests](#write)    
    3. [Step 3 : runTests()](#runtest)  



### Introduction <a name="introduction"></a>

The purpose of this project is to be able to easily **share the script functions** used in Fastercom's client projects. 

It's also possible to test all the functions or a precise one when you launch **runTests.js** from the Command-line interface.
You will see the results of each test in the terminal. 

Each test needs to be written following a precise pattern and configuration.




## :memo: Script functions <a name="script-function"></a>
### Folder location <a name="folder-location"></a>

All the script files are listed under folders named by function type (autofill, autohide, search, dev)

```
scripts / autofill
        / autohide 
        / search
```


### Script file configuration <a name="configuration"></a>

- Script files use the extension .txt
- There's one script in each file
- Name of the file is written in camelCase
- There's a summary of the script at the beginning of each .txt file :

```
// To get a clear summary of items when you have the item's name and quantity

let array = [];

[...]
```


## :chart_with_upwards_trend: Testing Comand-line interface <a name="testing-CLI"></a>

Each script can be tested while running runTests.js. 

- Be sure that your .txt and .js files are in the **correct folder** to run a test.
- It is also essential to use the **same name** for these two files.

```
scripts / autofill
            /test.txt
        / autohide 
        / search

tests   / autofill
            /test.js
        / autohide 
        / search
```

**Important**: The js file will be written following the EayTest.js model in the /dev folder.


### Technologies <a name="technologies"></a>
This project is created with : 

* Node version : 16.15.0
* NPM version : 8.5.5
* JavaScript : ES2020 


### Command-line interface <a name="cli"></a>

To run the testing interface, you need to install [Node](https://nodejs.org/en/download/) on your computer.

To launch tests, you have to run **runTests.js** from the FWfunctions folder.


```
$ node runTests.js 
```

You should see this in your terminal : 

```
--------------- tests interface ---------------

1. Run all tests from all functions
2. Run all tests from one specific function
3. Exit test module


What do you want to test (1, 2, 3)? 
```

If you want to run all tests from one specific function, you will be asked the function type (autofill, autohide, search, dev) and the function name:

```
Write Function Type : dev
Write function name : EasyName
```

*Tricks: if you don't know this last info, start with option one. You will find the information that you're looking for*


## :pencil2: Write a test <a name="test"></a>

*If you write a test, it's essential to follow the scripts/dev/EasyTest.js model.*



#### :one: Step 1 : variable name <a name="variable"></a>

The name of the .js test needs to be the same as the .txt script.
The **classNameString** is the name of your .txt and .js file. The class name also needs to be the same. 

The function **type** needs to be a string and the same name as the folder. It's essential because the path is related to it.

```
let type = "dev";
let classNameString = "EasyTest";
let scriptPath = `./scripts/${type}/${classNameString}.txt`; 

class EasyTest {
  constructor(type, classNameString, scriptPath) {
```

As you can see, each function has its class. In this class, you can find all tests for a single script. 



#### :two: Step 2: write your tests <a name="write"></a>

The test follows the arrange, act, assert pattern. 

```
  testNombreEntier(scriptPath, detail) {
    // arrange
    const docData = { test1: "2", test2: "3" };
    // act
    tstf.transformScriptToFunction(scriptPath, docData, detail);
    // assert
    af.assertFunction(tstf.result[0], 5);
  }

```

- The title of each test needs to **start with "test"**, be clear, and be as precise as possible.
- You need to **change the docData** depending on the information required in the script function. 
- The **wanted result** needs to be written in the second argument of assertFunction(). 

In this example, our docData is { test1: "2", test2: "3" } and we want to assert if the result is 5. 



#### :three: Step 3 : runTests() <a name="runtest"></a>

Finally, it's important to change the name of the class in rt.runTests() with the class name:
```
rt.runTests(EasyTest, type, classNameString, scriptPath, detail);
```

That's it! You should be able to run the test that you just wrote in CLI running **runTests.js**! :rainbow:



### :construction: Project status <a name="statut"></a>
This project is in progress 
