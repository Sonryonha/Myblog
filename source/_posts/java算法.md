---
title: 算法练习（java）
categories: 
- 算法
tags: 
- java算法
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

### 螺旋矩阵||
 ```java
 class Solution {
    public int[][] generateMatrix(int n) {
        int[][] res = new int[n][n];
        // 从第一个数开始计算
        int count = 1;
        // 每一圈的起点
        int start = 0;
        // 行列下标
        int i, j;
        // 圈数
        int loop = 0;

        while (loop++ < n / 2) {
            // 从左到右
            // 因为每转一圈左边界会+1，右边界会-1
            // 所以就用边界值+-圈数来控制
            for (j = start; j < n - loop; j++) {
                res[start][j] = count++;
            }
            // 从右到右下
            for (i = start; i < n - loop; i++) {
                res[i][j] = count++;
            }
            // 从右下到左下
            // 行下标固定，同时要放开相对右边界
            for ( ; j >= loop; j--) {
                res[i][j] = count++;
            }
            // 从左下到左上
            // 列下标固定，同时要放开相对左边界
            for ( ; i >= loop; i--) {
                res[i][j] = count++;
            }
            start++;
        }
        // n为奇数则需要计算中间点，为偶数则不用计算
        if (n % 2 == 1) {
            res[start][start] = count;
        }
        // 返回最终数组
        return res;
    }
}
 ```