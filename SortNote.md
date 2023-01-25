Bubble Sort
    1.比较相邻的元素，A，B
        如果A比B大。就去比B和C
        如果B比A大，就交换A，B 再去比B和C。
    2.重复以上步骤
    时间复杂度 O(n^2)

Selection sort
    1.从整个数组里选出最小的排在最前面
    2.从剩下的数组里选出最小的放在第二
    3.重复步骤直到剩余数字为0
    时间复杂度 O(n^2)

Insertion-Sort
    1.不移动第一个元素
    2.选取下一个元素和之前的元素对比，如果小于之前的元素就像前插入
    3.重复以上步骤直到没有新元素

Merge-sort
    1.把整个数组/2
    2.持续分组，直到数组只剩单独的数字
    3.对比单个数字，大小排序
    
Quick-sort
    1.找到中间值，把数组分成左右两部分
    2.从左往右检索，小于中间数的放左边，大于中间数的放右边
    3.在左半区和右半区重复以上步骤直至检索完成

    **Quick-select
        1.重复quick sort 分成左右两部分
        2.只检索需要的半区，剩下的半区不用管
        3.找到Target所在的位置，只检索target所在的半区直至sort完成

Radix-sort
    1.用int = 0; 找出数组个位数的数值，并且把他们分配到编号0-9
    2.用int = 1； 找出十位数组的数值，然后把他们再次分组
    3.持续排序直到sort结束；




public void mergeSort (int[] nums) {
    int left = 0;
    int right = nums.length - 1;
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (int)
    }
}





















[1,5,6,4,5]
    public void bubbleSort (int[] nums) {
        if (nums == 0) {
            return null;
        }
        int left = 0;
        int right = 1;

        while (right < nums.length) {
            if (nums[left] < nums[right]) {
                left++;
                right++
            } else if ( numd[right] < nums[left]) {
                swap(nums, left, right);
            } else {
                left++;
                right++;
            }
        } 
    }

    private void swap(int[] nums, int left, int right) {

        int temp = left; 
        left = right;
        right = temp;
        left++;
        right++;
    } 