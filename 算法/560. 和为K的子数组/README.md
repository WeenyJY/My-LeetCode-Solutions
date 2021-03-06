| [English](README_EN.md) | 简体中文 |

# [560. 和为K的子数组](https://leetcode-cn.com/problems/subarray-sum-equals-k)
<p>给定一个整数数组和一个整数&nbsp;<strong>k，</strong>你需要找到该数组中和为&nbsp;<strong>k&nbsp;</strong>的连续的子数组的个数。</p>

<p><strong>示例 1 :</strong></p>

<pre>
<strong>输入:</strong>nums = [1,1,1], k = 2
<strong>输出:</strong> 2 , [1,1] 与 [1,1] 为两种不同的情况。
</pre>

<p><strong>说明 :</strong></p>

<ol>
	<li>数组的长度为 [1, 20,000]。</li>
	<li>数组中元素的范围是 [-1000, 1000] ，且整数&nbsp;<strong>k&nbsp;</strong>的范围是&nbsp;[-1e7, 1e7]。</li>
</ol>

**标签:**  [数组](https://leetcode-cn.com/tag/array) [哈希表](https://leetcode-cn.com/tag/hash-table) 
 ### 相似题目
- 简单:	[两数之和](https://leetcode-cn.com/problems/two-sum) 
- 中等:	[连续的子数组和](https://leetcode-cn.com/problems/continuous-subarray-sum) 
- 中等:	[乘积小于K的子数组](https://leetcode-cn.com/problems/subarray-product-less-than-k) 
- 简单:	[寻找数组的中心索引](https://leetcode-cn.com/problems/find-pivot-index) 
- 中等:	[和可被 K 整除的子数组](https://leetcode-cn.com/problems/subarray-sums-divisible-by-k) 

# 解题思路 √

### Python

1. 利用前缀和 + hashtable

   转换 `prefixSum[j]-prefixSum[i]=k` -> `prefixSum[i]=prefixSum[j]-k`

```python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        length=len(nums)
        sumValue,count=0,0
        hashmap={0:1}
        
        for num in nums:
            sumValue+=num
            if sumValue-k in hashmap:count+=hashmap[sumValue-k]
            if sumValue in hashmap:hashmap[sumValue]+=1
            else:hashmap[sumValue]:hashmap[sumValue]=1
        
        return count
```


```python

```

### C++

```cpp

```

---



# 整理与总结

1. 需要注意 `hashmap` 初始化的时候 `{0:1}`