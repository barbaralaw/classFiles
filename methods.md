# Array methods to know!
All methods are good to know about, but the methods in this post are must-haves in any developer's arsenal.

```
// Variable for Array examples
const someNums = [0,1,2,3,4,5]
const cakes = [
  {flavor: 'Vanilla', stock: 3},
  {flavor: 'Red Velvet', stock: 2},
  {flavor: 'Chocolate', stock: 0},
  {flavor: 'Carrot', stock: 0}
]
const inLine = ['Bob', 'John', 'Leon', 'Machi', 'Simba']
let num = 3
```

##map()
Runs a function on each element of the array and returns a new array. Doesn't mutate the original array. Takes a callback as a parameter, runs that function on each element of the array in turn, returns the new array.

Time complexity is O(n).

###Examples
someNums.map(x => x + num) => [3,4,5,6,7,8]

cakes.map(x => x.flavor) => ['Vanilla', 'Red Velvet', 'Chocolate', 'Carrot']

inLine.map((x,i) => {
      return {name: x, place: i+1}
      }) => [{name:'Bob', place: 1}, {name:'John', place:2}, {name:'Leon', place:3}, {name:'Machi', place:4}, {name:'Simba', place:5}]


##reduce()
Runs a function on each element of the array and reduces that array to a single value. Takes a callback as a parameter, runs that function on each element of the array in turn, returns the single value. Optional starting value parameter, or else it uses the first element of the array as the starting value.

Time complexity is O(n).

###Examples
someNums.reduce((a,c)=> a + c, 0) => sum = 15

someNums.reduce((a,c)=> a * c) => mult = 0

inLine.reduce((a,c)=> a.concat(', '+c)) => names = "Bob, John, Leon, Machi, Simba"

##filter()
The filter() creates a new array with all elements from the initial array that pass a test function. Takes a test for each element as a callback function which returns true or false for each element. Optional index, array, and thisArg can be passed in.

Time complexity is O(n).

###Examples
someNums.filter(x => x > 3) => [4,5]
cakes.filter(x => x.stock > 0) => [{flavor: "Vanilla", stock: 3}, {flavor: "Red Velvet", stock: 2}]
inLine.filter((x,i) => i >= 2) => ['Leon', 'Machi', 'Simba']

##forEach()
The forEach() runs a function on each element of the array. Takes a callback function which accepts 1 to 3 arguments - element, optional index, optional array, optional thisArg. Returns undefined. Mutates original array if the function mutates.

Time complexity is dependent on the callback function's complexity. Complexity is at least O(n).

###Examples
cakes.forEach(x => x.stock++) => MUTATES cakes array to add 1 to each stock value (Resetting example to original values for this page)
inLine.forEach((x,i) => console.log(x, i)) => console logs names and indexes for each item in array. Doesn't mutate.
someNums.forEach((x,i,arr) => arr[i] = x*i) => MUTATES someNums to [0,1,4,9,16,25]

##sort()
The sort() sorts the elements of an array in place and returns the sorted array. It does mutate the array. Takes an optional compare function that defines the sort order, if it's left off it sorts the elements according to unicode point values (often with unwanted results)

Time complexity is O(n log(n)).

###Examples
someNums.sort((a,b)=>b-a) => [5,4,3,2,1] someNums is now mutated to this new order  (Resetting example to original values for this page)
cakes.sort((a,b)=>a.stock - b.stock) =>  cakes is now mutated to this new order     (Resetting example to original values for this page)
[
  {flavor: 'Chocolate', stock: 0},
  {flavor: 'Carrot', stock: 0},
  {flavor: 'Red Velvet', stock: 2},
  {flavor: 'Vanilla', stock: 3}
]
[5, 3, 2, 56, 3, 100, 10, 1].sort() => [1, 10, 100, 2, 3, 3, 5, 56] (might not be what you had expected)

## slice()
The slice() returns a shallow copy of a portion of an array into a new array from start to end, non-inclusive. Original is not mutated. Takes an optional start index and optional end index. Negative start is an offset from the end, if not provided treated as 0. If start is greater than index range of array, an empty array is returned. If negative end is used, it represents offset from end of array.

Time complexity is O(n).

