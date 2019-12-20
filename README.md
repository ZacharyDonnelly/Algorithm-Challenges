# Javascript-Algorithim-Challenges
Two Sum
*Write a function that takes an array of numbers (integers for the tests) and a target number. It should find two different items in the array that, when added together, give the target value. The indices of these items should then be returned in a tuple like so: (index1, index2).*

*For the purposes of this kata, some tests may have multiple answers; any valid solutions will be accepted.*

*The input will always be valid (numbers will be an array of length 2 or greater, and all of the items will be numbers; target will always be the sum of two different items from that array).*
```
function twoSum(numbers, target) {
    for (var i = 0; i < numbers.length-1; i++) {
        for (var j = i+1; j < numbers.length; j++) {
            if (numbers[i] + numbers[j] === target) return [i, j];
        }
    }
}
```
Sort The Odd
*You have an array of numbers.*
*Your task is to sort ascending odd numbers but even numbers must be on their places.*

*Zero isn't an odd number and you don't need to move it. If you have an empty array, you need to return it.*

```
function sortArray(array) {
  const odd = array.filter((x) => x % 2).sort((a,b) => a - b);
  return array.map((x) => x % 2 ? odd.shift() : x);
}
```
*Less Pretty*
```
function sortArray(array) {
  var odds = [];
  //loop, if it's odd, push to odds array
  for (var i = 0; i < array.length; ++i) {
    if (array[i]%2 !== 0) {
      odds.push(array[i]);
    }
  }
  //sort odds from smallest to largest
  odds.sort(function(a,b){
    return a-b;
  });
  
  //loop through array, replace any odd values with sorted odd values
  for (var j = 0; j < array.length; ++j) {
    if (array[j]%2 !== 0) {
      array[j] = odds.shift();
    }
  }
  
 return array;
}
```
Write a function called rotate which takes an array and a number, and moves each element however many spaces the number is to the right. For the value at the end of the array, rotate should move it back to the beginning.
```
function rotate(arr,num){
    let amount = num % arr.length;
    for(let i = 0;i < amount;i++){
        arr.unshift(arr.pop())
    }
    return arr
}
```
```
rotate([1,2,3], 1) // [3,1,2]
rotate([1,2,3], 2) // [2,3,1]
rotate([1,2,3], 3) // [1,2,3]
```
Write a function called makeXOGrid which takes in two parameters, rows and columns, and returns an array of arrays with the number of values in each subarray equal to the columns parameter and the number of subarrays equal to the rows parameter. The values in the sub-arrays should switch between "X" and "O".
```
function makeXOGrid(rows,amount){
    var finalArr = []
    var startWithX = true
    for(var i=0; i<rows; i++){
        var newRow = []
        for(var j=0; j<amount; j++){
            if(startWithX){
                newRow.push("X")
            }
            else {
                newRow.push("O")
            }
            startWithX = !startWithX
        }
        finalArr.push(newRow)
    }
    return finalArr;
}
```
```
makeXOGrid(1,4) 

/*/
[["X","O","X","O"]]
/*/

makeXOGrid(3,2) 

/*/
[["X","O"],["X","O"],["X","O"]]
/*/

makeXOGrid(3,3) 
/*/
[["X","O","X"],["O","X","O"],["X","O","X"]]
/*/
```
You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this "outlier" N.
```
function findOutlier(arr){
  let even = [];
  let odd = [];
  for(let i = 0;i < arr.length;i++){
    if(arr[i] % 2 === 0){
      even.push(arr[i])
    }else {
      odd.push(arr[i])
    }
  }
  if(even.length > odd.length){
    return Number(odd)
  }else {
    return Number(even)
  }
}
```
```
(findOutlier([0, 1, 2]),1) // returns odd
(findOutlier([1, 2, 3]), 2) // returns even
```
```
*clean version
function findOutlier(int){
  var even = int.filter(a=>a%2==0);
  var odd = int.filter(a=>a%2!==0);
  return even.length==1? even[0] : odd[0];
}
```

Return the number that only appears once in the array
```
function findUniq(arr) {
  arr.sort((a,b)=>a-b);
  return arr[0]==arr[1]?arr.pop():arr[0];
}
findUniq([ 3,3,3,10,3,3,3 ]);
```
Write a simple parser that will parse and run Deadfish.

Deadfish has 4 commands, each 1 character long:

i increments the value (initially 0)
d decrements the value
s squares the value
o outputs the value into the return array
Invalid characters should be ignored.

//output should be parse("iiisdoso") => [ 8, 64 ]
```
function parse(data) {
    let count = 0;
    let secondCount = 0;
    let arr = [];
    for (let i = 0; i < data.length; i++) {
        if (data[i] === 'i') {
            count++
        } else if (data[i] === 'd') {
            count--
        } else if (data[i] === 's') {
            count = count * count
        } else if (data[i] === 'o') {
            arr.push(count);
            if(count < 0){
                count = count
            }else {
                count += 0
            }
        }
    }
    return arr
}
*before refactor
```
```
function parse(data) {
    let count = 0;
    let arr = [];
    for (let i = 0; i < data.length; i++) {
        switch (data[i]) {
        case ('i'):
            count++
            break;
        case ('d'):
            count--
            break;
        case ('s'):
            count = count * count
            break;
        case ('o'):
            arr.push(count)
            break;
        }
    }
    return arr
}
*after refactor
```
Write a function called "countAllCharacters".

Given a string, "countAllCharacters" returns an object where each key is a character in the given string. The value of each key should be how many times each character appeared in the given string.
```
function countAllCharacters(str) {
        let result = {}
        for(let i = 0;i < str.length;i++){
          if(result[str[i]] === undefined){
            result[str[i]] = 1;
          }else{
            result[str[i]] += 1
          }
        }
        return result
}
countAllCharacters('banana'); 
//output: {b: 1, a: 3, n: 2}
```
Write a function that takes two or more arrays and returns a new array of unique values in the order of the original provided arrays.

In other words, all values present from all arrays should be included in their original order, but with no duplicates in the final array.

The unique numbers should be sorted by their original order, but the final array should not be sorted in numerical order.
```
function uniteUnique(arr) {
    const old = Array.from(arguments)
    const final = []
    for(let i = 0;i < old.length;i++){
        for(let j = 0;j < old[i].length;j++){
          if(!final.includes(old[i][j]))
          final.push(old[i][j])
        }
    }
  return final
}
// uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1])
// [1, 3, 2, 5, 4]
```
