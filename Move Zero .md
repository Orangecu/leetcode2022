8-26
Lint 539

```java

public class Solution {
    /**
     * @param nums: an integer array
     * @return: nothing
     */
    public void moveZeroes(int[] nums) {
        // write your code here
        int NZP = 0;
        int ZP = 0;
        while (NZP < nums.length) {
            if (nums[NZP] != 0) {
                if (ZP != NZP) {
                    nums[ZP] = nums[NZP];
                }
                ZP++;
            }
            NZP++;
        }
        while (ZP < nums.length) {
            nums[ZP++] = 0;
        }
    }
}


```
