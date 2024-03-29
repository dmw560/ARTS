# ARTS 第一周

## Algorithm
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。<br>
你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。<br>
示例:<br>
给定 nums = [2, 7, 11, 15], target = 9<br>
因为 nums[0] + nums[1] = 2 + 7 = 9<br>
所以返回 [0, 1]
### 使用双重循环

``` Java
public static  int[] twoSum(int[] nums,int target){
        int[] result={-1,-1};
        for(int i=0;i<nums.length-1;i++){
            for(int j=i+1;j<nums.length;j++){
                if(nums[i]+nums[j]==target){
                    result[0]=i;
                    result[1]=j;
                    break;
                }
            }
        }
        return result;
    }
```
### 使用HashMap
``` Java
public static  int[] twoSumByHashMap(int[] nums,int target){
        int[] result={-1,-1};
        Map<Integer,Integer> map=new HashMap<>();
        for(int i=0;i<nums.length;i++){
            map.put(nums[i],i);
        }
        for(int i=0;i<nums.length;i++){
            int complement=target-nums[i];
            if(map.containsKey(complement) && map.get(complement)!=i){
                return new int[]{i,map.get(complement)};
            }
        }
        throw new IllegalArgumentException("No two sum solution!");
    }
```
### HashMap改进
``` Java
public static  int[] twoSumByHashMapOne(int[] nums,int target){
        int[] result={-1,-1};
        Map<Integer,Integer> map=new HashMap<>();
        for(int i=0;i<nums.length;i++){
            int complement=target-nums[i];
            if(map.containsKey(complement) && map.get(complement)!=i){
                return new int[]{i,map.get(complement)};
            }
            map.put(nums[i],i);
        }
        throw new IllegalArgumentException("No two sum solution!");
    }
```

## Review

## Tips
最近在看<<深入理解计算机系统>> 这本书 ,文章中讲到计算机中信息的表示和处理<br>
C语言分为无符号和有符号两种表示方法，Java中都是按有符号来表示<br>
这就导致用C语言编写的程序，一不小心就会出现因为数据类型的不一致导致bug<br>
因此在编写程序时要时刻注意两点：<br>
1.保证程序中参数、返回值等数据类型一致；
2.对于特殊值，如最大值、最小值要时刻保持警惕。
## Share

