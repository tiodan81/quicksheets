#Methods
 	
A method is a function that is associated with an object. It can be declared inside an object literal or later, outside the object.

When you call the method, include the object name: `objectName.methodName();`

```javascript
//DECLARE a method inside the object
var myObject = {
	firstName: 'Dan',
	lastName: 'Schwartz',
	 //here's our method. inside the method, 
	 //'this' refers to the object itself - myObject
	myMethod: function() {
		console.log(this.firstName + ' ' + this.lastName);
	}  
}	

//CALL the method
myObject.myMethod();  //logs 'Dan Schwartz' to the browser console.

//DECLARE another property
myObject.age = 'old';

//DECLARE another method outside the object:
myObject.anotherMethod = function() {
	return this.age;
}

//CALL the new method and save the result to a new variable
//after this call, danAge will equal 'old'
var danAge = myObject.anotherMethod();
```	