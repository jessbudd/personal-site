---
title: Nothin' to see here folks!
layout: layouts/blank.njk
date: 2020-12-19
meta: practice makes progress
# tags: exercises
# img: https://jessbudd.com/images/featured/quoteGenerator.png
# excerpt:
---

<h1>{{title}}</h1>
<script>
    const toppings = ['Mushrooms ', 'Tomatoes', 'Eggs', 'Chili', 'Lettuce', 'Avocado', 'Chiles', 'Bacon', 'Pickles', 'Onions', 'Cheese'];
    const students = [
      {
        id: '11ce',
        first_name: 'Dall',
        last_name: 'Puckring',
      },
      {
        id: '2958',
        first_name: 'Margarete',
        last_name: 'Brandi',
      },
      {
        id: '565a',
        first_name: 'Bendicty',
        last_name: 'Woodage',
      },
      {
        id: '3a16',
        first_name: 'Micki',
        last_name: 'Mattes',
      },
      {
        id: 'f396',
        first_name: 'Flory',
        last_name: 'Gladeche',
      },
      {
        id: 'de5f',
        first_name: 'Jamill',
        last_name: 'Emilien',
      },
      {
        id: '54cb',
        first_name: 'Brett',
        last_name: 'Aizikowitz',
      },
      {
        id: '9135',
        first_name: 'Lorry',
        last_name: 'Smallman',
      },
      {
        id: '978f',
        first_name: 'Gilly',
        last_name: 'Flott',
      },
    ];
    const people = [
      {
        birthday: 'April 22, 1993',
        names: {
          first: 'Keith',
          last: 'Buckley'
        }
      },
      {
        birthday: 'January 3, 1975',
        names: {
          first: 'Larry',
          last: 'Heep'
        }
      },
      {
        birthday: 'February 12, 1944',
        names: {
          first: 'Linda',
          last: 'Bermeer'
        }
      }
    ];
    const buns = ['egg', 'wonder', 'brioche'];
    const meats = {
      beyond: 10,
      beef: 5,
      pork: 7
    };
    const prices = {
      hotDog: 453,
      burger: 765,
      sausage: 634,
      corn: 234,
    };
    const orderTotals = [342, 1002, 523, 34, 634, 854, 1644, 2222];
    const feedback = [
      { comment: 'Love the burgs', rating: 4 },
      { comment: 'Horrible Service', rating: 2 },
      { comment: 'Smoothies are great, liked the burger too', rating: 5 },
      { comment: 'Ambiance needs work', rating: 3 },
      { comment: 'I DONT LIKE BURGERS', rating: 1 },
    ];
    const faces = ['😃', '🤠', '🤡', '🤑', '😵', '🌞', '🐶', '😺'];
    const inventory = [
      { type: 'shirt', price: 4000 },
      { type: 'pants', price: 4532 },
      { type: 'socks', price: 234 },
      { type: 'shirt', price: 2343 },
      { type: 'pants', price: 2343 },
      { type: 'socks', price: 542 },
      { type: 'pants', price: 123 },
    ];
    /*
    Looping Methods
    */
    // for each
    function logTopping(topping, index, originalArray) {
    const nextTopping = originalArray[index + 1];
    const prevTopping = originalArray[index - 1];
        //    log the topping
        console.log(topping);
        //    log the prev topping if there is one
        prevTopping ? console.log(prevTopping) : null
        // log the next topping if there is one
        nextTopping ? console.log(nextTopping) : 'goodbye'
        // if its the last item say goodbye
        console.log('---------');
    }
    toppings.forEach(logTopping);
    // Map, Filter, Reduce
    console.clear();
    // map - immutable
    function addArms(face) {
        return ` 👋 ${face} 👋 `;
    }
    console.log(addArms( '🦕' ));
    //
    const toys = faces.map(addArms);
    console.log('Array.map(addArms)', toys);
    //
    const fullNames = ['nathan', 'jess', 'alyssa', 'summer'].map( name => `${name} Budd`);
    console.log('Array.map() anon arrow function', fullNames);
    //
    function Buddify(name) {
        return `${name} Budd`;
    }
    function capitalise(word) {
        return `${word[0].toUpperCase()}${word.slice(1)}`
    }
    console.log(`Array.map(capitalise fn).map(Buddify fn)`, fullNames.map(capitalise).map(Buddify))
    //
    const cleanPeople = people.map( function(person) {
        // console.log(person);
        // get their birthday timestamp
        const birthday = new Date(person.birthday).getTime();
        // now timestamp
        const now = Date.now();
        // figure out how old they are
        const age = Math.floor((now - birthday) / 31536000000);
        // return full name and age in object
        const fullName = `${person.names.first} ${person.names.last}`;
        return object = {
            fullName: fullName,
            age, // because value name is same as key name
        }
    })
    console.table(cleanPeople);
    //
    // library for working with dates https://date-fns.org/
    // site to convert timestamps https://epoch.now.sh/
    //
    // filter - immutable
    function isOver40(person) {
        return person.age > 40;
    }
    const over40 = cleanPeople.filter(isOver40);
    console.log('structured cleanPeople.filter()', over40);
    //
    //destrcutured version
    const cleanPeopleFiltered = cleanPeople.filter( ({ age }) => age > 40  );  
    console.log('destructured cleanPeople.filter()', cleanPeopleFiltered);
    //
    // find - immutable
    // const student = students.find( stud => stud.id === '565a');
    // higher order function is a function within a function
    function findById(id) {
        return function isStudent(student) {
            return student.id === id;
        }
    }
    // more generic extensible fn
    function findByProp(prop, propWeAreLookingFor) {
        return function(array) {
            return array[prop] === propWeAreLookingFor;
        }
    }
    const student = students.find(findById('565a'));
    const student2 = students.find(findByProp('first_name', 'Lorry'));
    console.log('find()', student2);
    console.log('find(findById(param)) using Higher Order Function' , student);
    console.clear();
    //
    // 
    // reduce!
    function tallyNumbers(tally, currentTotal) {
        console.log(`The current tally is ${tally}`);
        console.log(`The current total is ${currentTotal}`);
        console.log('----');
        return tally + currentTotal;
    }
    const allOrders = orderTotals.reduce(tallyNumbers, 0);
