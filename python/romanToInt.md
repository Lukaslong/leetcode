## Roman To Int/罗马数字转整数
### 问题描述：
罗马数字包含以下七种字符: I， V， X， L，C，D 和 M。

字符　　　数值

I　　　　　1

V　　　　　5

X　　　　　10

L　　　　　50

C　　　　　100

D　　　　　500

M　　　　　1000

例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做  XXVII, 即为 XX + V + II 。

通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况：

    I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。
    X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
    C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。

给定一个罗马数字，将其转换成整数。输入确保在 1 到 3999 的范围内。

#### 示例 1:

输入: "LVIII"

输出: 58

解释: L = 50, V= 5, III = 3.

##### 示例 2:

输入: "MCMXCIV"

输出: 1994

解释: M = 1000, CM = 900, XC = 90, IV = 4.

问题链接：https://leetcode-cn.com/problems/roman-to-integer

--------
### 问题分析：
##### 1. 直接法：
最直接粗暴的方法是遍历输入字符串的每个元素，由于Python没有switch语句，因此只能通过不断的if/elif来找到字符对应的数值。
另外还要进行if的嵌套，遇到I、X、C，需判断下一位是不是V、M等，如果是，则要一起计算。
这种方法过于繁琐，就不实现了。
##### 2. 字典：
使用字典，遍历字符串中字符时，只需通过字典中的key就可以直接获取key对应的value。
这里字典的设计有点小技巧，首先是将IV，IX这些组合数也一起作为key，另外由于先遍历的I，已经计入了I的值，因此IV，IX需要减去I，分别为3和8。
```
class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        d={'I':1,'IV':3,'V':5,'IX':8,'X':10,'XL':30,'L':50,'XC':80,'C':100,'CD':300,'D':500,'CM':800,'M':1000}
        ans=0
        for i,n in enumerate(len(s)):
            ans+=d.get(s[max(i-1,0):i+1],d(i))
        return ans
```
这种解决方法非常简洁，每次判断i和i-1这两个连续字符，为了把i=0的情况也融入进去，因此加入了max函数，对i-1和0取较大值，当i=0时，就只计算s[0]对应的value。
另外还有个值得一提的小地方，利用字典的get方法，d.get(key,errorvalue)，如果在字典里没有发现指定的key，则返回指定值errorvalue，利用这一特性，省去了if的判断。