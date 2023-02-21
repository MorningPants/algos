PROMPT
Given an array of ints, compute recursively the number of times that the value 6 appears in the array. We'll use the convention of considering only the part of the array that begins at the given index. In this way, a recursive call can pass index+1 to move down the array. The initial call will pass in index as 0.

Example(s)

```
array6([1, 2, 6], 0) == 1
array6([6, 6], 0) == 2
array6([1, 2, 3, 4], 0) == 0
```

SOLUTION

```
function array6(array : Array<number>, index : number) : number{
  if(index == array.length) return 0
  let count = (array[index] === 6) ? 1 : 0
  return count + array6(array, index + 1)
}

console.log(array6([6,1,6,6], 1)) // == 2
```

TIME: 4 minutes
