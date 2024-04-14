# LeetCode刷题笔记

markdown官方语法链接：

[Markdown 代码语法 | Markdown 官方教程](https://markdown.com.cn/basic-syntax/code.html)

## 一、基础代码模板

### 1、ACM模式（Python版）

#### 1.1 输入输出模式

[(3条未读私信) 牛客竞赛_ACM/NOI/CSP/CCPC/ICPC算法编程高难度练习赛_牛客竞赛OJ (nowcoder.com)](https://ac.nowcoder.com/acm/contest/5652)

##### 1.1.1 数字输入

print\println的区别 :

①print将它的参数显示在命令窗口，并将输出光标定位在所显示的最后一个字符之后。

②println 将它的参数显示在命令窗口，并在结尾加上换行符，将输出光标定位在下一行的开始。

```python
'''
Type 1:多组空格分隔的两个正整数
输入格式为：
1 5
10 20
'''
while True:
    try:
        num = list(map(int,input().split(" ")))
        print(sum(num)) 
    except:
        break
        
        
'''
Type 2：第一行组数接空格分隔的两个正整数
2
1 5
10 20
'''
t = int(input())
for i in range(t):
    num = list(map(int,input().split(" ")))
    print(sum(num))
    
    
'''
Type 3:空格分隔的两个正整数为0 0 结束
1 5
10 20
0 0
'''
while True:
    try:
        num = list(map(int,input().split(" ")))
        if num[0] == num[1] == 0:
            break
        print(sum(num)) 
    except:
        break
```

##### 1.1.2 字符串输入

```python
'''
Type 1:第一行个数第二行字符串
5
c d a bb e
'''
t = int(input())
num = list(input().split(" "))
num.sort()
print(" ".join(num))

'''
Type 2:多行逗号分开的字符串
a,c,bb
f,dddd
nowcoder
'''
while True:
    try:
        num = list(input().split(","))
        num.sort()
        print("," .join(num))
    except:
        break
```



### 2. 动态规划模板

动规五部曲：

1. **确定dp数组（dp table）以及下标的含义**

   dp\[i][j] 表示从下标为[0-i]的物品里任意取，放进容量为j的背包，价值总和最大是多少。

2. **确定递推公式**

   ​	$dp[i][j] = max(dp[i - 1][j], dp[i - 1][j - weight[i]] + value[i])$

3. dp数组如何初始化

   ​	$dp[0][j]$，即：i为0，存放编号0的物品的时候，各个容量的背包所能存放的最大价值。当$j >= weight[0]$时，$dp[0][j]$ 应该是value[0]，因为背包容量放足够放编号0物品。

4. 确定遍历顺序

5. 举例推导dp数组

背包问题：

### 3.递归遍历

#### 3.1 二叉树主要有两种遍历方式：

1. 深度优先遍历：先往深走，遇到叶子节点再往回走。
2. 广度优先遍历：一层一层的去遍历。

- 深度优先遍历
  - 前序遍历（递归法，迭代法）： 中左右
  - 中序遍历（递归法，迭代法）： 左中右
  - 后序遍历（递归法，迭代法）： 左右中
- 广度优先遍历
  - 层次遍历（迭代法）

#### 3.2 二叉树的定义

```python
class TreeNode:
    def __init__(self, val, left = None, right = None):
        self.val = val
        self.left = left
        self.right = right
```

python版本的三种遍历

```python
# 前序遍历-递归-LC144_二叉树的前序遍历
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right

class Solution:
    def preorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []

        left = self.preorderTraversal(root.left)
        right = self.preorderTraversal(root.right)

        return  [root.val] + left +  right
   
```

```python
# 中序遍历-递归-LC94_二叉树的中序遍历
class Solution:
    def inorderTraversal(self, root: TreeNode) -> List[int]:
        if root is None:
            return []

        left = self.inorderTraversal(root.left)
        right = self.inorderTraversal(root.right)

        return left + [root.val] + right
```

```python
# 后序遍历-递归-LC145_二叉树的后序遍历
class Solution:
    def postorderTraversal(self, root: TreeNode) -> List[int]:
        if not root:
            return []

        left = self.postorderTraversal(root.left)
        right = self.postorderTraversal(root.right)

        return left + right + [root.val]
```



## 二、题目要点及代码链接

## 三、知识点总结

### 1、并查集

[(39条消息) 并查集总结（python）_python 并查集_TransientYear的博客-CSDN博客](https://blog.csdn.net/z_feng12489/article/details/105789587)

### 2、字符串中对字母和数字集合

String模块ascii_letters和digits

本文介绍Python3中String模块ascii_letters和digits方法，其中ascii_letters是生成所有字母，从a-z和A-Z,digits是生成所有数字0-9.

注意，使用ord()函数表示将char字符转为ascii码

```python
import String
chars = string . ascii_letters + string . digits
print ( chars )
# output:abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789
```

[(39条消息) Python3基础:String模块ascii_letters和digits_killmice的博客-CSDN博客](https://blog.csdn.net/killmice/article/details/53118884)

注意raw_input()和inpu()的区别，一般raw_input()是把所有输入都当做字符串来看待

[(39条消息) raw_input和input的区别_DQ_DM的博客-CSDN博客](https://blog.csdn.net/dq_dm/article/details/45665069)

判断字符串s是否为数字或者字母：s.isalnum().返回True False

### 3、最大值和最小值的表示方法：

float('inf')表示正无穷；-float('inf')表示负无穷

其中的inf 都可以写成是 Inf

a//b表示a除以b再线下取整

enumerate() 函数用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，同时列出数据和数据下标，一般用在 for 循环当中。

```python
>>> seasons = ['Spring', 'Summer', 'Fall', 'Winter']
>>> list(enumerate(seasons))
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
```

4. 检验是否存在字母或者数字

   isalnum() 是 python 字符串对象的一个方法，用于检测字符串是否由字母和数字组成。该函数如果在字符串只包含字母数字字符则返回 True，否则返回 False。



四舍五入：

字母的大小写：

str.isupper(): 判断是否是大写字母

str.islower(): 判断是否是小写字母

ord(i)  : 把字母转换成ASCII码编号

chr(int(code))

round(num, 3) 保留小数点后3位

### 4、背包问题

分组背包问题：有n件物品，分为若干组，现约束，在每组物品里**最多取一件**物品放入背包，每件物品的重量确定，价值确定，背包容量确定，求在不超过背包容量的情况下，可以存放的最大价值。

```python
N, V = map(int, input().split())
dp = [0]*(V+1)

for _ in range(N):
    s = int(input())
    vs, ws = [], []
    for _ in range(s):
        v, w = map(int, input().split())
        vs.append(v); ws.append(w)
    for j in range(V, 0, -1):
        for v, w in zip(vs, ws):
            if j >= v: dp[j] = max(dp[j], dp[j-v]+w)
print(dp[-1])
```