//
//
function inventoryReducer(totals, item) {
    console.log(`looping over ${item.type}`);
    // increment the type by 1
    totals[item.type] = totals[item.type] + 1 || 1;
    // totals.shirt ? totals[item.type] + 1 : totals[item.type] = 1 
    // return the totals so the next loop can use it
    console.log(totals);
    return totals;
}
// get the total inventory
const inventoryCounts = inventory.reduce(inventoryReducer, {})
console.log('Array.reduce(namedFunction, {empty object})', inventoryCounts);
//
// get the total inventory price
const totalInventoryPrice = inventory.reduce((accumulator, item) => accumulator + item.price, 0);
console.log(totalInventoryPrice);
//
//
const text = `Skip to main content
Skip to search
Technologies
References & Guides
Feedback
Search MDN
Search MDN
Sign in
Array.prototype.reduce()
Web technology for developers
JavaScript
JavaScript reference
Standard built-in objects
Array
Array.prototype.reduce()
Select your preferred language
English (US)
 Change language
Jump to section
Syntax
Description
Polyfill
Examples
Specifications
Browser compatibility
See also
The reduce() method executes a reducer function (that you provide) on each element of the array, resulting in single output value.
The reducer function takes four arguments:
Accumulator
Current Value
Current Index
Source Array
Your reducer function's returned value is assigned to the accumulator, whose value is remembered across each iteration throughout the array, and ultimately becomes the final, single resulting value.
Syntax
arr.reduce(callback( accumulator, currentValue, [, index[, array]] )[, initialValue])
Parameters
callback
A function to execute on each element in the array (except for the first, if no initialValue is supplied).
It takes four arguments:
accumulator
The accumulator accumulates callback's return values. It is the accumulated value previously returned in the last invocation of the callback—or initialValue, if it was supplied (see below).
currentValue
The current element being processed in the array.
index Optional
The index of the current element being processed in the array. Starts from index 0 if an initialValue is provided. Otherwise, it starts from index 1.
array Optional
The array reduce() was called upon.
initialValue Optional
A value to use as the first argument to the first call of the callback. If no initialValue is supplied, the first element in the array will be used as the initial accumulator value and skipped as currentValue. Calling reduce() on an empty array without an initialValue will throw a TypeError.
Return value
The single value that results from the reduction.
Description
The reduce() method executes the callback once for each assigned value present in the array, taking four arguments:
accumulator
currentValue
currentIndex
array
The first time the callback is called, accumulator and currentValue can be one of two values. If initialValue is provided in the call to reduce(), then accumulator will be equal to initialValue, and currentValue will be equal to the first value in the array. If no initialValue is provided, then accumulator will be equal to the first value in the array, and currentValue will be equal to the second.
Note: If initialValue is not provided, reduce() will execute the callback function starting at index 1, skipping the first index. If initialValue is provided, it will start at index 0.
If the array is empty and no initialValue is provided, TypeError will be thrown.
If the array only has one element (regardless of position) and no initialValue is provided, or if initialValue is provided but the array is empty, the solo value will be returned without calling callback.
It is almost always safer to provide an initialValue, because there can be up to four possible output types without initialValue, as shown in the following example:
let maxCallback = ( acc, cur ) => Math.max( acc.x, cur.x );
let maxCallback2 = ( max, cur ) => Math.max( max, cur );
// reduce without initialValue
[ { x: 2 }, { x: 22 }, { x: 42 } ].reduce( maxCallback ); // NaN
[ { x: 2 }, { x: 22 }            ].reduce( maxCallback ); // 22
[ { x: 2 }                       ].reduce( maxCallback ); // { x: 2 }
[                                ].reduce( maxCallback ); // TypeError
// map & reduce with initialValue; better solution, also works for empty or larger arrays
[ { x: 22 }, { x: 42 } ].map( el => el.x )
                        .reduce( maxCallback2, -Infinity );
How reduce() works
Suppose the following use of reduce() occurred:
[0, 1, 2, 3, 4].reduce(function(accumulator, currentValue, currentIndex, array) {
  return accumulator + currentValue
})
The callback would be invoked four times, with the arguments and return values in each call being as follows:
callback iteration	accumulator	currentValue	currentIndex	array	return value
first call	0	1	1	[0, 1, 2, 3, 4]	1
second call	1	2	2	[0, 1, 2, 3, 4]	3
third call	3	3	3	[0, 1, 2, 3, 4]	6
fourth call	6	4	4	[0, 1, 2, 3, 4]	10
The value returned by reduce() would be that of the last callback invocation (10).
You can also provide an Arrow Function instead of a full function. The code below will produce the same output as the code in the block above:
[0, 1, 2, 3, 4].reduce( (accumulator, currentValue, currentIndex, array) => accumulator + currentValue )
If you were to provide an initialValue as the second argument to reduce(), the result would look like this:
[0, 1, 2, 3, 4].reduce((accumulator, currentValue, currentIndex, array) => {
    return accumulator + currentValue
}, 10)
callback iteration	accumulator	currentValue	currentIndex	array	return value
first call	10	0	0	[0, 1, 2, 3, 4]	10
second call	10	1	1	[0, 1, 2, 3, 4]	11
third call	11	2	2	[0, 1, 2, 3, 4]	13
fourth call	13	3	3	[0, 1, 2, 3, 4]	16
fifth call	16	4	4	[0, 1, 2, 3, 4]	20
The value returned by reduce() in this case would be 20.
Polyfill
// Production steps of ECMA-262, Edition 5, 15.4.4.21
// Reference: https://es5.github.io/#x15.4.4.21
// https://tc39.github.io/ecma262/#sec-array.prototype.reduce
if (!Array.prototype.reduce) {
  Object.defineProperty(Array.prototype, 'reduce', {
    value: function(callback /*, initialValue*/) {
      if (this === null) {
        throw new TypeError( 'Array.prototype.reduce ' +
          'called on null or undefined' );
      }
      if (typeof callback !== 'function') {
        throw new TypeError( callback +
          ' is not a function');
      }
      // 1. Let O be ? ToObject(this value).
      var o = Object(this);
      // 2. Let len be ? ToLength(? Get(O, "length")).
      var len = o.length >>> 0;
      // Steps 3, 4, 5, 6, 7
      var k = 0;
      var value;
      if (arguments.length >= 2) {
        value = arguments[1];
      } else {
        while (k < len && !(k in o)) {
          k++;
        }
        // 3. If len is 0 and initialValue is not present,
        //    throw a TypeError exception.
        if (k >= len) {
          throw new TypeError( 'Reduce of empty array ' +
            'with no initial value' );
        }
        value = o[k++];
      }
      // 8. Repeat, while k < len
      while (k < len) {
        // a. Let Pk be ! ToString(k).
        // b. Let kPresent be ? HasProperty(O, Pk).
        // c. If kPresent is true, then
        //    i.  Let kValue be ? Get(O, Pk).
        //    ii. Let accumulator be ? Call(
        //          callbackfn, undefined,
        //          « accumulator, kValue, k, O »).
        if (k in o) {
          value = callback(value, o[k], k, o);
        }
        // d. Increase k by 1.
        k++;
      }
      // 9. Return accumulator.
      return value;
    }
  });
}
Caution: If you need to support truly obsolete JavaScript engines that do not support Object.defineProperty(), it is best not to polyfill Array.prototype methods at all, as you cannot make them non-enumerable.
Examples
Sum all the values of an array
let sum = [0, 1, 2, 3].reduce(function (accumulator, currentValue) {
  return accumulator + currentValue
}, 0)
// sum is 6
Alternatively written with an arrow function:
let total = [ 0, 1, 2, 3 ].reduce(
  ( accumulator, currentValue ) => accumulator + currentValue,
  0
)
Sum of values in an object array
To sum up the values contained in an array of objects, you must supply an initialValue, so that each item passes through your function.
let initialValue = 0
let sum = [{x: 1}, {x: 2}, {x: 3}].reduce(function (accumulator, currentValue) {
    return accumulator + currentValue.x
}, initialValue)
console.log(sum) // logs 6
Alternatively written with an arrow function:
let initialValue = 0
let sum = [{x: 1}, {x: 2}, {x: 3}].reduce(
    (accumulator, currentValue) => accumulator + currentValue.x
    , initialValue
)
console.log(sum) // logs 6
Flatten an array of arrays
let flattened = [[0, 1], [2, 3], [4, 5]].reduce(
  function(accumulator, currentValue) {
    return accumulator.concat(currentValue)
  },
  []
)
// flattened is [0, 1, 2, 3, 4, 5]
Alternatively written with an arrow function:
let flattened = [[0, 1], [2, 3], [4, 5]].reduce(
  ( accumulator, currentValue ) => accumulator.concat(currentValue),
  []
)
Counting instances of values in an object
let names = ['Alice', 'Bob', 'Tiff', 'Bruce', 'Alice']
let countedNames = names.reduce(function (allNames, name) {
  if (name in allNames) {
    allNames[name]++
  }
  else {
    allNames[name] = 1
  }
  return allNames
}, {})
// countedNames is:
// { 'Alice': 2, 'Bob': 1, 'Tiff': 1, 'Bruce': 1 }
Grouping objects by a property
let people = [
  { name: 'Alice', age: 21 },
  { name: 'Max', age: 20 },
  { name: 'Jane', age: 20 }
];
function groupBy(objectArray, property) {
  return objectArray.reduce(function (acc, obj) {
    let key = obj[property]
    if (!acc[key]) {
      acc[key] = []
    }
    acc[key].push(obj)
    return acc
  }, {})
}
let groupedPeople = groupBy(people, 'age')
// groupedPeople is:
// {
//   20: [
//     { name: 'Max', age: 20 },
//     { name: 'Jane', age: 20 }
//   ],
//   21: [{ name: 'Alice', age: 21 }]
// }
Bonding arrays contained in an array of objects using the spread operator and initialValue
// friends - an array of objects
// where object field "books" is a list of favorite books
let friends = [{
  name: 'Anna',
  books: ['Bible', 'Harry Potter'],
  age: 21
}, {
  name: 'Bob',
  books: ['War and peace', 'Romeo and Juliet'],
  age: 26
}, {
  name: 'Alice',
  books: ['The Lord of the Rings', 'The Shining'],
  age: 18
}]
// allbooks - list which will contain all friends' books +
// additional list contained in initialValue
let allbooks = friends.reduce(function(accumulator, currentValue) {
  return [...accumulator, ...currentValue.books]
}, ['Alphabet'])
// allbooks = [
//   'Alphabet', 'Bible', 'Harry Potter', 'War and peace',
//   'Romeo and Juliet', 'The Lord of the Rings',
//   'The Shining'
// ]
Remove duplicate items in an array
Note: If you are using an environment compatible with Set and Array.from(), you could use let orderedArray = Array.from(new Set(myArray)) to get an array where duplicate items have been removed.
let myArray = ['a', 'b', 'a', 'b', 'c', 'e', 'e', 'c', 'd', 'd', 'd', 'd']
let myOrderedArray = myArray.reduce(function (accumulator, currentValue) {
  if (accumulator.indexOf(currentValue) === -1) {
    accumulator.push(currentValue)
  }
  return accumulator
}, [])
console.log(myOrderedArray)
Replace .filter().map() with .reduce()
Using Array.filter() then Array.map() traverses the array twice, but you can achieve the same effect while traversing only once with Array.reduce(), thereby being more efficient. (If you like for loops, you can filter and map while traversing once with Array.forEach()).
const numbers = [-5, 6, 2, 0,];
const doubledPositiveNumbers = numbers.reduce((accumulator, currentValue) => {
  if (currentValue > 0) {
    const doubled = currentValue * 2;
    accumulator.push(doubled);
  }
  return accumulator;
}, []);
console.log(doubledPositiveNumbers); // [12, 4]
Running Promises in Sequence
/**
 * Runs promises from array of functions that can return promises
 * in chained manner
 *
 * @param {array} arr - promise arr
 * @return {Object} promise object
 */
function runPromiseInSequence(arr, input) {
  return arr.reduce(
    (promiseChain, currentFunction) => promiseChain.then(currentFunction),
    Promise.resolve(input)
  )
}
// promise function 1
function p1(a) {
  return new Promise((resolve, reject) => {
    resolve(a * 5)
  })
}
// promise function 2
function p2(a) {
  return new Promise((resolve, reject) => {
    resolve(a * 2)
  })
}
// function 3  - will be wrapped in a resolved promise by .then()
function f3(a) {
 return a * 3
}
// promise function 4
function p4(a) {
  return new Promise((resolve, reject) => {
    resolve(a * 4)
  })
}
const promiseArr = [p1, p2, f3, p4]
runPromiseInSequence(promiseArr, 10)
  .then(console.log)   // 1200
Function composition enabling piping
// Building-blocks to use for composition
const double = x => x + x
const triple = x => 3 * x
const quadruple = x => 4 * x
// Function composition enabling pipe functionality
const pipe = (...functions) => input => functions.reduce(
    (acc, fn) => fn(acc),
    input
)
// Composed functions for multiplication of specific values
const multiply6 = pipe(double, triple)
const multiply9 = pipe(triple, triple)
const multiply16 = pipe(quadruple, quadruple)
const multiply24 = pipe(double, triple, quadruple)
// Usage
multiply6(6)   // 36
multiply9(9)   // 81
multiply16(16) // 256
multiply24(10) // 240
Write map using reduce
if (!Array.prototype.mapUsingReduce) {
  Array.prototype.mapUsingReduce = function(callback, thisArg) {
    return this.reduce(function(mappedArray, currentValue, index, array) {
      mappedArray[index] = callback.call(thisArg, currentValue, index, array)
      return mappedArray
    }, [])
  }
}
[1, 2, , 3].mapUsingReduce(
  (currentValue, index, array) => currentValue + index + array.length
) // [5, 7, , 10]
Specifications
Specification
ECMAScript (ECMA-262)
The definition of 'Array.prototype.reduce()' in that specification.
Browser compatibility
Report problems with this compatibility data on GitHub
desktop	mobile	server
Chrome	Edge	Firefox	Internet Explorer	Opera	Safari	WebView Android	Chrome Android	Firefox Android	Opera Android	iOS Safari	Samsung Internet	Node.js
reduce
Full support3	Full support12	Full support3	Full support9	Full support10.5	Full support5	Full support≤37	Full support18	Full support4	Full support14	Full support4	Full support1.0	Full support0.10.0
Legend
See also
Array.prototype.reduceRight()
Related Topics
Standard built-in objects
Array
Properties
Array.prototype[@@unscopables]
Array.prototype.length
Methods
Array.prototype[@@iterator]()
get Array[@@species]
Array.prototype.concat()
Array.prototype.copyWithin()
Array.prototype.entries()
Array.prototype.every()
Array.prototype.fill()
Array.prototype.filter()
Array.prototype.find()
Array.prototype.findIndex()
Array.prototype.flat()
Array.prototype.flatMap()
Array.prototype.forEach()
Array.from()
Array.prototype.includes()
Array.prototype.indexOf()
Array.isArray()
Array.prototype.join()
Array.prototype.keys()
Array.prototype.lastIndexOf()
Array.prototype.map()
Array.of()
Array.prototype.pop()
Array.prototype.push()
Array.prototype.reduce()
Array.prototype.reduceRight()
Array.prototype.reverse()
Array.prototype.shift()
Array.prototype.slice()
Array.prototype.some()
Array.prototype.sort()
Array.prototype.splice()
Array.prototype.toLocaleString()
Array.prototype.toSource()
Array.prototype.toString()
Array.prototype.unshift()
Array.prototype.values()
Inheritance:
Function
Properties
Function.arguments
Function.caller
Function.displayName
Function.length
Function.name
Methods
Function.prototype.apply()
Function.prototype.bind()
Function.prototype.call()
Function.prototype.toSource()
Function.prototype.toString()
Object
Properties
Object.prototype.constructor
Object.prototype.__proto__
Methods
Object.prototype.__defineGetter__()
Object.prototype.__defineSetter__()
Object.prototype.__lookupGetter__()
Object.prototype.__lookupSetter__()
Object.prototype.hasOwnProperty()
Object.prototype.isPrototypeOf()
Object.prototype.propertyIsEnumerable()
Object.setPrototypeOf()
Object.prototype.toLocaleString()
Object.prototype.toSource()
Object.prototype.toString()
Object.prototype.valueOf()
Found a problem with this page?
Source on GitHub
Report a problem with this content on GitHub
Want to fix the problem yourself? See our Contribution guide.
Last modified: Dec 22, 2020, by MDN contributors
Web Technologies
Learn Web Development
About MDN
Feedback
About
MDN Web Docs Store
Contact Us
Firefox
MDN
Mozilla
© 2005-2020 Mozilla and individual contributors. Content is available under these licenses.
Terms
Privacy
Cookies`
//
// task: count how many times each letter and number occurs
// 1. convert text into array of letters
// 2. filter out anything thats not a letter or number
// 3. remove capitalisation discrepancies
// 4. count  number of instances
// 5. Find most popular letter
//
function isValidChar(char) {
    return char.match(/[a-z0-9]/i); 
} 
function lowerCase(str) {
    return str.toLowerCase();
}
// arrow function version
// const lowercase = char => char.toLowercase();
function instanceCounter(count, char) {
    count[char] 
    ? count[char] = count[char] + 1 
    : count[char] = 1 ;
    return count;
}
function compareNumbers(a, b) {
  return a[1] - b[1];
}
//
const result = text
    .split('') // same as [...str]
    .filter(isValidChar)
    .map(lowerCase)
    .reduce(instanceCounter, {})
