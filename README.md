# Binary Tree Zigzag Level Order Traversal
## https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/


## Implementation :

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> list = new ArrayList<>();
        if(root == null)
            return list;
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        int currentLevel = 0;
        while(!queue.isEmpty()){
            currentLevel++;
            List<Integer> level = new ArrayList<>();
            int size = queue.size();
            for(int i = 0; i < size; i++){
                TreeNode current = queue.poll();
                level.add(current.val);
                if(current.left != null)
                    queue.offer(current.left);
                if(current.right != null)
                    queue.offer(current.right);
            }
            if(currentLevel % 2 == 0)
                Collections.reverse(level);
            list.add(level);
            
        }
       return list; 
    }
}
```
