8-23

leetCode.1
Two Sum
```

class Solution {
    public int[ ] twoSum(int[ ] nums, int target) {
        for (int i = 0; i < nums.length; i++){
            for (int j = i + 1; j < nums.length; ouj++) {
                if (nums[ j ] == target - nums[i]) {
                    return new int[ ] { i, j };
                }
            }
        }
        return null;
    }
}
```


leetCode.561
Array Partition
```
class Solution {
    public int arrayPairSum(int[] nums) {
        Arrays.sort(nums);
        int maxSum = 0;
        for (int i = 0; i < nums.length; i += 2) {
            maxSum += nums[i];
        }
        return maxSum;
    }
}
```