console.log(result);
//
const sortedResult = Object.entries(result)
.sort(compareNumbers);
// return the most used character and value
const lastResult = sortedResult[sortedResult.length - 1];
console.log(lastResult);
console.clear();
//
const numbers = [2, 34, 3, 23, 42, 3, 1, 65, 364, 5, 645, 6];
const name = 'Jess Budd 👨‍👨‍👦‍👦 🇦🇺';
//
const wes = [
    {
    name: 'wes',
    id: 2,
},
    name: 'judy',
    id: 3,
    }
    ];
//
// For
for (let i = 0; i <= numbers.length; i += 2 ) {
    console.log('for loop', numbers[i]);    
}
// For of
// use for strings, similar to spread or split
// can (generally) parse emojis in strings
// handy for sequencing promises and use with await
for (const letter of name) {
    console.log('for of loop', letter);
}
for (const number of numbers) {
    console.log('for of loop', number);
}
// For in
// used to loop over the keys of an object
// usually prefer to use object.Entries method
// for (const prop in wes) {
//     console.log(prop)
// }
//
// While Loop
//

</script>

<style>
    body {
        min-height: 100vh;
        display: grid;
        align-items: center;
        justify-items: center;
    }
    .container {
      text-align: center;
      margin: 20% auto;
    }
    
    </style>