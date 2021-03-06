| [English](README_EN.md) | 简体中文 |

# [93. 复原IP地址](https://leetcode-cn.com/problems/restore-ip-addresses)
<p>给定一个只包含数字的字符串，复原它并返回所有可能的 IP 地址格式。</p>

<p>有效的 IP 地址正好由四个整数（每个整数位于 0 到 255 之间组成），整数之间用 <code>&#39;.&#39; </code>分隔。</p>

<p>&nbsp;</p>

<p><strong>示例:</strong></p>

<pre><strong>输入:</strong> &quot;25525511135&quot;
<strong>输出:</strong> <code>[&quot;255.255.11.135&quot;, &quot;255.255.111.35&quot;]</code></pre>

**标签:**  [字符串](https://leetcode-cn.com/tag/string) [回溯算法](https://leetcode-cn.com/tag/backtracking) 
 ### 相似题目
- 简单:	[IP 到 CIDR](https://leetcode-cn.com/problems/ip-to-cidr) 

# 解题思路 √

### Python

1. 回溯法经典题目

```python
class Solution:
    def restoreIpAddresses(self, s: str) -> List[str]:
        if not s:return []
        if len(s)<4 or len(s)>12:return []
        results=[]

        def backTrack(k,tempAddress,s):
            if k==4 or len(s)==0:
                if k==4 and len(s)==0:
                    results.append(tempAddress)
                return 
            
            for i in range(len(s)):
                if i>2:break
                if i!=0 and s[0]=='0':break
                part=s[:i+1]
                if int(part)<256:
                    if len(tempAddress)!=0:
                        part='.'+part
                    backTrack(k+1,tempAddress+part,s[i+1:])

        backTrack(0,'',s)
        return results
```


```python

```

### C++

```cpp

```

---



# 整理与总结

1. 