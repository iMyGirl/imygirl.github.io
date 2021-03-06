### 1.删除排序数组中的重复项
给定一个排序数组，你需要在 原地 删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在 原地 修改输入数组 并在使用 O(1) 额外空间的条件下完成。

 

示例 1:

给定数组 nums = [1,1,2], 

函数应该返回新的长度 2, 并且原数组 nums 的前两个元素被修改为 1, 2。 

你不需要考虑数组中超出新长度后面的元素。

示例 2:

给定 nums = [0,0,1,1,1,2,2,3,3,4],

函数应该返回新的长度 5, 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4。

你不需要考虑数组中超出新长度后面的元素。

 

说明:

为什么返回数值是整数，但输出的答案是数组呢?

请注意，输入数组是以「引用」方式传递的，这意味着在函数里修改输入数组对于调用者是可见的。

你可以想象内部操作如下:

// nums 是以“引用”方式传递的。也就是说，不对实参做任何拷贝
int len = removeDuplicates(nums);

// 在函数里修改输入数组对于调用者是可见的。
// 根据你的函数返回的长度, 它会打印出数组中该长度范围内的所有元素。
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
```
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        count = 0
        for i in range(1,len(nums)):
            if nums[i] != nums[count]:
                nums[count + 1] = nums[i]
                count += 1

        return count + 1
```
```
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        current = 0 # current默认赋值为0，这样就避免了special case (if not nums: return 0)

        for i in range(1, len(nums)): # 从index为1开始遍历数组，如果数组长度小于1，则会自动退出
            if nums[i] != nums[current]:
                nums[current + 1] = nums[i]
                current += 1

        return current + 1

作者：LucasWang474
链接：https://leetcode-cn.com/leetbook/read/top-interview-questions-easy/x2gy9m/?discussion=9ZerB6
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```

# 2. 两数之和
  
给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 的那 两个 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。

你可以按任意顺序返回答案。

 

示例 1：

输入：nums = [2,7,11,15], target = 9
输出：[0,1]
解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。

示例 2：

输入：nums = [3,2,4], target = 6
输出：[1,2]

示例 3：

输入：nums = [3,3], target = 6
输出：[0,1]

 

提示：

    2 <= nums.length <= 103
    -109 <= nums[i] <= 109
    -109 <= target <= 109
    只会存在一个有效答案


```
### 未调通
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        plot = []
        for i in range (1,len(nums)-1):
            for j in range(i+1,len(nums)):
                if nums[i] + nums[j] == target:
                    plot[0] = i
                    plot[1] = j
        return plot

```
