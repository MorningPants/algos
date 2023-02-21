Q. Given a linked list, swap every two nodes, starting from the head of the list.

Example:

1 -> 2 -> 3 -> 4 returns 2 -> 1 -> 4 -> 3
1 -> 2 -> 3 returns 2 -> 1 -> 3

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


```function solution(head: ListNode<number>): ListNode<number> {
    let dummy = new ListNode(0)
    dummy.next = head
    let curr = dummy
    while(curr?.next?.next){
        let first = curr.next
        let second = curr.next.next
        let third = curr.next.next.next
        curr.next = second
        second.next = first
        first.next = third
        curr = first
    }
    
    return dummy.next
}

```
    TIME: 5 minutes
