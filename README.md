# Study-notes
记录leetcode 学习
   return shell_exec("echo $input | $markdown_script");
   
   

- LeetCode 53. 最大子序和

给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

示例:

输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。
```
class Solution {
    public int maxSubArray(int[] nums) {
        int maxSum = nums[0];
        int tempSum = 0;
        int begin = 0;
        for(int i=0;i<nums.length;i++){
            if(tempSum>0){
                tempSum+=nums[i];
            }else{
                tempSum=nums[i];
                begin=i;        //标记开始位
            }          
            if(tempSum>maxSum){
                maxSum=tempSum;
            }
        }       
        return maxSum;
    }
}
```




- LeetCode 64. 最小路径和

给定一个包含非负整数的 m x n 网格，请找出一条从左上角到右下角的路径，使得路径上的数字总和为最小。

说明：每次只能向下或者向右移动一步。

示例:

输入:
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
输出: 7
解释: 因为路径 1→3→1→1→1 的总和最小。
```
class Solution {
    public int minPathSum(int[][] grid) {        
        for(int i=grid.length-1;i>=0;i--){
            for(int j=grid[0].length-1;j>=0;j--){
                if(i==grid.length-1 && j!=grid[0].length-1){
                    grid[i][j]=grid[i][j]+grid[i][j+1];
                }
                else if(i!=grid.length-1 && j==grid[0].length-1){
                    grid[i][j]=grid[i][j]+grid[i+1][j];
                }
                else if(i!=grid.length-1 && j!=grid[0].length-1){
                    grid[i][j]=grid[i][j]+Math.min(grid[i+1][j],grid[i][j+1]);
                }
            }
        }
        return grid[0][0];
    }
}
```

- LeetCode 70. 爬楼梯

假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

示例 1：

输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 阶 + 1 阶
2.  2 阶
示例 2：

输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。
1.  1 阶 + 1 阶 + 1 阶
2.  1 阶 + 2 阶
3.  2 阶 + 1 阶


```ruby
class Solution {
    public int climbStairs(int n) {
        if(n==0)
            return 0;
        if(n==1)
            return 1;
        if(n==2)
            return 2;
        int first=1,second=2,third=0;
        for(int i=3;i<=n;i++){
            third=first+second;
            first=second;
            second=third;
        }
        return third;
    }
}
```

