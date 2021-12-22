# [233. 数字 1 的个数](https://leetcode-cn.com/problems/number-of-digit-one/)

难度困难279收藏分享切换为英文接收动态反馈

给定一个整数 `n`，计算所有小于等于 `n` 的非负整数中数字 `1` 出现的个数。

 

**示例 1：**

```
输入：n = 13
输出：6
```

**示例 2：**

```
输入：n = 0
输出：0
```

 

**提示：**

- `0 <= n <= 2 * 109`



思路：

统计出每一的位上1出现的个数，累加起来就是1出现的总个数。
num = 31456
现在统计百位上1出现的次数。
将num分成两部分（根据百位），a = 314，b=56。
此时a的个位是4（即num的百位是4），此时该为出现1的次数为：31*100次。
假设a的个位数是x，
当x > 1时，百位出现1的次数：(a / 10 + 1) * 100
当x = 1时，百位出现1的次数：(a / 10 ) * 100 + b + 1 （0~b）
当x = 0时，百位出现1的次数：(a / 10 ) * 100 
根据规律，可以分为两类，一类x >= 2；一类0 <= x < 2，用一个表达式写出：
(a+8) / 10 * 100 ，再将x = 1的特殊情况写入表达式：(a+8) / 10 * 100 + (a % 10 == 1 ) * (b + 1)

~~~java
class Solution {
    public int countDigitOne(int n) {
        if (n == 0) return 0;
        int res = 0;
        for (int i = 1; i <= n; i *= 10) {
            int a = n / i, b = n % i;
            res += (a + 8) / 10 * i + (a % 10 != 1 ? 0 : (b + 1));
        }
        return res;
    }
}
~~~





# [1. 两数之和](https://leetcode-cn.com/problems/two-sum/)

给定一个整数数组 `nums` 和一个整数目标值 `target`，请你在该数组中找出 **和为目标值** *`target`* 的那 **两个** 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

你可以按任意顺序返回答案。

 

**示例 1：**

```
输入：nums = [2,7,11,15], target = 9
输出：[0,1]
解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。
```

**示例 2：**

```
输入：nums = [3,2,4], target = 6
输出：[1,2]
```

**示例 3：**

```
输入：nums = [3,3], target = 6
输出：[0,1]
```

 

**提示：**

- `2 <= nums.length <= 104`
- `-109 <= nums[i] <= 109`
- `-109 <= target <= 109`
- **只会存在一个有效答案**



思路1：暴力求解

~~~java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = 0; j < nums.length; j++) {
                if(i==j) continue;
                if(nums[i]+nums[j]==target) return new int[]{i, j};
            }
        }
        return null;
    }
}
~~~



思路2：利用字典也就是HashMap求解

~~~java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            map.put(nums[i], i);
        }

        for (int i = 0; i < nums.length; i++) {
            int k = target - nums[i];
            if (map.get(k) != null&&map.get(k)!=i) {
                return new int[]{i, map.get(k)};
            }
        }
        return null;
    }
}
~~~





# [2. 两数相加](https://leetcode-cn.com/problems/add-two-numbers/)

给你两个 **非空** 的链表，表示两个非负的整数。它们每位数字都是按照 **逆序** 的方式存储的，并且每个节点只能存储 **一位** 数字。

请你将两个数相加，并以相同形式返回一个表示和的链表。

你可以假设除了数字 0 之外，这两个数都不会以 0 开头。

 

**示例 1：**

![img](https://gitee.com/gu097/note/raw/master/img/addtwonumber1.jpg)

```java
输入：l1 = [2,4,3], l2 = [5,6,4]
输出：[7,0,8]
解释：342 + 465 = 807.
```

**示例 2：**

```
输入：l1 = [0], l2 = [0]
输出：[0]
```

**示例 3：**

```
输入：l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
输出：[8,9,9,9,0,0,0,1]
```

 

**提示：**

- 每个链表中的节点数在范围 `[1, 100]` 内
- `0 <= Node.val <= 9`
- 题目数据保证列表表示的数字不含前导零



思路：设置一个进位标志j，每一次相加都加上j。

~~~java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode res = new ListNode(0);
        ListNode r = res;
        int j = 0;

        while (l1 != null || l2 != null) {
            int v1 = l1 == null ? 0 : l1.val;
            int v2 = l2 == null ? 0 : l2.val;

            int val = v1 + v2 + j;
            ListNode nl = new ListNode(val % 10);
            j = val / 10;

            r.next = nl;
            r = r.next;

            if(l1!=null) l1 = l1.next;
            if(l2!=null) l2 = l2.next;
        }

        if(j==1)
            r.next = new ListNode(1);

        res = res.next;
        return res;
    }

    public static void  ListAdd(ListNode l,int val){
        while (l.next!=null) l = l.next;
        l.next = new ListNode(val, null);
    }
}

class ListNode {
    int val;
    ListNode next;

    ListNode() {
    }

    ListNode(int val) {
        this.val = val;
    }

    ListNode(int val, ListNode next) {
        this.val = val;
        this.next = next;
    }

    @Override
    public String toString() {
        String s = "[";
        ListNode t=this;
        while (t.next != null) {
            s += t.val + ",";
            t = t.next;
        }
        s = s + t.val + "]";
        return s;
    }
}
~~~

# [3. 无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

