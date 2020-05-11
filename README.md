# Study-notes
记录个人的学习笔记

LeetCode 53. 最大子序和

给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

示例:

输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。


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



LeetCode 64. 最小路径和

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





