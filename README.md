# Finoramic-test
Test

Section 1: Data Structures 
Problem 1:
Given a binary tree and a sum, find all root-to-leaf paths where each path’s sum equals the given sum.

For example:
Given the below binary tree and sum = 22,

              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
return

[
   [5,4,11,2],
   [5,8,4,5]
]

ANS:
Answer is solved in JAVA 8  Language.

public class Solution {
    public List<ArrayList<Integer>> pathSum(TreeNode A, int B) {
    ArrayList<ArrayList<Integer>> result = new ArrayList<ArrayList<Integer>>();
    if(A == null) 
        return result;
 
    ArrayList<Integer> l = new ArrayList<Integer>();
    l.add(A.val);
    dfs(A, B-A.val, result, l);
    return result;
}
public void dfs(TreeNode t, int B, ArrayList<ArrayList<Integer>> result, ArrayList<Integer> l){
    if(t.left==null && t.right==null && B==0){
        ArrayList<Integer> temp = new ArrayList<Integer>();
        temp.addAll(l);
        result.add(temp);
    }
    if(t.left != null){
        l.add(t.left.val);
        dfs(t.left, B-t.left.val, result, l);
        l.remove(l.size()-1);
    }
    if(t.right!=null){
        l.add(t.right.val);
        dfs(t.right, B-t.right.val, result, l);
        l.remove(l.size()-1);
    }

}

Problem 2:

Implement pow(x, n) % d.

In other words, given x, n and d,

find (xn % d)

Note that remainders on division cannot be negative. 
In other words, make sure the answer you return is non negative.

Input : x = 2, n = 3, d = 3
Output : 2

2^3 % 3 = 8 % 3 = 2.

ANS:-
Answer is solved in C++ Language.

int pow(int x, int n, int d) {
    
    if (n == 0) return 1 % d;

    long long ans = 1, base = x;
    
    while (n > 0) {
        if (n % 2 == 1) {
            ans = (ans * base) % d;
            n--;
        } 
        else {
            base = (base * base) % d;
            n /= 2;
        }
    }
    
    if (ans < 0) ans = (ans + d) % d;
    return ans;
}


