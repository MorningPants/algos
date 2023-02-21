Q. Given a linked list, turn the value of each node into its index, starting with 0.

For example, given this linked list:
1 -> 5 -> 3

Overwrite the values so that it is:
0 -> 1 -> 2

Parameters
list: ListNode - the head of the list

Return
the head of the list (should be same as the input list)


```
// Singly-linked lists are already defined with this interface:
// class ListNode<T> {
//   value: T;
//   next: ListNode<T>;
//
//   constructor(value: T) {
//     this.value = value;
//     this.next = null;
//   }
// }
//
function solution(list: ListNode<number>, index = 0): ListNode<number> {
    if(list == null) return list
    list.value = index
    solution(list.next, index + 1)
    return list
}

```

TIME: 2 minutes



Q. Given a linked list, find the first occurring pair from the head with the biggest difference.

Example:
Input: [1, 2, 3, 10, 4, 11]
Output: [3, 10] // difference of 7; notice [4, 11] also differs by 7

function solution(head: ListNode<number>): ListNode<number> | null {
 let curr1 = head
 let curr2 = head?.next
 let maxDiff = -1
 let chosenNode : ListNode<number> | null = null
 while(curr2){
     let diff = Math.abs(curr2.value - curr1.value)
     if(diff > maxDiff){
         chosenNode = curr1
         maxDiff = diff
     }
     curr1 = curr2
     curr2 = curr2.next
 }
 if(chosenNode){
     chosenNode.next.next = null
     return chosenNode
 }
 return null
}
 time: 10
 
 
 
 
 Q. Given a linked list representing a binary number, convert it to a decimal value. Each node contains either 0 or 1 and the digits are high order first (2's place before 1's).

Example:

1 -> 1 returns 3.
 
 function solution(head: ListNode<number>): number {
    
    let pow = 0
    function calculate(node){
        if(!node) return 0
        let ans = calculate(node.next) + node.value * 2 ** pow
        pow++
        return ans
    }
    return calculate(head)
}

Time: 8 mins


Q. Given a target k, create a linked list with values starting at 0 and incrementing by 1 until k.

For example, given k = 3, return:
0 -> 1 -> 2 -> 3

You may assume k >= 0.

function solution(k: number, i = 0): ListNode<number> {
    if(k < i) return null
    let ans = new ListNode(i)
    ans.next = solution(k, i + 1)
    return ans
}


Time : 2 mins
