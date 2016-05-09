# JavaScript Structure

1. Declare Global Variables
2. Declare Constructor functions - name should be capitalized!
3. Declare regular functions
4. Call functions 

```javascript
//declare global variables at the top of your file
var globalVariable1 = 'hello';
var globalVariable2 = [0, 1, 2];

//create an instance of PersonConstructor and save it to the sam variable
//note that we can do this before the constructor function declaration
var sam = new PersonConstructor('Sam', 'Hamm');
//now sam = { firstName: 'Sam', lastName: 'Hamm' }

//then put any object constructors
function PersonConstructor(first, last) {
	this.firstName = first;
	this.lastName = last;
}

//then put any prototype functions that go with the object constructor
//call this function on an instance of PersonConstructor
PersonConstructor.prototype.sayHello = function() {
	console.log('Hello, my name is ' + this.firstName);
}

//then put regular function declarations
function firstFunction(parameter) {
	console.log(parameter);
}

function secondFunction(myArray) {
	for (i = 0; i < myArray.length; i++) {
		console.log(myArray[i]);
	}
}

//finally, call your functions
firstFunction(globalVariable1);	
//logs 'hello'
secondFunction(globalVariable2);	
//logs  0
//		1
//		2
sam.sayHello();
//logs 'Hello, my name is Sam'