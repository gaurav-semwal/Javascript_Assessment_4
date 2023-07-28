# Question No.1 How does the JS engine work?

* Explanation => The JavaScript engine is a program that interprets and executes JavaScript code. It is an essential component of web browsers and server-side JavaScript environments. Here is the explanation that how the JS engine works.
  
`Parser` - The source code is sent to a decoder which decodes the contents inside the HTML script tag into tokens that are sent to the parser. The engine tries to avoid parsing code that’s not necessary right away in order to save time.

`AST` - The parser creates nodes based on the tokens it receives. With these nodes, it creates an Abstract Syntax Tree (AST).

`Interpreter` - It generates byte code, by reading the code line by line. Once the byte code is generated, the AST is deleted and memory space is cleared up.

`Profiler` - Monitors and watches code to optimize it.

`Compiler` - Works ahead of time and creates a translation of the code that has been written and compiles it down to a lower level language that machines can read.

`Optimized code` - Code needs to be optimized to be run rapid. 

# Question No.2   What is the output & Why?
let timerId = setInterval(function () {    
alert("tick");                                       
}, 2000);                                    
setTimeout(function () {                     
clearInterval(timerId);                    
alert("stop");                             
}, 5000);       
```js
Output ->     tick
              tick
              stop
```

* Explanation => Here in the above code, the setInterval function will repeat the given function
alert("tick") at a fixed interval(mean it will sets up a timer that goes "tick"
in every 2 seconds i.e 2000 milliseconds).The timer will keeps going until 5
seconds (5000 miliseconds) have passed. The clearInterval function inside the
setTimeout function will stop the repeating alerts of "tick" from displaying
after the 5 seconds mark (i.e after 5 seconds, the timer will stopped, and we
will see a final message saying "stop")

# Question No.3 Write printAnimals() in such a way that it prints all animals in the object below.
```js
const animals = [
  { species: "Lion", name: "King" },
  { species: "Whale", name: "Queen" },
];

function printAnimals() {
  for (let i in animals) {
    const animal = animals[i];
    console.log("#" + i + " " + animal.species + ": " + animal.name);
  }
}
printAnimals.call(animals);
```
* Explanation => In this code we have called animals containig two objects. Now inside the printAnimals function we have a for in loop(we used this for iterating over object property).In each iteration of the for in loop, the variable i will take the value of the current index.The console.log() inside the loop construct a string to print information about each animal. It uses the i (index), animal.species, and animal.name property to build the string and the console.log() will print each animal information to the console. Atlast, printAnimals.call(animals); is used to call the printAnimals function.

# Question No.4 What is the output & Why?
```js
 function sumOfNumbers() {
var total = 0;
for (var i = 0; i < arguments.length; i++) {
total += arguments[i];
}
return total;
}
var numbers = [1, 2, 3]; 
var sum = sumOfNumbers.apply(null, numbers);
console.log(sum);
```
*Explanation => Here in above code the function sumOfNumber will calculate the total sum of any number of arguments it receives. Then, the apply method here is used to call the sumOfnumbers functions with its elemets of numbers array as its arguments, and inside the sumOfnumber function it will add all the arguments which is variable numbers and will calculate the total sum(i.e "1+2+3 = 6"). And at last the function returns the total sum which is stored in the sum variable and the console.log(sum) will execute it and will print "6" in the output.

# Question No.5 What is the output & Why?
```js
var person = {
name : "Jack",
prop : { name : "Daniel",
getName : function() {
return this.name;}}}
var name = person.prop.getName.bind(person);
console.log(name());
var  name = person.prop.getName();
console.log(name);
```
* Explanation => Here we have an object person with a property prop which is also an object containing a method getName() which will return the name of its parent object. Then, we use the bind method to create a new function name which is copy of getName function. When we call name(), it will execute the getName function and as the getName function is pointing to parent so it will return the value of person.name ("Jack").
Now in this -> person.prop.getName() we are directly calling this and storing in name variable. and last when we log the the name , it print the value of person.prop.getName(), which is "Daniel".

# Question No.6 What is the output & Why?
```js
function makeUser() 
{ return { name: "John", ref: this };
} 
let user = makeUser(); 
alert( user.ref.name );
```
* Explanation => Here the function makeUser() is returning the object. And the user variable is assigned for calling the makeUser() function. When the function is called then the this keyword inside the function is pointing to global object. Now the global object does not have a name property, so when we call the user.ref.name it return undefined in output.
  