###Examples
someNums.slice(num) => [3,4,5]
someNums.slice(-2) => [4,5]
someNums.slice(1,4) => [1,2,3]
someNums.slice(2, -3) => [2]

##pop()
The pop() removes the last element from an array and returns that element. It mutates and changes length of original array.

Time complexity is O(1).

###Examples
someNums.pop() => 5
someNums.pop() => 4 Can keep popping off    (Resetting example to original values for this page)
cakes.pop() => {flavor: "Carrot", stock: 0} (Resetting example to original values for this page)

##shift()
The shift() removes the first element of an array and returns that removed element. It mutates and changes length of original array.

Time complexity is O(1).

###Examples
someNums.shift() => 0
someNums.shift() => 1 Can keep shifting off (Resetting example to original values for this page)
cakes.shift() => {flavor: "Vanilla", stock: 3} (Resetting example to original values for this page)

##push()
The push() adds one or more elements to the end of an array and returns the new length of the array. It mutates the array. Elements should be comma separated.

Time complexity is O(1).

###Examples
someNums.push(23) => 7  (and someNums is now [0,1,2,3,4,5,23]) (Resetting example to original values for this page)
inLine.push("Bill", "Elon") => 7 (and inLine is now ['Bob', 'John', 'Leon', 'Machi', 'Simba', 'Bill', 'Elon']) (Resetting example to original values for this page)
someNums.push([1,2,3]) => 7 (someNums is now [0,1,2,3,4,5,[1,2,3]]) (Resetting example to original values for this page)

##unshift()
The unshift() adds one or more elements to the beginning of the array and returns the new length of the array. It mutates the array. Elements should be comma separated.

Time complexity is O(1).

###Examples
someNums.push(23) => 7  (and someNums is now [23,0,1,2,3,4,5]) (Resetting example to original values for this page)
inLine.push("Bill", "Elon") => 7 (and inLine is now ['Bill', 'Elon', 'Bob', 'John', 'Leon', 'Machi', 'Simba']) (Resetting example to original values for this page)
someNums.push([1,2,3]) => 7 (someNums is now [[1,2,3],0,1,2,3,4,5]) (Resetting example to original values for this page)

##includes()
The includes() determines whether an array includes a certain value, returns boolean. Can take an optional fromIndex argument, which gives a starting index for search.

Time complexity is O(n).

###Examples
someNums.includes(7) => false
someNums.includes(3) => true
someNums.includes(3,4) => false

## indexOf()
The indexOf() returns the first index at which a given element can be found in the array, or -1 if not found. Can take an optional fromIndex argument, which gives a starting index for search.

Time complexity is O(n).

### Examples
someNums.indexOf(3) => 3
cakes.indexOf("Vanilla") => -1
cakes.indexOf({flavor: 'Vanilla', stock: 3}) => -1

## every()
The every() tests whether all elements in the array pass the test provided, returns a boolean.

Time complexity is O(n).

### Examples
someNums.every(x >= 0) => true
someNums.every(x > 0) => false
someNums.every(x % 2) => false

####Problems;
  Given a non-empty array of integers, return the result of multiplying the values together in order. Example:
  [1, 2, 3, 4] => 1 * 2 * 3 * 4 = 24
  ```
  function multInOrder(numArr) {
    return numArr.reduce((a,c)=>a*c)
  }
  ```

  You will be given an array of all the family members' ages, in any order. The ages will be given in whole numbers, so a baby of 5 months, will have an ascribed 'age' of 0. Return a new array with [youngest age, oldest age, difference between the youngest and oldest age].
  ```
  function putAgeOrder(famAges) {
    return famAges.sort((a,b)=>a-b)
  }
  ```

  Sum all the numbers of the array except the highest and the lowest element (the value, not the index!).
  Example:
  [ 6, 2, 1, 8, 10 ] => 16
  [ 1, 1, 11, 2, 3 ] => 6
  ```
  function sumMiddle(numArr) {
    return numArr.reduce((a,c)=>a+c) - Math.min(...numArr) - Math.max(...numArr)
  }
  ```




# String methods to know!
There are a lot of helpful string methods that every developer should get familiar with.

```
// Variables for string examples
let str1 = "Mornings are for chumps"
let str2 = "Garage office!!!!"
let arr1 = [1,2,3,4]
let obj1 = {key1: "store", key2: true, key3: 47}
```

