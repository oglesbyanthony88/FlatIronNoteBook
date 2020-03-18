## ES6

* **Destructuring**
	* Creating variables from objects and arrays.
	* Creating Objects with same-variable-name key value pairs.

* **Spread Operator**
	* How and why we use it.
	* Immutability principle.
	
* **Arrow Functions**
	* writing arrow functions and seeing them in diffrent contexts.
	
* **Class Syntax**
	* Transition back into Object Oriented programming from functional.
	* Defining class and instance methods.
	* Creating Instances.
	* The `this` keyword.
	
### Destructuring

**Destructuring of Arrays**

```javascript
let teacherArray = ["Chris", "Jenn", "Cernan"]

// Instead of 

let chris = teacherArray[0]
let jenn = teacherArray[1]
let cernan = teacherArray[2]

// use Destructuring

let [chris, jenn, cernan] = TeacherArray

```

**Destructuring Objects**

```javascript
let studentObj = {name: "Chris", grade: 12, canGraduate: true}

// same as array destructuring

let {name, grade, canGraduate} = studentObj

// the variable we create for an object need to be the same as the keys.

```

**Examples**

```javascript

function studentHTML([name, grade, canGraduate]){
document.body.innerHTML += `
<div>
	<p>Student Name: ${studentObj.name}</p>
	<p>Student Grade: ${studentObj.grade}</p>
	<p>Student Can Graduate: ${studentObj.canGraduate}</p>
</div>
`
}

```

```javascript

let name = "Chris"
let password = "test"

let configObj = {
	method: "POST",
	headers: '',
	body: JSON.stringify({
		name,
		password
	})
}

```

## Spread Operator

* All changes to Arrays and Objects should yield copies.


```javascript

let newStudentObj = {...studentObj, honors: false}

//this create a newStudentObj but keeps studentObj saved. this code also adds a new key HONORS with a value of false.

let newTeacherArray = [...teacherArray, "Ashlee"]

// This works the same as objects, however with arrays you would use brackets.

```

**Example**

```javascript

let state = {
	loggedInUser: null,
	toys: []
}

state = {...state, loggedInUser: chris}

state = { ...state, toys: ["Woody", "Buzz"]}

// This code creates a state with loggedInUser, and toys. The next two lines creates a state with these atrributes and adds in chris as the value for loggedInUser and also adds a few toys to the toys array.

```

## Arrow Functions

* Always inherently anonymous.

```javascript

// arrow

const add2 = num => num + 2

{} => {}

// regular

function add2(num) {
	return num + 2
}

{} => {}

// most commonly used in fetches

fetch("")
// regular
	// .then(function(res){
	//	return res.json
	// })
// vs. arrow	
	.then(res => res.json())
	
```

* There are times where you must us an arrow, and times when you must use a regular function.
* They are not always interchangeable.

## Class Syntax

* To define a class

```javascript

class Pet{
	constructor(name, age){
	// Constructor takes in arguments to create instances of a class.
	// The constructor works like a setter and getter method.
	
	this.name = name
	this.age = age
	
	// This works alot like Ruby's self.
	}
	
	// To manually create a setter.
	
	set owner(owner){
	this.owner = owner
	}
	
	// To manually create a getter.
	
	get owner(){
	return this.owner
	}
}

```


* To create instance methods within a class:

```javascript

class Pet{
	constructor(name, age){
	
	this.name = name
	this.age = age
	}
	
	// An example instance method
	sayName(){
	console.log("Hi, my name is " + this.name)
	}
}

```

* Inheritance

```javascript

class Dog extends Pet{
	constructor(name, age, breed, favToy){
		super(name, age)
		
		//If a class inherits from another class use the word super to pass in the variable from the inherited class.
		
		this.breed = breed
		this.favToy = favToy
		
		}
}

```

* A class that inherite from another class also inherits that classes instance methods as well.

* Arrow Functions and Classes

```javascript

class Dog extends Pet{
	constructor(name, age, breed, favToy){
		super(name, age)
		
		this.breed = breed
		this.favToy = favToy
		}
		
		havePuppy(name){
			let puppy = new Dog(name, 0, this.breed, null)
			
			puppy.whoIsMom = () => {console.log("My mom is " + this.name)}
			
			return puppy
			
		}
		
}

```

Arrow functions will bind the `this` keyword to the parent function.

**Video:** https://www.youtube.com/watch?v=a6FewRfi6cI&feature=youtu.be