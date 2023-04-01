Given a binary tree t, determine whether it is symmetric around its center, i.e. each side mirrors the other.

function solution(t: Tree<number>): boolean {
    if(!t) return true
    let Lstack = [t.left]
    let Rstack = [t.right]
    while(Lstack.length && Rstack.length){
        let l = Lstack.pop()
        let r = Rstack.pop()
        if(l == null && r == null) continue
        if(l == null || r == null) return false
        if(l.value !== r.value) return false
        Lstack.push(l.left)
        Lstack.push(l.right)
        Rstack.push(r.right)
        Rstack.push(r.left)
    }
    return Lstack.length == Rstack.length
}

  
  Q. Given a binary tree, return the the maximum sum of nodes from the root to any leaf.
  
  function solution(root: Tree<number>): number {
    let max = 0;
    function helper(node: Tree<number>, sum: number) {
        if (!node) return;
        sum += node.value;
        if (!node.left && !node.right) {
            if (sum > max) max = sum;
            return;
        }
        helper(node.left, sum);
        helper(node.right, sum);
    }
    helper(root, 0);
    return max;
}
  
  Q. Given a binary tree, return the values of the nodes when facing the tree from the right side (from top to bottom).

Example:
Input:
   1              <---
 /   \
2     5         <---
 \  
  7               <---
Output: [1, 5, 7]
                       
 function solution(root: Tree<number>): number[] {
    let queue = [root]
    let ans = []
    while(queue.length){
        let l = queue.length
        let curr
        for(let i = 0; i < l; i++){
            curr = queue.shift()
            if(curr.left) queue.push(curr.left)
            if(curr.right) queue.push(curr.right)
        }
        ans.push(curr.value)
    }
    return ans
}
                             
  Q. Given a binary tree and a target k, count the number of nodes that has a value less than k.
                             
function solution(root: Tree<number>, target: number): number {
    let count = 0;
    if(root.value < target) count++;
    if(root.left) count += solution(root.left, target);
    if(root.right) count += solution(root.right, target);
    return count;
}
                           
                           
                           Q. Flip a given binary tree.
                           
  function solution(root: Tree<number>): Tree<number> {
    if(!root) return null
    let temp = solution(root.left);
    root.left = solution(root.right);
    root.right = temp
    return root
}

  
  Q. Given a binary tree, sum all left leaf nodes.
  
  function solution(root: Tree<number>, isLeft = false): number {
    if(!root) return 0
    if(isLeft && !root.left && !root.right) return root.value
    let left = solution(root.left, true)
    let right = solution(root.right, false)
    return left + right

}


