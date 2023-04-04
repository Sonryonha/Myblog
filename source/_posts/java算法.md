---
title: 算法练习（java）
---

## 数组

### 二分查找
```java
    //题目要求：给定一个 n 个元素有序的（升序）整型数组 nums 和一个目标值 target  ，写一个函数搜索 nums 中的 target，如果目标值存在返回下标，否则返回 -1。
    // 测试用例1：nums = [-1,0,3,5,9,12], target = 9
    // 测试用例2：nums = [-1,0,3,5,9,12], target = 2
    // mainCodePart
    class Solution {
        public int search(int[] nums, int target) {
            if (target < nums[0] || target > nums[nums.length - 1]) {
                return -1;
            }
            int leftEdge = 0;
            int rightEdge = nums.length - 1;
            while (leftEdge <= rightEdge) {
                int mid = leftEdge + ((rightEdge - leftEdge) >> 1);
                if (nums[mid] == target) {
                    return mid;
                }else if (nums[mid] > target) {
                    rightEdge = mid - 1;
                }else if (nums[mid] < target) {
                    leftEdge = mid + 1;
                }
            }
            return -1;
        }
    }
```