82 · Single Number
```java

class Solution {
        /**
     * @param a: An integer array
     * @return: An integer
     */
    public int singleNumber(int[] a) {
        // write your code here
        int single = 0;
        for (int num : a) {
            single ^= num;
        }
        return single;
    }
}

```
157 · Unique Characters
```java
public class Solution {
    /**
     * @param str: a string
     * @return: a boolean
     */
    public boolean isUnique(String str) {
        // write your code here
        boolean[] char_set = new boolean[256];
        for (int i = 0; i < str.length(); i++) {
            int val = str.charAt(i);

            if (char_set[val]) {
                 return false;
                 }
                char_set[val] = true;
        }
        return true;
    }
}

```
608 · Two Sum II - Input array is sorted
```java
public class Solution {
    /**
     * @param nums: an array of Integer
     * @param target: target = nums[index1] + nums[index2]
     * @return: [index1 + 1, index2 + 1] (index1 < index2)
     */
    public int[] twoSum(int[] nums, int target) {
         // write your code here
        if (nums == null || nums.length == 0) {
            return new int[0];
        }
        
        int left = 0;
        int right = nums.length - 1;
        int[] res = new int[2];
        
        while (left < right) {
            int sum = nums[left] + nums[right];
            if (sum > target) {
                right--;
            } else if (sum < target) {
                left++;
            } else { 
                res[0] = left + 1;
                res[1] = right + 1;
                return res;
            }
        }
        return new int[0];
    }
}

```