难度中等6171收藏分享切换为英文接收动态反馈

给定一个字符串 `s` ，请你找出其中不含有重复字符的 **最长子串** 的长度。

 

**示例 1:**

```
输入: s = "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

**示例 2:**

```
输入: s = "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```

**示例 3:**

```
输入: s = "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```

**示例 4:**

```
输入: s = ""
输出: 0
```

 

**提示：**

- `0 <= s.length <= 5 * 104`
- `s` 由英文字母、数字、符号和空格组成



解法1：穷举，效率低

基本思想就是i=0；i<s.length();i++，每一次从i开始向后探测，发现重复字符后停止，记下探测长度。取最大长度。

~~~java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int max=0;
        char[] cs = s.toCharArray();

        for (int i = 0; i < cs.length; i++) {
            int count=0;
            HashMap<Character, Integer> map = new HashMap<Character, Integer>();
            for (int j = i; j < cs.length; j++) {
                if(map.put(cs[j],0)==null) {
                    count++;
                    continue;
                }
                break;
            }
            if(count>max) max = count;
        }
        return max;
    }
}
~~~



解法2：滑动窗口

~~~java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        if(s.length()<=1) return s.length();
        int left=0;//窗口左边界
        int max = 0;//最大一次取到的窗口大小
        Map<Character, Integer> map = new HashMap<Character, Integer>();
        for (int i = 0; i < s.length(); i++) {
            if(map.containsKey(s.charAt(i))){
                //例如abba，假设第i个元素在以前出现过，但不是在目前的窗口（left~i-1）中，
                // 那么left不需要数值，也就是说窗口不需要滑动
                left = Math.max(map.get(s.charAt(i)) + 1, left);
            }
            map.put(s.charAt(i), i);
            max = Math.max(i - left + 1, max);
        }
        return max;
    }
}
~~~



收获：滑动窗口算法！！！

什么是滑动窗口？

例如字符串abcabc，left=0，向后探测，队列里逐渐加入字符，队列为abc时，加入了a，此时后面前面已经有了字符a，怎么使得队列没有重复字符串呢？需要将当前队列向右滑动，也就是left++，这样，当前队列（left~i）的字符就是bca。

# [4. 寻找两个正序数组的中位数](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/)

给定两个大小分别为 `m` 和 `n` 的正序（从小到大）数组 `nums1` 和 `nums2`。请你找出并返回这两个正序数组的 **中位数** 。

 

**示例 1：**

```
输入：nums1 = [1,3], nums2 = [2]
输出：2.00000
解释：合并数组 = [1,2,3] ，中位数 2
```

**示例 2：**

```
输入：nums1 = [1,2], nums2 = [3,4]
输出：2.50000
解释：合并数组 = [1,2,3,4] ，中位数 (2 + 3) / 2 = 2.5
```

**示例 3：**

```
输入：nums1 = [0,0], nums2 = [0,0]
输出：0.00000
```

**示例 4：**

```
输入：nums1 = [], nums2 = [1]
输出：1.00000
```

**示例 5：**

```
输入：nums1 = [2], nums2 = []
输出：2.00000
```

 

**提示：**

- `nums1.length == m`
- `nums2.length == n`
- `0 <= m <= 1000`
- `0 <= n <= 1000`
- `1 <= m + n <= 2000`
- `-106 <= nums1[i], nums2[i] <= 106`

 

**进阶：**你能设计一个时间复杂度为 `O(log (m+n))` 的算法解决此问题吗？

解法：正常找第k大的数，中位数要求平均值，就找k与k+1的值。

k是中位数下标。

~~~java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        boolean tow=false;
        int k;
        if ((nums1.length + nums2.length) % 2 == 0) {
            k = (nums1.length + nums2.length) / 2;
            tow = true;
        }else
            k = (nums1.length + nums2.length) / 2 + 1;
        
        int p=0,q=0;
        for (int i = 0; i < nums1.length + nums2.length; i++) {
            int t;
            if (p >= nums1.length) {
                t = nums2[q++];
            } else if (q >= nums2.length) {
                t = nums1[p++];
            }else {
                if(nums1[p]>nums2[q]) t = nums2[q++];
                else t = nums1[p++];
            }
            
            k--;
            if(k==0&& !tow){
                return t;
            }else if(k==0&&tow) {
                int t1;
                if (p >= nums1.length) {
                    t1 = nums2[q];
                } else if (q >= nums2.length) {
                    t1 = nums1[p];
                }else {
                    t1 = Math.min(nums1[p], nums2[q]);
                }
                return (t1 + t) / 2.0;
            }
        }
        return 0;
    }
}
~~~



# [5. 最长回文子串](https://leetcode-cn.com/problems/longest-palindromic-substring/)

难度中等4149收藏分享切换为英文接收动态反馈

给你一个字符串 `s`，找到 `s` 中最长的回文子串。

 

**示例 1：**

```
输入：s = "babad"
输出："bab"
解释："aba" 同样是符合题意的答案。
```

**示例 2：**

```
输入：s = "cbbd"
输出："bb"
```

**示例 3：**

```
输入：s = "a"
输出："a"
```

**示例 4：**

```
输入：s = "ac"
输出："a"
```

 

**提示：**

- `1 <= s.length <= 1000`
- `s` 仅由数字和英文字母（大写和/或小写）组成
