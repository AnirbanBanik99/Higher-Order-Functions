# Higher-Order-Functions
Map, Filter and Reduce function's documentation.


What is Javascript?

JavaScript, often abbreviated as JS, is a programming language that conforms to the 
ECMAScript specification. JavaScript is high-level, often just-in-time compiled, and 
multi-paradigm. It has curly-bracket syntax, dynamic typing, prototype-based 
object-orientation, and first-class functions



What's Higher Order Function?

In Javascript, functions can be assigned to variables in the same way that strings 
or arrays can. They can be passed into other functions as parameters or returned 
from them as well. A “higher-order function” is a function that accepts functions as 
parameters and/or returns a function.
eg:- map, sort, reduce, filter, forEach, etc.

           Today, we are goin to understand the most popularly used three higher order functions,
namely Map, Filter and Reduce.
--------------------------------------------------------------------------------------------------------------------


Map 

The map() method in Javascript is used for creating a new array from an 
existing one, applying a function to each one of the elements of the 
first array.

Syntax :
	var new_array = arr.map(function callback(element, index, array) {
   	 // Return value for new_array
	}[, thisArg])

or
        var officers = [
	  { id: 1, name: 'Anirban Banik' },
	  { id: 2, name: 'Ramu Pal' },
	  { id: 3, name: 'Abhishek Das' },
	  { id: 4, name: 'Raj Singh' }
	];

	const officersIds = officers.map(officer => officer.id);


Basically, it takes 2 arguments, a callback and an optional context, which I 
did not use in the previous example. The callback runs for each value in the 
array and returns each new value in the resulting array.

Example
In the following example, each number in an array is halved.

const numbers = [2, 3, 4, 5];
const halved = numbers.map(item => item / 2);
console.log(halved); // [4, 6, 8, 10]

----------------------------------------------------------------------------------------------------------------------
Filter

The filter() method in Javascript takes each element in an array and it 
applies a conditional statement against it. If this conditional returns 
true, the element gets pushed to the output array. If the condition 
returns false, the element does not get pushed to the output array.

Syntax :
	var new_array = arr.filter(function callback(element, index, array) {
	    // Return true or false
	}[, thisArg])

The syntax for filter is similar to map, except the callback function should return 
true to keep the element, or false otherwise. In the callback, only the element is 
required.

Examples
In the following example, odd numbers are "filtered" out, leaving only even numbers.

1. 
const numbers = [2, 3, 4, 5];
const evens = numbers.filter(item => item % 2 === 0);
console.log(evens); // [2, 4]

2. 
const students = [
  { name: 'Rahul', grade: 92 },
  { name: 'Mohan', grade: 89 },
  { name: 'Raj', grade: 96 },
  { name: 'Sameer', grade: 75 },
  { name: 'Karan', grade: 91 }
];

const studentGrades = students.filter(student => student.grade >= 90);
return studentGrades; // [ { name: 'Rahul', grade: 96 }, 
			   { name: 'Raj', grade: 100 }, 
			   { name: 'Karan', grade: 90 } ]
------------------------------------------------------------------------------------------------------------------------
Reduce

The reduce() method in Javascript reduces an array of values down to just
one value. To get the output value, it runs a reducer function on each 
element of the array.Just like .map(), .reduce() also runs a callback for each 
element of an array. What’s different here is that reduce passes the result of this 
callback (the accumulator) from one array element to the other.
The accumulator can be pretty much anything (integer, string, object, etc.) and must 
be instantiated or passed when calling .reduce().

Syntax :
	arr.reduce(callback[, initialValue])

The callback argument is a function that will be called once for every item in the 
array. This function takes four arguments, but often only the first two are used.

1.accumulator - the returned value of the previous iteration
2.currentValue - the current item in the array
3.index - the index of the current item
4.array - the original array on which reduce was called
5.The initialValue argument is optional. If provided, it will be used as the initial 
accumulator value in the first call to the callback function.

Examples
1.
The following example adds every number together in an array of numbers.

const numbers = [1, 2, 3, 4];
const sum = numbers.reduce(function (result, item) {
  return result + item;
}, 0);
console.log(sum); // 10

2.
Say, We have an array with these pilots and their respective years of experience,

var pilots = [
  {
    id: 10,
    name: "Poe Dameron",
    years: 14,
  },
  {
    id: 2,
    name: "Temmin 'Snap' Wexley",
    years: 30,
  },
  {
    id: 41,
    name: "Tallissan Lintra",
    years: 16,
  },
  {
    id: 99,
    name: "Ello Asty",
    years: 22,
  }
];

a.
Now, to know the total years of experience of all of them. With .reduce(), it’s 
pretty straightforward:

var totalYears = pilots.reduce(function (accumulator, pilot) {
  return accumulator + pilot.years;
}, 0);

or this can be shortened with ES6’s arrow functions:
const totalYears = pilots.reduce((acc, pilot) => acc + pilot.years, 0);

Notice that I’ve set the starting value as 0. I could have also used an existing 
variable if necessary. After running the callback for each element of the array, 
reduce will return the final value of our accumulator (in our case: 82).

b.
Now, to find which pilot is the most experienced one. For that, We can use reduce as 
well:

var mostExpPilot = pilots.reduce(function (oldest, pilot) {
  return (oldest.years || 0) > pilot.years ? oldest : pilot;
}, {});

We named my accumulator oldest. Our callback compares the accumulator to each pilot. 
If a pilot has more years of experience than oldest, then that pilot becomes the new 
oldest so that’s the one we return.
As you can see, using .reduce() is an easy way to generate a single value or object 
from an array.


3.
In this example, reduce() is used to transform an array of strings into a single 
object that shows how many times each string appears in the array. Notice this call 
to reduce passes an empty object {} as the initialValue parameter. This will be used 
as the initial value of the accumulator (the first argument) passed to the callback 
function.

var pets = ['dog', 'chicken', 'cat', 'dog', 'chicken', 'chicken', 'rabbit'];

var petCounts = pets.reduce(function(obj, pet){
    if (!obj[pet]) {
        obj[pet] = 1;
    } else {
        obj[pet]++;
    }
    return obj;
}, {});

console.log(petCounts); 

//
Output:
 { 
    dog: 2, 
    chicken: 3, 
    cat: 1, 
    rabbit: 1 
 }
 


We can also chain them up to get our desired output.
Suppose, we have an array with individual's firstname, lastname, and age.

const users = [
{ firstName: "Anirban", lastName: "Banik", age: "22"},
{ firstName: "Abhishek", lastName: "Das", age: "23"},
{ firstName: "Arthav", lastName: "Mishra", age: "33"},
{ firstName: "Rahul", lastName: "Sen", age: "22"},
 ]

And suppose we want to print the firstname of users, whose age is less than 30.

const output =
users.filter((x) => x.age < 30)
.map((x) => x.firstName);

//
Output:
 ["Anirban","Abhishek","Rahul"]
 
 That's all about the map, Reduce and Filter.