# Question No.7 What is the output & Why?
const func = (function(a){ delete a; return a; })(5); console.log(func);
```js
const func = (function (a) {
  delete a;
  return a;
})
(5);
console.log(func);
```
* Explanation => Here inside the function the argument a is received. the line delete(a) will delete the variable a but we can not delete function arguments or variable when it is declared with const, so this line will not proceed. Now on the next line the function returns the value of a, which is 5. Finally the console.log(func) will execute and will print 5 in the output as 5 is stored in the func variable.

# Question No.8 Create an object `calculator` with three methods: - `read()` prompts for two values and saves them as object properties with names `a` and `b` respectively. - `sum()` returns the sum of saved values. - `mul()` multiplies saved values and returns the result.
 ``` js
const calculator = {
  read: function() {
        a = prompt("Enter the first number:");
        b = prompt("Enter the second number:");
  },
  sum: function() {
    return +a + + b;
  },
  mul: function() {
    return a*b;
  }
};
calculator.read();       

const Add = calculator.sum();
console.log("Sum is:", Add);

const Multiply = calculator.mul();
console.log("Multiplication:", Multiply);
```

# Question No.9 What is scope chain and lexical scoping in JS?
* Explanation => `Scope Chain` = When a variable is used in JavaScript, the JavaScript engine will try to find
the variable’s value in the current scope and if it could not find the variable, it
will look into the outer scope and will continue to do so until it find the
variable or reaches global scope. If it's still could not find the variable it
will declare the variable in the global scope or return an error.
  Example :
  ```js

  var sem = "rav";
            function app() {
            var wal = "Gau";
            console.log(wal);
            console.log(sem);
            number = 23;
            console.log(number);
            }
            app();
  ```
`Lexical Scoping` = In a nested group of functions, accessing the variables which are declared
outside the function call is lexical scoping. In simple words, JavaScript looks for variables 
in a way, if it can’t find a variable in its local Execution Context, it will look for it in its calling
context. And if not found in its calling context. Repeatedly, until it is
looking in the global execution context. And if it does not find then, it’s
undefined. Example :  
```js
                      const x = 3;
                      function f() {
                      console.log(x);
                      console.log(y);}
                      const y = 3;
                      f();

```

# Question No.10 What is FEC & GEC? How are Execution Contexts Created?
* Explanation => FEC stands for Functional Execution Context.
Functional Execution Code is type of context which is created by the
JavaScript engine when any function call is found. Every function has its own
execution context, unlike Global Execution Context the Functional Execution Context can be more than one.
Also, Functional Execution Context can access the entire code of the Global Execution Context, but it is not possible for global to access
all the code of the functional. So during the Gl;obal code execution a function call is initiate
and later when it found by the JS Engine it create new function for that specific function.

* GEC stands for Global Execution Context.
The Global Execution Context represents the environment in which global level
JavaScript code runs. It is created when the JavaScript program starts executing
and is always present through out the entire runtime of the program. In a web
browser, the Global Execution Context includes global variables and functions
defined in the global scope and the reference to the global object.

# Creation of Global Execution Context
When JavaScript code is executed, the JavaScript engine creates a new execution context for each function
call and a global execution context for the top of the code. 
# The context is created in two phases :
* Creation Phase :  In this phase, the JavaScript engine creates the execution context and sets up
  the script's environment. It consider the values of variables and functions and sets up the scope chain for the execution context.
* Execution Phase : During the execution phase, the JavaScript engine executes the code line by line and 
  assigns the values to variables, and executes the function calls.

  # Question No.11 Write a JavaScript program to create a clock.
      `JS CODE FOR CLOCK :`
  ```js
  function displayclock() {
  let date = new Date();
  let hrs = date.getHours();
  let mins = date.getMinutes();
  let secs = date.getSeconds();
  let time = `${hrs}:${mins}:${secs}`
  console.log(time) }
  displayclock();
  
  ```
  # Question No.12 Make the following code work [1, 2, 3, 4, 5, 6] .shuffle();
  *Code :
  ```js
            Array.prototype.shuffle = function() {
            for (let i = this.length - 1; i > 0; i--) {
              const j = Math.floor(Math.random() * (i + 1));
              [this[i], this[j]] = [this[j], this[i]];
            }
            return this;
          };
          const array = [1, 2, 3, 4, 5, 6];
          array.shuffle();
          console.log(array);
```


                   


    

