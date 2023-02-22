/*
Given a text input, print out the kth line in the file.

Follow-ups:
1) Ignoring the space complexity used to load the file into memory, what additional memory does using .split() incur? The answer should be O(n) since we're making an array copy.

2) Come up with an iterative solution that uses only O(l) additional space (after loading the file into memory).
 

EXAMPLE(S)
"lineZero\nlineOne\nlineTwo\nlineThree\n", k = 0
Output: "lineZero"

"lineZero\nlineOne\nlineTwo\nlineThree\n", k = 3
Output: "lineThree"

"lineZero\nlineOne\nlineTwo\nlineThree\n", k = 5
Output: ""
 

FUNCTION SIGNATURE
func printLine(text: String, lineNumber: Int)
*/

function printLine(str, k){
  // return str.split("\n")[k] || ""

  let arr = []
  let start = 0
  for(let i = 0; i < str.length; i++){
    if(str[i] === "\n"){
      arr.push(str.substring(start, i))
      start = i + 1
    }
  }
  arr.push(str.substring(start))
  return arr[k] || ""
  
}
// let test = "lineZero\nlineOne\nlineTwo\nlineThree\n"
let test2 = "LineZero\n"
let test3 = "LineZero\nLineOne"
let test4 = "LineZero\nLineOne"

 console.log(printLine(test, 0), "0")
 console.log(printLine(test, 3),"3")
 console.log(printLine(test, 5), "5")
console.log(printLine(test2, 0)) // "LineZero"
console.log(printLine(test3, 1)) //"LineOne"
console.log(printLine(test4, 4)) ""

Time Complexity: O(n)
Space Complexity: O(n)


Time to first solution: 2 minutes
Time to iterative solution: 10 minutes