##charAt
The charAt() takes an index as a argument and returns the character at that given index. If no index is provided, default return is 0. If index is out of range, returns an empty string

Time complexity is O(1)

###Examples:
let str1 = "Mornings are for chumps"
let str2 = "Garage office!!!!"

str1.charAt(7) => 's'   // index in range
str2.charAt(21) => ''   // index out of range
str1.charAt() => 0      // no index provided

##charCodeAt
the charCodeAt() takes an index as a argument and returns the UTF-16 code for the character at that given index. If no index is provided, default return is code at index 0. If index is out of range, returns NaN. If the UTF-16 code for that character is bigger than 0xFFFF, the first part of a surrogate pair for the code point will be returned.

Time complexity is O(1)

###Examples:
let str1 = "Mornings are for chumps"
let str2 = "Garage office!!!!"

str1.charCodeAt(7) => 115  // index in range
str2.charCodeAt(21) => NaN // index out of range
str1.charCodeAt() => 77    // no index provided

##concat
The concat() takes one or more strings as arguments (separated by commas) and concatenates them to the string the method is called on. If the arguments provided are not of string-type, they'll be converted to strings. Changes to the original string or concatenated string do not affect each other.

Time complexity is likely O(1), but curious if converting types of arguments makes it higher?

###Examples:
let str1 = "Mornings are for chumps"
let str2 = "Garage office!!!!"
let arr1 = [1,2,3,4]
let obj1 = {key1: "store", key2: true, key3: 47}

str1.concat(". ",str2) = "Mornings are for chumps. Garage office!!!!"  // more than 1 argument
str1.concat(arr1) = "Mornings are for chumps1,2,3,4"                   // argument non-string-type
str1.concat(obj1) = "Mornings are for chumps[object Object]"           // argument is object literal

##includes
The includes() does a case-sensitive search in the string the method was called on for a passed-in string. Optional *position* argument tells the method on which index to start searching (defaults to 0).

Time complexity seems like it should be O(n), but who can say?

###Examples:
let str1 = "Mornings are for chumps"
let arr1 = [1,2,3,4]
let obj1 = {key1: "store", key2: true, key3: 47}

str1.includes('are') => true        // checks for string that it includes
str1.includes('are', 12) => false   // starts checking string at optional index
"These are numbers 1,2,3,4".includes(arr1) => true        // forces arr1 to string type
"I'm going to the store".includes(obj1["key1"]) => true   // can use nested object data
"This is 9".includes(9) => true     // forces 9 to string type
str1.includes() => false            // did not include parameter, returns false

##indexOf
The indexOf() returns the index of the first instance found of the given string argument. If the search string is not found, returns -1. Takes an optional *fromIndex* parameter from which to start search.

Time complexity is O(n), but some nerds will argue O(m*n).

###Examples:
let str1 = "Mornings are for chumps"
let arr1 = [1,2,3,4]

str1.indexOf("chumps") => 17              // returns first index of character of first instance of 'chumps'
str1.indexOf("are", 15) => -1             // doesn't find 'are' because starting at index 15
"These are 1,2,3,4".indexOf(arr1) => 10   // coerces arr1 to string type

##match
The match() returns the results of matching a string against a regular expression, as an array. Takes a regexp obj as an argument, if argument isn't a regex, it coerces it into a new regexp. If no argument is provided, returns [""].

###Examples
let str1 = "Mornings are for chumps"

str1.match(/[o]/) => ['o', index: 1, input: 'Mornings are for chumps', groups: undefined] //returned first 'o'
str1.match(/^M/) => ['M', index: 0, input: 'Mornings are for chumps', groups: undefined]  //returned starting char 'M'
str1.match(/^a/) => null                                                                  //did not find, returned null
str1.match() => ['', index: 0, input: 'Mornings are for chumps', groups: undefined]       // returned [''] no arg
str1.match(/[a,c]/g) => ['a','c']                                                         // global tag returned group
str2.match(65);                                                                           // returns ["65"]

##repeat
The repeat() creates a new string consisting of the original string repeated a given number of times (concatenated together). Repeat value must be positive number, and floats will be rounded down. Repeat values will be coerced into number type if able.

Time complexity is O(n), but waiting for fierydrake to educate me.

