# Leetcode Daily Challenge Solutions

This is my attemp to make the coding experience easier for you guys so that you can easily learn what to do in today's leetcode challenge.


## Always here to assist you guys.

## Today's 02-01-24 [Problem Link](https://leetcode.com/problems/convert-an-array-into-a-2d-array-with-conditions/solutions/4490329/daily-02-01-24/)

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Unitary way to think.

# Approach
<!-- Describe your approach to solving the problem. -->
- I counted the frequencies of every number in the given array
- - used HashMap for that
- The maximum frequency of all element will be the number of answer rows
- - as in every row there should be unique elements
- Created and initialised answerlist with empty sub-lists
- Now, according to their frequencies adding elements to their rows
- - elements with frequency '1' will be present in only first row
- - elements with frequency '2' will be present in first and second row
- - ... and so on
---
Have a look at the code , still have any confusion then please let me know in the comments
Keep Solving.:)


# Complexity
- Time complexity : $$O(cm)$$
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity : $$O(c)$$
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
$$c$$ : number of unique elements in array
$$m$$ : maximum frequency of any element

# Code
```
class Solution {
    public List<List<Integer>> findMatrix(int[] nums) {
        HashMap<Integer, Integer> m = new HashMap<>();
        int mf = 0; // to store maximum frequency of any integer : it will determine the number of rows
    
        // adding numbers in hashmap along with its frequencies
        for( int i = 0; i < nums.length; i++){
            m.putIfAbsent(nums[i], 0);
            m.put( nums[i], m.get(nums[i]) + 1 );
            mf = Math.max(mf, m.get(nums[i]));
        }
        List<List<Integer>> l = new ArrayList<>(); // to store the answer list
        // the element with maximum frequency will be present in every sub-list of answerlist
        // making 'mf' rows in answer list
        for( int i = 0; i < mf; i++){              
            List<Integer> t = new ArrayList<>();
            l.add(t);
        }
        
        // according to their frequencies adding elements to their rows
        // elements with frequency '1' will be present in only first row
        // elements with frequency '2' will be present in first and second row
        // ... and so on

        for( int c : m.keySet() ){
            for( int f = 0; f < m.get(c); f++){
                l.get(f).add(c);
            }
        }
        return l;
    }
}
```
