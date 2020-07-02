# **LeetCode__001：两数之和**

##### 难度：简单

##### 题目描述：

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。

##### 示例：

```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

##### 解题思路：

利用hashMap，遍历一次即可，检查map中是否包含需要的值，有的话返回对应的key，没有的话将当前遍历到的元素put进map中。

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
       Map<Integer, Integer> map = new HashMap();
       int[] res = new int[2];
       for(int i=0; i<nums.length; i++) {
           int tmp = target-nums[i];
           if(map.containsKey(tmp)) {
               res[0] = map.get(tmp);
               res[1] = i;
               break;
           } else {
               map.put(nums[i],i);
           }
       }
       return res;
    }
}
```

##### 复杂度分析：

时间复杂度：由于最多只需要遍历一遍nums数组即可，所以复杂度为O(n)。

空间复杂度：除了返回的res数组外，额外使用了一个HashMap，最多存放n个元素，所以复杂度为O(n)。