###Examples:
let str1 = "Mornings are for chumps"

str2.repeat(3) => "Garage office!!!!Garage office!!!!Garage office!!!!"  // repeated 3 times
"butts ".repeat(5.3438282) => "butts butts butts butts butts"            // rounded down to 5 times
str1.repeat("2") => "Mornings are for chumpsMornings are for chumps"     // coerced value to number type
str2.repeat() => ""                                                      // no value treated as 0 value

##replace
The replace() creates a new string with some or all matches of a pattern replaced by a replacement. The given pattern can be a string or a regexp - string patterns only replace the first occurrence. Give 2 arguments to call it - a pattern (str or regexp), and replacement (str, or replacer function)

Time complexity is likely O(n), but unsure

###Examples:
let str2 = "Garage office!!!!"

str2.replace('a', 'A') => 'GArage office!!!!'     // Only replaced first instance of 'a'
str2.replace(/a/g, 'A') => 'GArAge office!!!!'    // Replaced all instances of 'a'
str2.replace('!!!!', '?') => 'Garage office?'     // Replaced 4 characters with single character

##search
The search() looks for a match between a regexp and the string. Returns the index of the first instance of the first match, or -1 is no match found.

Time complexity likely O(n)

###Examples
let str1 = "Mornings are for chumps"

str1.search(/are/) => 9
str1.search(/are/g) => 9
str1.search(/great/) => -1

##slice
The slice() extracts a section of string and returns it as a new string, without mutating the original string. Takes a beginning index, which if negative is treated as string.length - val. If it greater than string.length, '' is returned. Optional end index, non-inclusive, can be passed in. End index should be greater than beginning index, else '' returned.

Time complexity is likely O(n)

###Examples
let str2 = "Garage office!!!!"

str2.slice(3) => "age office!!!!"
str2.slice(-3) => "!!!"
str2.slice(5, 10) => "e off"

##split
The split() divides a string into an ordered list of substrings by searching for a pattern, places them in an array, and returns the array. Takes an optional separator, if none given it returns array with 1 index containing entire string. If separator is at beginning or end of the string, it leaves an empty string in its place when split. Optional limit can be passed in the limits the number of substrings in the array, leftover text is not included at all.

Time complexity is likely O(n)

###Examples
let str1 = "Mornings are for chumps"

str1.split(' ') => ['Mornings', 'are', 'for', 'chumps']
str1.split('') => ["M", "o", "r", "n", "i", "n", "g", "s", " ", "a", "r", "e", " ", "f", "o", "r", " ", "c", "h", "u", "m", "p", "s"]
str1.split('great') => ["Mornings are for chumps"]

##substr
The substr() method returns a portion of the string, starting at a specified index and extending for a given number of characters afterwards. Takes a starting index and optional length. If start is negative nuumber it counds from end of string.

Time complexity is likely O(n)

###Examples
let str2 = "Garage office!!!!"

str2.substr(5) => "e office!!!!"
str2.substr(-5) => "e!!!!"
str2.substr(5, 2) => "ic"

##toLowerCase
The toLowerCase() returns a new string of the calling string converted to lowercase.

Time complexity is likely O(n) or O(1)

###Examples
let str1 = "Mornings are for chumps"
let str2 = "Garage office!!!!"

str1.toLowerCase() => "mornings are for chumps"
"Garage office!!!!".toLowerCase() => "garage office!!!!"
''.toLowerCase() => ''

##toUpperCase
The toUpperCase() returns a new string of the calling string converted to uppercase.

Time complexity is likely O(n) or O(1)

###Examples
let str1 = "Mornings are for chumps"
let str2 = "Garage office!!!!"

str1.toUpperCase() => "MORNINGS ARE FOR CHUMPS"
"Garage office!!!!".toUpperCase() => "GARAGE OFFICE!!!!"
''.toUpperCase() => ''

##trim
The trim() removes whitespace from both ends of a string, but not the middle. Includes all whitespace - space, tab, no-break space, line terminators, etc. Does not mutate original string.

Time complexity is likely O(1) or O(n).

###Examples
let str3 = '      gnomes   '
let str4 = '  are      adorable    '

str3.trim() => 'gnomes'
str4.trim() => 'are      adorable'
(str3+str4).trim() => 'gnomes  are      adorable    '
