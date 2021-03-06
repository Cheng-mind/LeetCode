&nbsp;
<div align='center' ><font size=9 color='red'>LeetCode刷题笔记</font></div>
&nbsp;
<div align='center' ><font size=6>画家王铁男</font></div>
&nbsp;
<div align='center' ><font size=6>2020年于北京</font></div>
&nbsp;

<div STYLE="page-break-after: always;"></div>

```c++

























                                       ::::::
                                 \\\\\\||||||//////
                             \\\\\                /////        
                           \\\\\                    /////
                         \\\\\                       /////
                        \\\\\                         /////
                        \\\\\         _oo8oo_         /////
                        \\\\\        o8888888o        /////
                        /////        88" . "88        \\\\\
                         /////       (| ^|^ |)       \\\\\
                            /////    0\  =  /0    \\\\\
                              /////___/'==='\___\\\\\
                                 .' \\|     |// '.
                                / \\|||  :  |||// \
                               / _||||| -:- |||||_ \
                              |   | \\\  -  /// |   |
                              | \_|  ''\---/''  |_/ |
                              \  .-\__  '-'  __/-.  /
                            ___'. .'  /--.--\  '. .'___
                         ."" '<  '.___\_<|>_/___.'  >' "".
                        | | :  `- \`.:`\ _ /`:.`/ -`  : | |
                        \  \ `-.   \_ __\ /__ _/   .-` /  /
                    =====`-.____`.___ \_____/ ___.`____.-`=====
                                      `=---=`
                          佛祖保佑    大厂offer    永无bug



```
<div STYLE="page-break-after: always;"></div>


[toc]
# 第一章、 数据结构
## 一、 数组
## 二、 矩阵
## 三、 字符串
## 四、 链表
## 五、 栈
## 六、 队
## 七、 树
## 八、 图
## 九、 哈希表
[1.two sum](#1)
## 十、 滑动窗口
# 第二章、 算法
## 一、 双指针
### 1. 快慢指针
### 2. 跟随指针
### 3. 相向指针
## 二、 深度优先
### 1. 树状问题
### 2. 图状问题
### 3. 搜索问题
### 4. 枚举问题
## 三、 广度优先
### 1. 树状问题
### 2. 图状问题
### 3. 搜索问题
## 四、 二分查找
### 1. 双闭区间流派
### 2. 左闭右开流派
## 五、 分治
## 六、 贪心
## 七、 动态规划
### 1. 问题类型
#### 1. 背包DP
[45. Jump Game II ](#45)
[55. Jump Game](#55)
[70. Climbing Stairs](#70)
[91. 解码方法](#91)
[121. 买卖股票的最佳时机](#121)
[122. 买卖股票的最佳时机 II](#122)
[123. 买卖股票的最佳时机 III](#123)
[188. 买卖股票的最佳时机 IV](#188)
[198. 打家劫舍](#198)
[213. 打家劫舍 II](#213)
[309. 最佳买卖股票时机含冷冻期](#309)
[322. 零钱兑换](#322)
[377. 组合总和 Ⅳ](#377)
[410. 分割数组的最大值](#410)
[416. 分割等和子集](#416)
[518. 零钱兑换 II](#518)
[714. 买卖股票的最佳时机含手续费](#714)
[739. 每日温度](#739)
#### 2. 数组DP
[53. Maximum Subarray](#53)
[62. 不同路径](#62)
[63. 不同路径 II](#63)
[64. Minimum Path Sum](#64)
[120. 三角形最小路径和](#120)
[152. 乘积最大子数组](#152)
[221. 最大正方形](#221)
[413. 等差数列划分](#413)
[485. 最大连续1的个数](#485)
[501. 二叉搜索树中的众数](#501)
[509. 斐波那契数](#509)
[562. 矩阵中最长的连续1线段](#562)
[799. 香槟塔](#799)
##### 区间DP
#### 3. 字符串DP
##### a.回文串DP
[5. Longest Palindromic Substring](#5)
[647. 回文子串](#647)
##### b. 子串DP
[44.  通配符匹配](#44)
[72. Edit Distance](#72)
[139. 单词拆分](#139)
[583. 两个字符串的删除操作](#583)
[343. 整数拆分](#343)
##### c. 序列DP
[300. 最长上升子序列](#300)
[646. 最长数对链](#646)
[1035. 不相交的线](#1035)
[1143. 最长公共子序列](#1143)
### 2. 优化方法
#### 1. 时间复杂度
#### 2. 空间复杂度
## 八、 排序
### 1. 快速排序
### 2. 计数排序
### 3. 归并排序
## 九、 位运算

<div STYLE="page-break-after: always;"></div>

<div id="1"></div>

```c++
// 1.two sum
// 哈希表 

/*

输入 <= 数组 目标值
初始化 =：哈希表（value => index）
for遍历数组：
    v 哈希表查找（目标值）：
    v     输出 => index
    v 哈希表插入（value => index）
输出 => 空

 */

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        std::unordered_map<int, int> m; // value=>index
         
        for (int index = 0; index <= (int)nums.size() - 1; index++)
        {
            if (m.find(target - nums[index]) != m.end()) // 哈希表查找
            {
                return {m[target - nums[index]], index};
            }

            m[nums[index]] = index; // 哈希表插入
        }

        return {};
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        std::unordered_map<int, int> m; // value=>index

        for (int index = 0; index <= nums.size() - 1; index++)
        {
            if (m.find(target - nums[index]) != m.end())
            {
                return {m[target - nums[index]], index};
            }

            m.insert({nums[index], index});
        }
        return {};
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 2.add two numbers
// 链表 数学（进位）

/*
 
定义结构体 =：
    值, 结构体指针
    构造函数, 重载构造函数
输入 <= 链表1 链表2
初始化 := 虚结点 尾指针（虚结点） 进位（0）
while遍历链表1 || 2
    v 计算进位
    v     real = 链表1值 + 链表2值 + 进位
    v     进位 = real / 10
    v     个位 = real % 10
    v 创建结点
    v     尾插法 + new 创建结点
    v     更新尾指针
    v 遍历链表
检查进位
    v 尾插法 + new 创建结点
输出 => 虚结点next

 */

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* dumm = new ListNode();
        ListNode* rear = dumm;
        int carry = 0;
         
        while (l1 || l2)
        {
            int l1_val = l1 ? l1->val : 0;
            int l2_val = l2 ? l2->val : 0;
            int real = l1_val + l2_val + carry;
            carry = real / 10;
            int value = real % 10;
            
            rear->next = new ListNode(value);
            rear = rear->next;
            
            if (l1)
            {
                l1 = l1->next;
            }
            
            if (l2)
            {
                l2 = l2->next;
            }
        }
        
        if (carry)
        {
            rear->next = new ListNode(carry);
        }
        
        return dumm->next;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* psDumm = new ListNode(0);
        ListNode* psRear = psDumm;
        int carry = 0;

        // step 1
        while (l1 && l2)
        {
            // get the value
            int real = l1->val + l2->val + carry;
            carry = real / 10;
            int value = real % 10;
            // create new node
            ListNode* psCurr = new ListNode(value);
            psRear->next = psCurr;
            // drive
            psRear = psRear->next;
            l1 = l1->next;
            l2 = l2->next;
        }

        // step 2
        while (l1)
        {
            // get the value
            int real = l1->val + carry;
            carry = real / 10;
            int value = real % 10;
            // create new node
            ListNode* psCurr = new ListNode(value);
            psRear->next = psCurr;
            // drive
            psRear = psRear->next;
            l1 = l1->next;
        }

        while (l2)
        {
            // get the value
            int real = l2->val + carry;
            carry = real / 10;
            int value = real % 10;
            // create new node
            ListNode* psCurr = new ListNode(value);
            psRear->next = psCurr;
            // drive
            psRear = psRear->next;
            l2 = l2->next;
        }

        // step 3
        if (0 != carry)
        {
            // create new node
            ListNode* psCurr = new ListNode(carry);
            psRear->next = psCurr;
        }

        return psDumm->next;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 3. Longest Substring Without Repeating Characters
// 哈希表 双指针（快慢指针）滑动窗口

/*

输入 <= 字符串
初始化 =：哈希表（char => index）, 结果（0）
for遍历字符串 + 快慢指针：
    v 哈希表查找（相同字符）：
    v     慢指针 = max(原慢指针， 相同字符的下标后一位)
    v 哈希表插入（char => index）
    v 结果 = max(原结果， |快指针, 慢指针|)
输出 => 结果

 */

class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        std::unordered_map<char, int> m; // char=>index
        int res = 0;
        
        for (int fast = 0, slow = 0; fast <= (int)s.size() - 1; fast++)
        {
            if (m.find(s[fast]) != m.end())
            {
                // s[fast] is duplicate, move slow to fast + 1
                slow = std::max(m[s[fast]] + 1, slow);
            }
            
            m[s[fast]] = fast;
            res = std::max(res, fast - slow + 1);
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        if ("" == s)
        {
            return 0;
        }
        
        size_t fast = 0;
        size_t slow = 0;
        int temp_len = 0;
        int len = 0;
        std::unordered_map<char, size_t> uHash;

        for (fast = 0; fast <= s.size() - 1; fast++)
        {
            // meet repeating characters
            if (uHash.find(s[fast]) != uHash.end() && uHash[s[fast]] >= slow)
            {
                slow = uHash[s[fast]] + 1;
                temp_len = fast - slow; // 重新开始计算长度
            } 

            // template
            uHash[s[fast]] = fast;
            temp_len++;
            len = len > temp_len ? len : temp_len;
        }

        return len;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="5"></div>

```c++

// 5. Longest Palindromic Substring
// 动态规划 马拉车 双指针（相向指针）

/*

输入 <= 字符串
初始化 =：二维数组DP（false）, 子串起始下标（0），子串长度（0）
for遍历二维数组行（从下到上）：
    for遍历二维数组列（从左到右）：
        v 行列值相同：
        v     主对角线：dp[row][col] = true
        v     相邻：dp[row][col] = true
        v     上三角：dp[row][col] = dp[下一行][上一列]
        v 是回文串 且 回文串长度更大：
        v     子串起始下标 = 行标
        v     子串长度 = |行， 列|
输出 => 子串

 */
class Solution {
public:
    string longestPalindrome(string s) {
        if ("" == s)
        {
            return "";
        }

        vector<vector<bool>> dp(s.size(), vector<bool>(s.size(), false));

        int start = 0;
        int length = 0;

        for (int row = s.size() - 1; row >= 0; row--)
        {
            for (int col = row; col <= s.size() - 1; col++)
            {
                if (s[row] == s[col])
                {
                    if (row == col) // 主对角线
                    {
                        dp[row][col] = true;
                    }
                    else if (col - row == 1) // 相邻
                    {
                        dp[row][col] = true;
                    }
                    else if (col - row > 1) // 上三角
                    {
                        dp[row][col] = dp[row + 1][col - 1];
                    }
                }

                if (dp[row][col] && length < col - row + 1)
                {
                    start = row;
                    length = col - row + 1;
                }
            }
        }
        return s.substr(start, length);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    string longestPalindrome(string s) {
        std::string res;
        std::string m_s = "#";
        res += s[0];

        for (char c : s)
        {
            m_s += c;
            m_s += "#";
        }

        for (int index = 0; index <= m_s.size() - 1; index++)
        {
            for (int left = index, right = index;
                 left >= 0 && right <= m_s.size() - 1; 
                 left--, right++)
            {
                if (m_s[left] != m_s[right])
                {
                    break;
                }

                if ('#' != m_s[left] && '#' != m_s[right])
                {
                    // 对称的肯定是奇数，((right - left + 1) + 1) / 2
                    // a#a => 2
                    // b#a#b => 3
                    if (res.size() < (right - left + 2) / 2)
                    {
                        res.clear();

                        for (int i = left; i <= right; i++)
                        {
                            if ('#' != m_s[i])
                            {
                                res += m_s[i];
                            }
                        }
                    }
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 6. ZigZag Conversion
// 数学

/*

输入 <= 字符串 行数
初始化 =: vector<字符串>（行） 结果字符串
...
输出 => 字符串

 */

class Solution {
public:
    string convert(string s, int numRows) {
        std::vector<std::string> vRes(numRows);
        std::string sRes;

        for (size_t index = 0; index <= (int)s.size() - 1;) // index在下面增加
        {
            // 向下走
            for (int row = 0; row <= numRows - 1 && index <= (int)s.size() - 1; row++)
            {
                vRes[row] += s[index++];
            }

            // 向上走
            for (int row = numRows - 2; row >= 1 && index <= (int)s.size() - 1; row--)
            {
                vRes[row] += s[index++];
            }
        }

        for (auto str : vRes)
        {
            sRes += str;
        }

        return sRes;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 7. Reverse Integer
// 数学

class Solution {
public:
    int reverse(int x) {
        long res = 0;

        while (0 != x)
        {
            res = res * 10 + x % 10;
            // drive
            x /= 10;
        }

        if (static_cast <int>(res) != res)
        {
            return 0;
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 9. Palindrome Number
// 双指针（相向指针）

class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0)
        {
            return false;
        }

        string s = to_string(x);
        int len = s.size();

        for (int left = 0, right = len - 1; 
             left <= len / 2 - 1; left++, right--)
        {
            if (s[left] != s[right])
            {
                return false;
            }
        }

        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 11. Container With Most Water
// 双指针（相向指针）

class Solution {
public:
    int maxArea(vector<int>& height) {
        int left = 0;
        int right = height.size() - 1;
        int area = 0;

        while (left < right)
        {
            int h = std::min(height[left], height[right]);
            area = std::max(area, h * (right - left));

            if (height[left] == height[right])
            {
                left++;
                right--;
            }
            else if (height[left] < height[right])
            {
                left++;
            }
            else if (height[left] > height[right])
            {
                right--;
            }
        }
        return area;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 15. 3Sum
// 双指针（相向指针）

class Solution {
public:
    vector<vector<int>> threeSum(vector<int>& nums) {
        if (nums.size() < 3)
        {
            return {};
        }

        std::vector<std::vector<int>> vRes;
        std::sort(nums.begin(), nums.end());

        // 第一层循环用来遍历cur，第二层循环用来双指针往中间夹
        for (size_t index = 0; index <= nums.size() - 3 && nums[index] <= 0;)
        {
            for (size_t left = index + 1, right = nums.size() - 1; 
                 left < right; )
            {
                if (0 == nums[index] + nums[left] + nums[right])
                {
                    // add
                    std::vector<int> vRow{nums[index], nums[left], nums[right]};
                    vRes.push_back(vRow);
                    // delete repeating number
                    while (nums[left] == nums[++left] && left < right);
                    while (nums[right] == nums[--right] && left < right);
                }
                else if (0 < nums[index] + nums[left] + nums[right]) // drive
                {
                    right--;
                }
                else if (0 > nums[index] + nums[left] + nums[right]) // drive
                {
                    left++;
                }
            }
            // delete repeating index
            while (nums[index] == nums[++index] && index <= nums.size() - 3);
        }

        return vRes;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 16. 3Sum Closest
// 双指针（相向指针）

class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        int offset = INT_MAX;
        std::sort(nums.begin(), nums.end());

        for (size_t index = 0; index <= nums.size() - 3; index++)
        {
            for (size_t left = index + 1, right = nums.size() - 1; 
                 left < right; )
            {
                int temp = nums[index] + nums[left] + nums[right] - target;
                offset = (std::abs(temp) < std::abs(offset)) ? temp : offset;

                // drive
                if (0 ==  temp)
                {
                    return target;
                }
                else if (0 < temp)
                {
                    right--;
                }
                else if (0 > temp)
                {
                    left++;
                }
            }
        }

        return target + offset;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 17. Letter Combinations of a Phone Number
// 深度优先 递归

class Solution {
public:
    vector<string> letterCombinations(string digits) {
        if ("" == digits)
        {
            return {};
        }

        std::vector<string> vMap{"", "abc", "def", 
                                 "ghi", "jkl", "mno", 
                                 "pqrs", "tuv", "wxyz"};
        std::vector<string> vRes;

        dfs(vMap, vRes, digits, 0, "");

        return vRes;
    }

private:
    void dfs(const std::vector<string> vMap, 
             std::vector<string>& vRes, const std::string& digits, 
             int index, std::string vBuf) // 中间变量没有用引用
    {
        if (digits.size() == index)
        {
            vRes.push_back(vBuf);
            return;
        }

        for (char ch : vMap[digits[index] - '0' - 1])
        {
            dfs(vMap, vRes, digits, index + 1, vBuf + ch);
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 19. Remove Nth Node From End of List
// 链表 双指针（快慢指针）

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* psDumm = new ListNode(0);
        psDumm->next = head;
        ListNode* fast = psDumm;
        ListNode* slow = psDumm;

        for (int index = 0; index <= n - 1; index++)
        {
            fast = fast->next;
        }

        while (fast->next)
        {
            fast = fast->next;
            slow = slow->next;
        }

        slow->next = slow->next->next;
        return psDumm->next;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 20. Valid Parentheses
// 栈

class Solution {
public:
    bool isValid(string s) {
        if ("" == s)
        {
            return true;
        }

        std::stack<char> stChar;

        for (size_t index = 0; index <= s.size() - 1; index++)
        {
            if ('(' == s.at(index) || 
                '[' == s.at(index) || 
                '{' == s.at(index)) // push
            {
                stChar.push(s.at(index));
            }
            else if (')' == s.at(index) || 
                     ']' == s.at(index) || 
                     '}' == s.at(index)) // pop
            {
                // 不匹配时
                if (stChar.empty() || 
                    '(' == stChar.top() && ')' != s.at(index) ||
                    '[' == stChar.top() && ']' != s.at(index) ||
                    '{' == stChar.top() && '}' != s.at(index))
                {
                    return false;
                }
                // 匹配时
                stChar.pop();
            }
        }

        return stChar.empty(); 
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 21. Merge Two Sorted Lists
// 链表

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* psDumm = new ListNode(0);
        ListNode* psCurr = psDumm;

        while (l1 && l2)
        {
            psCurr->next = (l1->val < l2->val) ? l1 : l2;
            // drive
            if (l1->val < l2->val)
            {
                l1 = l1->next;
            }
            else if (l1->val >= l2->val)
            {
                l2 = l2->next;
            } 

            psCurr = psCurr->next; 
        }

        psCurr->next = (nullptr == l1) ? l2 : l1;
        return psDumm->next; 
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 22. Generate Parentheses
// 深度优先 递归 回溯

class Solution {
public:
    vector<string> generateParenthesis(int n) {
        std::vector<string> vRes;
        dfs(vRes, n, "", 1, 1);
        return vRes;
    }

private:
    void dfs(std::vector<string>& vRes, const int n, 
             std::string sBuf, int left, int right)
    {
        // 放完了
        if (n == right - 1)
        {
            vRes.push_back(sBuf);
            return;
        }
        // 先放左边
        if (left <= n)
        {
            dfs(vRes, n, sBuf + '(', left + 1, right);
        }
        // 再放右边
        if (left > right)
        {
            dfs(vRes, n, sBuf + ')', left, right + 1);
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 23. Merge k Sorted Lists
// 优先队列 链表

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */

class Solution {
public:
    struct cmp
    {
        bool operator()(ListNode* a, ListNode* b) 
        { 
            return  a->val > b->val; 
        }
    };

    ListNode* mergeKLists(vector<ListNode*>& lists) {
        if (0 == lists.size()) // 防止输入[]
        {
            return {};
        }

        ListNode* psDumm = new ListNode(0);
        ListNode* psCurr = psDumm;
        std::priority_queue<ListNode*, vector<ListNode*>, cmp> qvNode;

        for (int index = 0; index <= lists.size() - 1; index++)
        {
            if (nullptr != lists[index]) // 防止输入[[]]
            {
                qvNode.push(lists[index]); // 每个链表头放入队列
            }
        }

        while (!qvNode.empty())
        {
            // pop
            psCurr->next = qvNode.top();
            psCurr = psCurr->next;
            qvNode.pop();
            // push
            // 因为只是链表头放进去了，所以把下一个结点入队
            if (nullptr != psCurr->next)
            {
                qvNode.push(psCurr->next); 
            }
        }

        return psDumm->next;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 24. Swap Nodes in Pairs
// 链表 交换

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        ListNode* psDumm = new ListNode(0);
        psDumm->next = head;

        for (ListNode* psCurr = psDumm; 
             psCurr->next && psCurr->next->next; 
             psCurr = psCurr->next->next)
        {
            // swap 
            ListNode* cur_next = psCurr->next; // 定义临时变量，指向pair的first
            psCurr->next = cur_next->next; 
            // 第一个节点（pair对的前驱节点）指向pair的second
            cur_next->next = cur_next->next->next; 
            // 第二个节点（pair的first）指向第四个节点（pair对的后继节点）
            psCurr->next->next = cur_next; 
            // 第三个节点（pair的second）指向第二节点（pair的first）
        }

        return psDumm->next;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 25. Reverse Nodes in k-Group
// 链表 双指针（快慢指针）头插法 旋转链表

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        ListNode* psDumm = new ListNode(0);
        psDumm->next = head;

        ListNode* slow = psDumm; // 每次后面插入被反转的节点
        ListNode* fast = head; // 每次去找要被反转的节点
        ListNode* curr = nullptr; // 每次头插法的节点

        ListNode* index = head;
        // 第一层循环用来遍历链表，每到k个节点停下反转
        // length是长度，从1开始，每次增加
        // index是遍历的节点，每次往后移一个
        for (int length = 1; nullptr != index; 
             length++, index = index->next) 
        {
            // 还没到k个节点
            if (0 != (length % k))
            {
                continue;
            }
            // 到了k个节点，开始反转
            // 默认第一个排好了，所以只要k - 1次就行
            for (int count = 1; count <= k - 1; count++) 
            {   
                // 头插法，循环对称
                curr = fast->next; // 要被反转的就是fast后面的节点
                fast->next = curr->next; 
                // fast断开和curr的连接，接到curr后面的节点
                // 头插法（curr接到slow后面）
                curr->next = slow->next; // slow每k-1次才动，都接到slow后面
                slow->next = curr; // curr接到slow后面
            }
            // drive
            slow = fast; // 更新slow
            index = fast; // 更新index，因为顺序已经反了
            fast = fast->next; // 更新fast
        }

        return psDumm->next;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 26. Remove Duplicates from Sorted Array
// 双指针（快慢指针）

class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (1 >= nums.size())
        {
            return nums.size();
        }

        size_t slow = 0;
        // 快慢指针模板，用fast去遍历，slow跟着走
        for (size_t fast = 1; fast <= nums.size() - 1; fast++)
        {
            // fast每次去找不同元素，跳过相同的元素
            if (nums[slow] != nums[fast])
            {
                nums[++slow] = nums[fast];
            }
        }

        return slow + 1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 27. Remove Element
// 双指针（快慢指针）

class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        if (0 >= nums.size())
        {
            return nums.size();
        }

        size_t slow = 0;
        // 快慢指针模板，用fast去遍历，slow跟着走
        for (size_t fast = 0; fast <= nums.size() - 1; fast++)
        {
            // fast每次去找不等于val的元素，跳过val的元素
            if (val != nums[fast])
            {
                nums[slow++] = nums[fast];
            }
        }

        return slow;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 28. Implement strStr()
// 库函数

class Solution {
public:
    int strStr(string haystack, string needle) {
        return haystack.find(needle);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 31. Next Permutation
// 双指针

class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        if (1 >= nums.size())
        {
            return;
        }

        int left = 0;
        int right = 0;

        // 找左边的位置，从倒数第二个开始，往右比较
        for (left = nums.size() - 2; left >= 0; left--)
        {
            if (nums[left] < nums[left + 1])
            {
                break; // 找a到位置后跳出
            }
        }

        if (-1 == left) // 如果本来就是逆序的
        {
            std::sort(nums.begin(), nums.end());
            return; // 及时退出
        }

        
        // 找右边的位置，找到第一个比nums[left]来的小的，
        // 那么nums[right - 1]就是最接近num[left]的值
        for (right = left + 1; right <= nums.size() - 1; right++)
        {
            if (nums[left] >= nums[right])
            {
                break;
            }
        }

        // 交换左边找出来的位置和right左边的值
        int temp = nums[right - 1];
        nums[right - 1] = nums[left];
        nums[left] = temp;

        std::sort(nums.begin() + left + 1, nums.end());
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 32. Longest Valid Parentheses
// 双指针（快慢指针） 栈 动态规划

class Solution {
public:
    int longestValidParentheses(string s) {
        int fast = 0; // 去找匹配的括号
        int slow = -1; // 指向无效的那个括号，这样fast - slow刚好是总长度
        int max = 0;
        std::stack<int> sPar; // 存放的是括号的下标

        // 双指针模板，fast走
        for (fast = 0; fast <= (int)s.size() - 1; fast++)
        {
            // 遇到左括号，无论什么时候都可以入栈
            if ('(' == s.at(fast))
            {
                sPar.push(fast); // 把下标入栈
            }
            else if (')' == s.at(fast)) // 遇到右括号，考虑出栈
            {
                if (sPar.empty()) // 空栈
                {
                    slow = fast; // 因为此时fast指的右括号肯定是无效的
                }
                else if (!sPar.empty()) 
                {   
                    // 无论什么时候先出栈，因为栈里的都是左括号   
                    sPar.pop();

                    if (sPar.empty()) // 栈空，已经没有待匹配的左括号了
                    {
                        max = std::max(fast - slow, max);
                    }
                    else if (!sPar.empty()) // 栈不为空，还有未匹配的左括号
                    {
                        max = std::max(fast - sPar.top(), max);
                    }
                }
            }
        }
        return max;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int longestValidParentheses(string s) {
        int res = 0;
        std::vector<int> dp(s.size(), 0); // 当前位最大符号

        for (int index = 1; index <= (int)s.size() - 1; index++)
        {
            if (')' == s[index])
            {
                if ('(' == s[index - 1])
                {
                    if (1 == index)
                    {
                        dp[index] = 2;
                    }
                    else if (2 <= index)
                    {
                        dp[index] = dp[index - 2] + 2;
                    }
                }
                else if (')' == s[index - 1])
                {
                    if (index - dp[index - 1] > 0 && 
                        '(' == s[index - dp[index - 1] - 1])
                    {
                        if (1 == index - dp[index - 1])
                        {
                            dp[index] = dp[index - 1] + 2;
                        }
                        else if (2 <= index - dp[index - 1])
                        {
                            dp[index] = dp[index - 1] + 
                                        dp[index - dp[index - 1] - 2] + 2;
                        }
                    }
                }
            }
            res = std::max(res, dp[index]);
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 33. Search in Rotated Sorted Array
// 二分法 双指针（相向指针）

class Solution {
public:
    int search(vector<int>& nums, int target) {
        if (0 == nums.size())
        {
            return -1;
        }

        int left = 0;
        int right = nums.size() - 1;
        int mid = 0;
        // 二分法模板(left和right隔一个位置，最后在讨论)  
        while (left + 1 < right) 
        {
            mid = left + (right - left) / 2; // 二分法模板

            if (target == nums[mid]) // 二分法模板
            {
                return mid; 
            }

            if (nums[left] < nums[mid])
            {
                // 三个条件决定唯一位置
                if (nums[left] <= target && target <= nums[mid]) 
                {
                    right = mid;
                }
                else if (nums[mid] < target || target <= nums[left])
                {
                    left = mid;
                }
            }
            else if (nums[mid] < nums[left])
            {
                // 三个条件决定唯一位置
                if (nums[mid] <= target && target <= nums[right]) 
                {
                    left = mid;
                }
                else if (nums[right] <= target || target < nums[mid])
                {
                    right = mid;
                }
            }
        }

        if (target == nums[left]) // 二分法模板
        {
            return left;
        }

        if (target == nums[right]) // 二分法模板
        {
            return right;
        }

        return -1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 34. Find First and Last Position of Element in Sorted Array
// 二分法 双指针（相向指针）

class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        if (0 == nums.size())
        {
            return {-1, -1};
        }

        std::vector<int> vRes;
        int left = 0;
        int right = nums.size() - 1;
        int mid = 0;

        // 找开头
        while (left + 1 < right)
        {
            mid = left + (right - left) / 2;

            if (target == nums[mid])
            {
                right = mid;
            }
            else if (target < nums[mid])
            {
                right = mid;
            }
            else if (target > nums[mid])
            {
                left = mid;
            }
        }

        if (target == nums[left])
        {
            vRes.push_back(left);
        }
        else if (target == nums[right]) // 找最左边的,所以用else if
        {
            vRes.push_back(right);
        }
        else // 没找到target值的
        {
            return {-1, -1};
        }

        // 找结尾
        left = 0;
        right = nums.size() - 1;

        while (left + 1 < right)
        {
            mid = left + (right - left) / 2;

            if (target == nums[mid])
            {
                left = mid; 
            }
            else if (target < nums[mid])
            {
                right = mid;
            }
            else if (target > nums[mid])
            {
                left = mid;
            }
        }

        if (target == nums[right])
        {
            vRes.push_back(right);
        }
        else if (target == nums[left])
        {
            vRes.push_back(left);
        }

        return vRes;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 35. Search Insert Position
// 二分法 双指针（相向指针）

class Solution {
public:
    int searchInsert(vector<int>& nums, int target) {
        if (0 == nums.size())
        {
            return 0;
        }

        int left = 0;
        int right = nums.size() - 1;
        int mid = 0;

        while (left + 1 < right)
        {
            mid = left + (right - left) / 2;

            if (target == nums[mid])
            {
                return mid;
            }
            else if (target < nums[mid])
            {
                right = mid;
            }
            else if (target > nums[mid])
            {
                left = mid;
            }
        }

        if (target <= nums[left])
        {
            return left;
        }
        else if (nums[left] < target && target <= nums[right])
        {
            return right;
        }
        else // if (nums[right] < target)
        {
            return right + 1;
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 36. Valid Sudoku
// 枚举法 暴力法

class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
        if (0 == board.size())
        {
            return false;
        }

        // 每一行
        for (int row = 0; row <= 8; row++)
        {
            std::vector<bool> vUse(9, false);

            for (int col = 0; col <= 8; col++)
            {
                if ('.' != board[row][col]) // 有数字的情况下就去判断
                {
                    int num = board[row][col] - '1';

                    if (true == vUse[num])
                    {
                        return false;
                    }
                    else
                    {
                        vUse[num] = true;
                    }
                }
            }
        }

        // 每一列
        for (int col = 0; col <= 8; col++)
        {
            std::vector<bool> vUse(9, false);

            for (int row = 0; row <= 8; row++)
            {
                if ('.' != board[row][col])
                {
                    int num = board[row][col] - '1';

                    if (true == vUse[num])
                    {
                        return false;
                    }
                    else
                    {
                        vUse[num] = true;
                    }
                }
            }
        }

        // 每一3x3
        for (int box = 0; box <= 8; box++)
        {
            std::vector<bool> vUse(9, false);

            for (int row = 0; row <= 2; row++)
            {
                for (int col = 0; col <= 2; col++)
                {
                    if ('.' != board[(box / 3) * 3 + row][(box % 3) * 3 + col])
                    {
                        int num = \
                        board[(box / 3) * 3 + row][(box % 3) * 3 + col] - '1';

                        if (true == vUse[num])
                        {
                            return false;
                        }
                        else
                        {
                            vUse[num] = true;
                        }
                    }
                }
            }
        }

        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 37. Sudoku Solver
// 深度优先 回溯 递归 暴力法 枚举法

class Solution {
public:
    void solveSudoku(vector<vector<char>>& board) {
        dfs(board, 0, 0);
    }

private:
    bool dfs(std::vector<vector<char>>& board, int row, int col)
    {
        // 找下一个要填的j空格
        for (; row <= 8; row++)
        {
            for (col = 0; col <= 8; col++)
            {
                if ('.' == board[row][col])
                {
                    break;
                }
            }

            if ('.' == board[row][col]) // 需要再跳出一次
            {
                break;
            }
        }
        // 等价上面的
        // while (row <= 8 && col <= 8)
        // {
        //     if ('.' == board[row][col])
        //     {
        //         break;
        //     }
        //
        //     if (8 == col)
        //     {
        //         col = 0;
        //         row++;
        //     }
        //     else 
        //     {
        //         col++;
        //     }
        // }
        // 找了一次发现是row = 9时跳出第一个循环的，说明已经填完了
        if (9 == row)
        {
            return true;
        }
        // 开始填,总共有9个数字可以填
        for (int num = 1; num <= 9; num++)
        {
            if (isValid(board, row, col, num))
            {
                board[row][col] = static_cast <char>(num + '0');

                // 下一个位置dfs，一般情况下同一行，后一列，
                // 如果是第8列，那么下一个就是下一行第0列
                if (dfs(board, row + col / 8, (col + 1) % 9))
                {
                    return true;
                }

                board[row][col] = '.'; // 回溯
            }
        }

        return false; // 9个数字试了都不行，退回上一次
    }

    bool isValid(std::vector<vector<char>> board, 
                 const int row, const int col, const int num)
    {
        // check row and col
        for (int index = 0; index <= 8; index++)
        {
            if (num + '0' == board[row][index] || num + '0' == board[index][col])
            {
                return false;
            }
        }
        // check 3 x 3
        for (int i = 0; i <= 2; i++)
        {
            for (int j = 0; j <= 2; j++)
            {
                if (num + '0' == board[(row / 3) * 3 + i][(col / 3) * 3 + j])
                {
                    return false;
                }
            }
        }

        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 39. Combination Sum
// 深度优先 递归 回溯 

class Solution {
public:
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        // 39题.给定数组没有重复数字，可以重复使用给定数字，结果不能是重复的
        // 40题.给定数组有重复数字，不能重复使用给定数字，结果不能是重复的
        // 77题.给定数组没有重复数字，不能重复使用给定数字，结果不能是重复的
        if (0 == candidates.size())
        {
            return {};
        }
        std::sort(candidates.begin(), candidates.end());
        std::vector<std::vector<int>> vRes;
        std::vector<int> vBuf;

        dfs(candidates, target, vRes, vBuf, 0);

        return vRes;
    }

private:
    // 输入[2,3,6,7]
    // target = 7
    // 可以重复使用s数字
    // 每次不会从头开始，而是从当前值开始
    // [[2,2,3],[7]]
    void dfs(std::vector<int> candidates, int target, 
             std::vector<std::vector<int>>& vRes, std::vector<int>& vBuf, 
             int index)
    {
        if (0 == target)
        {
            vRes.push_back(vBuf);
            return;
        }

        if (0 > target)
        {
            return;
        }

        for (int i = index; i <= candidates.size() - 1; i++)
        {
            if (candidates[i] > target)
            {
                break;
            }

            vBuf.push_back(candidates[i]);
            dfs(candidates, target - candidates[i], vRes, vBuf, i);
            vBuf.pop_back();
        }
    }

    // 不能使用重复数字
    // [[7]]
    // 区别在于i + 1
    void dfs3(std::vector<int> candidates, int target, 
             std::vector<std::vector<int>>& vRes, std::vector<int>& vBuf, 
             int index)
    {
        if (0 == target)
        {
            vRes.push_back(vBuf);
            return;
        }

        if (0 > target)
        {
            return;
        }

        for (int i = index; i <= candidates.size() - 1; i++)
        {
            if (candidates[i] > target)
            {
                break;
            }

            // 每次i可以使用一次，下一次就不能了
            if (i != index && candidates[i] == candidates[i - 1])
            {
                continue;
            }

            vBuf.push_back(candidates[i]);
            // 从下一个元素开始
            dfs3(candidates, target - candidates[i], vRes, vBuf, i + 1); 
            
            vBuf.pop_back();
        }
    }

    // 会有重复
    // [[2,2,3],[2,3,2],[3,2,2],[7]]
    void dfs1(std::vector<int> candidates, int target, 
             std::vector<std::vector<int>>& vRes, std::vector<int>& vBuf)
    {
        if (0 == target)
        {
            vRes.push_back(vBuf);
            return;
        }

        if (0 > target)
        {
            return;
        }

        for (int n : candidates)
        {
            if (n > target)
            {
                break;
            }

            vBuf.push_back(n);
            dfs1(candidates, target - n, vRes, vBuf);
            vBuf.pop_back();
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 40. Combination Sum II
// 深度优先 递归 回溯 组合

class Solution {
public:
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        // 39题.给定数组没有重复数字，可以重复使用给定数字，结果不能是重复的
        // 40题.给定数组有重复数字，不能重复使用给定数字，结果不能是重复的
        // 77题.给定数组没有重复数字，不能重复使用给定数字，结果不能是重复的
        if (0 == candidates.size())
        {
            return {};
        }
        std::sort(candidates.begin(), candidates.end());
        std::vector<std::vector<int>> vRes;
        std::vector<int> vBuf;

        dfs(candidates, target, vRes, vBuf, 0);

        return vRes;
    }

private:
    void dfs(std::vector<int> candidates, int target, 
             std::vector<std::vector<int>>& vRes, std::vector<int>& vBuf, 
             int index)
    {
        if (0 == target)
        {
            vRes.push_back(vBuf);
            return;
        }

        if (0 > target)
        {
            return;
        }

        for (int i = index; i <= candidates.size() - 1; i++)
        {
            if (candidates[i] > target) // 减枝
            {
                break;
            }

            // 每次i可以使用一次，下一次就不能了
            // 相当于i = index时可以用一次，下次碰到一样的就不能用了
            // 并且index每次加一，已经是往后走了
            if (i != index && candidates[i] == candidates[i - 1])
            {
                continue;
            }

            vBuf.push_back(candidates[i]);
            // 从下一个元素开始
            dfs(candidates, target - candidates[i], vRes, vBuf, i + 1); 
            vBuf.pop_back();
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 41. First Missing Positive
// 键值对 原地哈希

class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        if (0 == nums.size())
        {
            return 1;
        }

        // 处理0和负数，都变成最大值，因为不需要考虑这些值
        for (int index = 0; index <= nums.size() - 1; index++)
        {
            nums[index] = 0 >= nums[index] ? INT_MAX : nums[index];
        }

        // 把每一个n以内的数字，因为要是连续的缺省的序列，最大值肯定小于n
        // 用他们的(值-1)作为key，对应位置的值转换为负数，
        // 没被转换的位置，对应的下标值+1就是缺省值
        for (int index = 0; index <= nums.size() - 1; index++)
        {
            // value为计数，因为可能已经被转成负数了
            int value = abs(nums[index]); 

            if (value <= nums.size())
            {
                // 把z对应位置的数转换为负数
                nums[value - 1] = -abs(nums[value - 1]); 
            }
        }

        // 找出缺省值
        for (int index = 0; index <= nums.size() - 1; index++)
        {
            if (nums[index] > 0)
            {
                return index + 1;
            }
        }

        // 不缺
        return nums.size() + 1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 42. Trapping Rain Water
// 双指针（相向指针） 单调栈

class Solution {
public:
    int trap(vector<int>& height) {
        if (0 == height.size())
        {
            return 0;
        }

        int max = 0;
        int leftmax = 0;
        int rightmax = 0;

        for (int left = 0, right = height.size() - 1; left < right; )
        {
            // 先找出两端最高的
            leftmax = height[left] > leftmax ? height[left] : leftmax;
            rightmax = height[right] > rightmax ? height[right] : rightmax;

            // 每次从矮的那边往中间走
            if (leftmax < rightmax)
            {
                max += leftmax - height[left++];
            }
            else if (leftmax >= rightmax)
            {
                max += rightmax - height[right--];
            }   
        }

        return max;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int trap(vector<int>& height) {
        int max = 0;
        std::stack<int> s; // 单调递减栈

        for (int index = 0; index <= (int)height.size() - 1; index++)
        {
            while (false == s.empty() && height[index] > height[s.top()])
            {
                int bottom = s.top();
                s.pop();
                if (s.empty()) break;
                int h = std::min(height[index], height[s.top()]) - height[bottom];
                int w = index - s.top() - 1;
                max += h * w;
            }
            s.push(index); 
        }
        return max;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 43. Multiply Strings
// 数学（进位）库函数

class Solution {
public:
    string multiply(string num1, string num2) {
        if ("0" == num1 || "0" == num2)
        {
            return "0";
        }

        std::string sRes(num1.size() + num2.size(), '0');
        int carry = 0;

        for (int index1 = num1.size() - 1; index1 >= 0; index1--)
        {
            for (int index2 = num2.size() - 1; index2 >= 0; index2--)
            {
                int real = (num1.at(index1) - '0') * (num2.at(index2) - '0')
                           + (sRes.at(index1 + index2 + 1) - '0') + carry;
                carry = real / 10;
                sRes[index1 + index2 + 1] = real % 10 + '0';
            }

            if (0 != carry)
            {
                sRes[index1] = carry + '0';
                carry = 0;
            }
        }

        return sRes.substr(sRes.find_first_of("123456789"));
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="44"></div>

```c++

// 44. 通配符匹配
// 动态规划 滚动数组

class Solution {
public:
    bool isMatch(string s, string p) {
        /*
        * s为行，p为列
        * 状态方程： case1: if "?", dp[i][j] = dp[i - 1][j - 1] 左上角传递给右下角
        *            case2: if "*", dp[i][j] = dp[i][j - 1] 左下角传递给右下角，作为空字符
        *                           dp[i][j] = dp[i - 1][j] 右上角传递给右下角，作为任意字符
        * 初始条件： dp[0][0] = true;
        * 边界条件： dp[0][j] = false; dp[i][0] = dp[i - 1][0]
        */
        if ("" == s && "" == p)
        {
            return true;
        }

        std::vector<std::vector<bool>> dp(p.size() + 1, std::vector<bool>(s.size() + 1, false));

        dp[0][0] = true;

        for (int row = 1; row <= p.size(); row++)
        {
            if ('*' == p[row - 1])
            {
                dp[row][0] = dp[row - 1][0];
            }
        }

        for (int row = 1; row <= p.size(); row++)
        {
            for (int col = 1; col <= s.size(); col++)
            {
                if (s[col - 1] == p[row - 1] || '?' == p[row - 1])
                {
                    dp[row][col] = dp[row - 1][col - 1];
                }
                else if ('*' == p[row - 1])
                {
                    dp[row][col] = dp[row - 1][col] || dp[row][col - 1];
                }
            }
        }

        return dp[p.size()][s.size()];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    bool isMatch(string src, string dst) {
        if ("" == src && "" == dst)
        {
            return true;
        }
        // 模板化答题
        vector<vector<bool>> dp(dst.size() + 1, vector<bool>(src.size() + 1, false));

        for (int row = 0; row <= dst.size(); row++) 
        {
            for (int col = 0; col <= src.size(); col++)
            {
                if (0 == row && 0 == col)
                {
                    dp[0][0] = true;
                }
                else if (0 == row && 0 != col)
                {
                    dp[0][col] = false;
                }
                else if (0 != row && 0 == col)
                {
                    if ('*' == dst[row - 1])
                    {
                        dp[row][0] = dp[row - 1][0];
                    }
                }
                else if (src[col - 1] == dst[row - 1] || '?' == dst[row - 1])
                {
                    dp[row][col] = dp[row - 1][col - 1];
                }
                else if ('*' == dst[row - 1])
                {
                    dp[row][col] = dp[row - 1][col] || dp[row][col - 1];
                }
            }
        }
        return dp[dst.size()][src.size()];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    bool isMatch(string src, string dst) {
        if ("" == src && "" == dst)
        {
            return true;
        }

        vector<vector<bool>> dp(2, vector<bool>(src.size() + 1, false));

        for (int row = 0; row <= dst.size(); row++) 
        {
            for (int col = 0; col <= src.size(); col++)
            {
                if (0 == row && 0 == col)
                {
                    dp[0][0] = true;
                }
                else if (0 == row && 0 != col)
                {
                    dp[0][col] = false;
                }
                else if (0 != row && 0 == col)
                {
                    if ('*' == dst[row - 1])
                    {
                        dp[row % 2][0] = dp[(row + 1) % 2][0];
                    }
                    else
                    {
                        dp[row % 2][col] = false;
                    }
                }
                else if (src[col - 1] == dst[row - 1] || '?' == dst[row - 1])
                {
                    dp[row % 2][col] = dp[(row + 1) % 2][col - 1];
                }
                else if ('*' == dst[row - 1])
                {
                    dp[row % 2][col] = dp[(row + 1) % 2][col] || dp[row % 2][col - 1];
                }
                else
                {
                    dp[row % 2][col] = false;
                }
            }
        }
        return dp[dst.size() % 2][src.size()];
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="45"></div>

```c++

// 45. Jump Game II
// 动态规划 双指针（快慢指针） 区间DP

class Solution {
public:
    int jump(vector<int>& nums) {
        if (0 == nums.size())
        {
            return 0;
        }

        int max = 0;

        for (int fast = 0, step = 0; ; 
             fast = max, step++) // 步数, fast每次到达最远处
        {
            if (fast >= nums.size() - 1)
            {
                return step; // 快指针比长度长就返回步数
            }

            // 当前用slow找出最远能到达的距离
            for (int slow = 0; slow <= fast; slow++)
            {
                max = max > slow + nums[slow] ? max : slow + nums[slow];
            }
        }

        return 0;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int jump(vector<int>& nums) {
        if (1 >= nums.size())
        {
            return 0;
        }

        int left = 0;
        int right = 0;
        int step = 0;

        for (int index = 0; index <= nums.size() - 1; index++)
        {
            right = std::max(right, index + nums[index]);

            if (right >= nums.size() - 1)
            {
                return step + 1;
            }

            if (index == left)
            {
                step++;
                left = right;
            }
        }
        return step;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 46. Permutations
// 深度优先 递归 回溯 集合（set）

class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        std::vector<std::vector<int>> vRes;
        std::vector<int> vBuf;
        std::vector<bool> vUse(nums.size(), false);
        dfs(nums, vRes, vBuf, vUse);
        return vRes;
    }
private:
    void dfs(std::vector<int> nums, 
             std::vector<std::vector<int>>& vRes, std::vector<int>& vBuf, 
             std::vector<bool>& vUse)
    {
        if (nums.size() == vBuf.size())
        {
            vRes.push_back(vBuf);
            return;
        }

        for (int index = 0; index <=nums.size() - 1; index++)
        {
            if (true == vUse[index]) // 如果这个数字被用过就不用
            {
                continue; // continue表示不用此数
            }

            vBuf.push_back(nums[index]);
            vUse[index] = true;
            dfs(nums, vRes, vBuf, vUse);
            vUse[index] = false;
            vBuf.pop_back();
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        std::vector<std::vector<int>> vRes;
        std::vector<int> vBuf;
        std::set<int> sUse;

        dfs(nums, vRes, vBuf, sUse);

        return vRes;
    }

private:
    void dfs(std::vector<int> nums, 
             std::vector<std::vector<int>>& vRes, std::vector<int>& vBuf,  
             std::set<int>& sUse)
    {
        if (nums.size() == vBuf.size())
        {
            vRes.push_back(vBuf);
            return;
        }

        for (auto num : nums)
        {
            if (sUse.end() == sUse.find(num))
            {
                vBuf.push_back(num);
                sUse.insert(num);
                dfs(nums, vRes, vBuf, sUse);
                vBuf.pop_back();
                sUse.erase(num);
            }
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 47. Permutations II
// 深度优先 递归 回溯 

class Solution {
public:
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        std::vector<std::vector<int>> vRes;
        std::vector<int> vBuf;
        std::vector<bool> vUse(nums.size(), false);

        std::sort(nums.begin(), nums.end());

        dfs(nums, vRes, vBuf, vUse);

        return vRes;
    }

private:
    // in:[1,1,2]
    // out:[[1,1,2],[1,2,1],[2,1,1]]
    void dfs(const std::vector<int> nums, 
             std::vector<std::vector<int>>& vRes, 
             std::vector<int>& vBuf, 
             std::vector<bool>& vUse)
    {
        if (vBuf.size() == nums.size()) 
        {
            vRes.push_back(vBuf);
            return;
        }

        for (int index = 0; index <= nums.size() - 1; index++)
        {
            // 为了减少嵌套，单独拎出来写
            if (true == vUse[index]) // 如果这个数字被用过就不用
            {
                continue; // continue表示不用此数
            }
            // 遇到重复的情况时，第一个不用，到第二个才用
            if (0 != index && nums[index] == nums[index - 1] 
                && true == vUse[index - 1])
            {
                continue; 
                // false == vUse[index - 1]也行，
                // 表示重复的数字第一个就用，第二个不用
            }

            vUse[index] = true;
            vBuf.push_back(nums[index]);
            dfs(nums, vRes, vBuf, vUse);
            vUse[index] = false;
            vBuf.pop_back();
        }
    }    
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 48. Rotate Image
// 数学

class Solution {
public:
    void rotate(vector<vector<int>>& matrix) {
        // 对角线翻转 a[row][col]和a[col][row]交换
        for (int row = 0; row <= matrix.size() - 1; row++)
        {
            for (int col = row + 1; col <= matrix[0].size() - 1; col++)
            {
                std::swap(matrix[row][col], matrix[col][row]);
            }
        }

        // d轴对称翻转 a[row][col]和a[row][n - 1 - col]交换
        for (int row = 0; row <= matrix.size() - 1; row++)
        {
            for (int col = 0; col <= (matrix[0].size() - 1) / 2; col++)
            {
                std::swap(matrix[row][col], matrix[row][matrix[0].size() - 1 - col]);
            }
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 49. Group Anagrams
// 哈希表 库函数

class Solution {
public:
    vector<vector<string>> groupAnagrams(vector<string>& strs) {
        std::vector<std::vector<std::string>> res;
        std::multimap<std::string, std::string> m;

        for (auto str : strs)
        {
            string key = str;
            std::sort(key.begin(), key.end());
            m.insert(make_pair(key, str));
        }

        for (auto it_m = m.begin(); 
             it_m != m.end(); 
             it_m = m.upper_bound(it_m->first))
        {
            res.push_back({});

            auto range = m.equal_range(it_m->first);
            for (auto it_k = range.first; it_k != range.second; it_k++)
            {
                res.back().push_back(it_k->second);
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 51. N皇后
// 深度优先 回溯 递归 位运算 映射

class Solution {
public:
    vector<vector<string>> solveNQueens(int n) {
        this->n = n;
        std::string s(n, '.');
        res_row.assign(n, s);
        dfs(0, 0, 0, 0);
        return res;
    }

private:
    int n;
    std::vector<std::string> res_row;
    std::vector<std::vector<std::string>> res;

    void dfs(int row, int col, int main_dia, int sub_dia)
    {
        if (row == n)
        {
            res.push_back(res_row);
            return;
        }

        for (int col_index; col_index <= n - 1; col_index++)
        {
            int pos = 1 << col_index;

            if ((pos & col) || (pos & main_dia) || (pos & sub_dia))
            {
                continue;
            }

            res_row[row][col_index] = 'Q';
            dfs(row + 1, (col | pos), (main_dia | pos) << 1, (sub_dia | pos) >> 1);
            res_row[row][col_index] = '.';
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 52. N皇后 II
// 深度优先 回溯 递归 位运算 映射

class Solution {
public:
    int totalNQueens(int n) {
        // 维护三个数组，行，主对角线，副对角线
        // 分别用三个整数表示三个数组，并且不能有重复出现
        // 位运算表示占位
        // & 表示该元素是否存在于该数组
        // | 表示添加该元素
        dfs(n, 0, 0, 0, 0);
        return count;
    }

private:
    int count = 0; // 总个数

    void dfs(int n, int row, int col, int main_diagonal, int sub_diagonal)
    {
        if (row == n) // 到最后一行下一行，说明已经填完n行了
        {
            count++;
            return ;
        }
        // 递归是每一行，for填每一列
        for (int col_index = 0; col_index <= n - 1; col_index++)
        {
            int pos = 1 << col_index; // pos映射到三个数组的位置
            // 判断是否出现在行、主对角线、副对角线上
            if ((pos & col) || (pos & main_diagonal) || (pos & sub_diagonal))
            {
                continue;
            }
            // 不存在就添加
            // 主副对角线一共有2n - 1个位置
            // 行和列只有n个位置
            // (x, y)在主对角线用x + y映射成整数(0 .. n - 1)
            // (x, y)在副对角线用x - y + n - 1映射成整数(0 .. n - 1)
            dfs(n, row + 1, (pos | col), 
                (pos | main_diagonal) << 1, 
                (pos | sub_diagonal) >> 1);
        }
    }
};

```

<div STYLE="page-break-after: always;"></div>

<div id="53"></div>

```c++

// 53. Maximum Subarray
// 动态规划

class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        std::vector<int> vDp(nums.size()); // 表示开头到当前位置的最大值
        vDp[0] = nums[0];
        int max = vDp[0];

        for (int index = 1; index <= nums.size() - 1; index++)
        {
            // 碰到前面是负数的，就不累加了
            if (0 > vDp[index - 1])
            {
                vDp[index] = nums[index];
            }
            else if (0 <= vDp[index - 1]) // 碰到是0和正数就累加
            {
                vDp[index] = nums[index] + vDp[index - 1];
            }

            max = max > vDp[index] ? max : vDp[index];
        }

        return max;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int res = 0;
        int sum = 0;

        for (int index = 0; index <= nums.size() - 1; index++)
        {
            sum = (sum > 0) ? sum + nums[index] : nums[index];
            res = max(res, sum);
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 54. 螺旋矩阵
// 矩阵

class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        if (0 == matrix.size() || 0 == matrix[0].size())
        {
            return {};
        }

        int direction = 0;
        int top = 0;
        int right = matrix[0].size() - 1;
        int bottom = matrix.size() - 1;
        int left = 0;

        std::vector<int> res;

        while (top <= bottom && left <= right)
        {
            switch (direction)
            {
                case 0: // 向右
                    for (int index = left; index <= right; index++)
                    {
                        res.push_back(matrix[top][index]);
                    } 
                    top++;  
                    break;
                case 1: // 向下
                    for (int index = top; index <= bottom; index++)
                    {
                        res.push_back(matrix[index][right]);
                    }
                    right--;
                    break;
                case 2: // 向左
                    for (int index = right; index >= left; index--)
                    {
                        res.push_back(matrix[bottom][index]);
                    }
                    bottom--;
                    break;
                case 3: // 向上
                    for (int index = bottom; index >= top; index--)
                    {
                        res.push_back(matrix[index][left]);
                    }
                    left++;
                    break;
                default:
                    break;
            }
            direction = (++direction) % 4;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="55"></div>

```c++

// 55. Jump Game
// 动态规划 双指针（快慢指针）

class Solution {
public:
    bool canJump(vector<int>& nums) {
        /*
        * 状态转移: f[j] = OR(0 <= i < j){f[i] AND i + a[i] >= j}
        * 初始条件：f[0] = true
        * 边界情况：无
        */
        
        // 双指针（跟随指针）
        int slow = 0;
        int fast = 1;
        int len = nums.size();

        // 每个元素表示能不能跳到
        std::vector<bool> vDp(len, false);
        vDp[0] = true;

        for ( ; fast <= len - 1; fast++)
        {
            for (slow = 0; slow < fast; slow++)
            {
                // 上一个节点可以跳得到，
                // 并且上一个节点加上它能到达的距离大于现在位置
                if (vDp[slow] && slow + nums[slow] >= fast)
                {
                    vDp[fast] = true;
                    break;
                }
            }
        }

        return vDp[len - 1];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    bool canJump(vector<int>& nums) {
        if (1 >= nums.size())
        {
            return true;
        }

        int right = 0;
        int left = 0;

        for (int index = 0; index <= nums.size() - 1; index++)
        {
            right = max(right, index + nums[index]);

            if (right <= index && right != nums.size() - 1)
            {
                return false;
            }
        }
        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 56. Merge Intervals
// 区间问题

class Solution {
public:
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        int len = intervals.size();
        std::vector<int> vLeft(len);
        std::vector<int> vRight(len);
        std::vector<std::vector<int>> vRes;

        for (int row = 0; row <= len - 1; row++)
        {
            vLeft[row] = intervals[row][0];
            vRight[row] = intervals[row][1];
        }

        std::sort(vLeft.begin(), vLeft.end());
        std::sort(vRight.begin(), vRight.end());

        for (int row = 0; row <= len - 1; row++)
        {
            // 初始化本行开头,即找开头
            std::vector<int> vBuf({vLeft[row]});
            // 去下一行找当前开头的结尾，
            // 如果下一行的开头小于本行的结尾，说明断了，保留本行结尾
            for ( ; row <= len - 2; row++) // 比较到倒数第二行
            {
                if (vRight[row] < vLeft[row + 1])
                {
                    break;
                }
            }
            // 填结尾
            vBuf.push_back(vRight[row]);
            vRes.push_back(vBuf);
        }
        return vRes;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 57. 插入区间
// 区间问题

class Solution {
public:
    vector<vector<int>> insert(vector<vector<int>>& intervals, 
                               vector<int>& newInterval) {
        int len = (int)intervals.size();
        std::vector<std::vector<int>> vRes;
        // 处理前面的
        int row = 0;
        for ( ; row <= len - 1; row++)
        {
            // 本行结尾大于区间开头，说明这一行是和区间重合的
            if (intervals[row][1] >= newInterval[0]) 
            {
                break;
            }

            vRes.push_back(intervals[row]);
        }

        if (row == len) // 防止new是最后一段
        {
            vRes.push_back(newInterval);
            return vRes;
        }

        // 找出区间重合的开头
        int left = std::min(intervals[row][0], newInterval[0]); 

        // 找出区间重合的结尾
        for ( ; row <= len - 1; row++)
        {
            if (intervals[row][0] > newInterval[1])
            {
                break;
            }
        }

        if (0 == row) // 新区间在最开头
        {
            vRes.push_back(newInterval);
        }
        else
        {
            int right = std::max(intervals[row - 1][1], newInterval[1]);
            vRes.push_back({left, right});  
        }

        // 处理后面的
        for ( ; row <= len - 1; row++)
        {
            vRes.push_back(intervals[row]);
        }   

        return vRes;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 61. Rotate List
// 链表 双指针（快慢指针）

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        if (nullptr == head)
        {
            return nullptr;
        }

        ListNode* fast = head;
        ListNode* slow = head;
        int len = 0;

        // 求链表长度
        while (fast)
        {
            len++;
            fast = fast->next;
        }

        fast = head;

        // fast先移动k个位置
        for (int count = 1; count <= k % len; count++)
        {
            fast = fast->next;
        }
        // fast,slow一起往后移动
        while (fast->next)
        {
            slow = slow->next; // slow指向要被移动的前一个节点
            fast = fast->next; // fast移动到最后一个节点
        }

        fast->next = head;
        head = slow->next;
        slow->next = nullptr;
        return head;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="62"></div>

```c++

// 62. 不同路径
// 动态规划 滚动数组

class Solution {
public:
    int uniquePaths(int m, int n) {
        std::vector<int> dp(m, 0);
        dp[0] = 1;

        for (int row = 0; row <= n - 1; row++)
        {
            for (int col = 0; col <= m - 1; col++)
            {
                if (0 == row && 0 == col)
                {
                    continue;
                }

                if (0 == col)
                {
                   continue;
                }

                dp[col] = dp[col] + dp[col - 1]; 
            }
        }
        return dp[m - 1];
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="63"></div>

```c++

// 63. 不同路径 II
// 动态规划 滚动数组

class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        // 因为只有两个方向，每个位置都唯一确定方案
        // 若能上下左右走，那么最后位置不确定，要用搜索
        // 滚动数组优化空间复杂度
        // 因为转移方程具有对称性
        // 再优化成一维数组优化空间
        
        std::vector<std::vector<int>> 
        dp(obstacleGrid.size(), std::vector<int>(obstacleGrid[0].size(), 0));
        for (int row = 0; row <= obstacleGrid.size() - 1; row++)
        {
            for (int col = 0; col <= obstacleGrid[0].size() - 1; col++)
            {
                if (0 == row && 0 == col) // 初始条件
                {
                    if (1 == obstacleGrid[0][0])
                    {
                        return 0;
                    }
                    else
                    {
                        dp[0][0] = 1;
                    }
                }
                else if (0 == row) // 边界条件
                {
                    dp[0][col] = (0 == obstacleGrid[0][col] && dp[0][col - 1]) ? 
                                 1 : 0;
                }
                else if (0 == col) // 边界条件
                {
                    dp[row][0] = (0 == obstacleGrid[row][0] && dp[row - 1][0]) ? 
                                 1 : 0;
                }
                else // 状态转移
                {
                    dp[row][col] = (0 == obstacleGrid[row][col]) ? 
                                   dp[row - 1][col] + dp[row][col - 1] : 0;
                }
            }
        }
        return dp[obstacleGrid.size() - 1][obstacleGrid[0].size() - 1];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        // 因为只有两个方向，每个位置都唯一确定方案
        // 若能上下左右走，那么最后位置不确定，要用搜索
        // 滚动数组优化空间复杂度
        // 因为转移方程具有对称性
        // 再优化成一维数组优化空间
        
        std::vector<std::vector<int>> 
        dp(2, std::vector<int>(obstacleGrid[0].size(), 0));

        for (int row = 0; row <= obstacleGrid.size() - 1; row++)
        {
            for (int col = 0; col <= obstacleGrid[0].size() - 1; col++)
            {
                if (0 == row && 0 == col) // 初始条件
                {
                    if (1 == obstacleGrid[0][0])
                    {
                        return 0;
                    }
                    else
                    {
                        dp[0][0] = 1;
                    }
                }
                else if (0 == row) // 边界条件
                {
                    dp[0][col] = 
                    (0 == obstacleGrid[0][col] && dp[0][col - 1]) ? 1 : 0;
                }
                else if (0 == col) // 边界条件
                {
                    dp[row % 2][0] = 
                    (0 == obstacleGrid[row][0] && dp[(row + 1) % 2][0]) ? 1 : 0;
                }
                else // 状态转移
                {
                    dp[row % 2][col] = (0 == obstacleGrid[row][col]) ? 
                    dp[(row + 1) % 2][col] + dp[row % 2][col - 1] : 0;
                }
            }
        }
        return dp[(obstacleGrid.size() - 1) % 2][obstacleGrid[0].size() - 1];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        // 因为只有两个方向，每个位置都唯一确定方案
        // 若能上下左右走，那么最后位置不确定，要用搜索
        // 滚动数组优化空间复杂度
        // 因为转移方程具有对称性
        // 再优化成一维数组优化空间
        
        std::vector<int> dp(obstacleGrid[0].size(), 0);

        for (int row = 0; row <= obstacleGrid.size() - 1; row++)
        {
            for (int col = 0; col <= obstacleGrid[0].size() - 1; col++)
            {
                if (0 == row && 0 == col)
                {
                    if (1 == obstacleGrid[0][0])
                    {
                        return 0;
                    }
                    else
                    {
                        dp[0] = 1;
                    }
                }
                else if (0 == col)
                {
                    dp[0] = (1 == obstacleGrid[row][col]) ? 0 : dp[0];
                }
                else // 上一列加上本身
                {
                    dp[col] = (1 == obstacleGrid[row][col]) ? 
                              0 : dp[col] + dp[col - 1];
                }
            }
        }
        return dp[obstacleGrid[0].size() - 1];
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="64"></div>

```c++

// 64. Minimum Path Sum
// 动态规划

class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        /*
        * 状态方程：dp[i][j] = grid[i][j] + MIN{dp[i - 1][j] + dp[i][j - 1]}
        * 边界情况：dp[i][0] = grid[i][0] + dp[i - 1][0]; 
        *          dp[0][j] = grid[0][j] + dp[0][i - 1]
        * 初始条件：dp[0][0] = grid[0][0]
        */

        std::vector<std::vector<int>> vDp(grid.size(), std::vector<int>(grid[0].size()));

        for (int row = 0; row <= grid.size() - 1; row++)
        {
            for (int col = 0; col <= grid[0].size() - 1; col++)
            {
                if (0 == row && 0 == col) // 初始条件
                {
                    vDp[row][col] = grid[0][0];
                }
                else if (0 == row) // 边界条件
                {
                    vDp[row][col] = grid[row][col] + vDp[row][col - 1];
                }
                else if (0 == col) // 边界条件
                {
                    vDp[row][col] = grid[row][col] + vDp[row - 1][col];
                }
                else // 状态转移
                {
                    vDp[row][col] = grid[row][col] + 
                                    min(vDp[row - 1][col], vDp[row][col - 1]);
                }
            }  
        }

        return vDp[grid.size() - 1][grid[0].size() - 1];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 69. x 的平方根
// 数学 双指针（相向指针） 二分法

class Solution {
public:
    int mySqrt(int x) {
        int left = 0;
        int right = x / 2 + 1;
        // 双闭流派

        while (left <= right) 
        {
            long mid = left + (right - left) / 2;

            if (mid * mid == x)
            {
                return mid;
            }
            else if (mid * mid > x)
            {
                right = mid - 1;
            }
            else if (mid * mid < x)
            {
                left = mid + 1;
            }
        }
        return left - 1; // left会到mid右边去，所以减一
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int mySqrt(int x) {
        if (x <= 1)
        {
            return x;
        }

        int left = 0;
        int right = x / 2 + 1;

        while (left + 1 < right) 
        {
            long mid = left + (right - left) / 2;

            if (mid * mid == x)
            {
                return mid;
            }
            else if (mid * mid > x)
            {
                right = mid;
            }
            else if (mid * mid < x)
            {
                left = mid;
            }
        }
        return left; // left会指向mid
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="70"></div>

```c++

// 70. Climbing Stairs
// 动态规划

class Solution {
public:
    int climbStairs(int n) {
        /*
        * 状态方程： dp[i] = dp[i - 1] + dp[i - 2]
        * 初始条件： dp[0] = 1; dp[1] = 1; dp[2] = 2;
        */

        std::vector<int> vRes(n + 2); // 至少分配2个位置
        vRes[0] = 1;
        vRes[1] = 1;
        vRes[2] = 2;

        for (int floor = 3; floor <= n; floor++)
        {
            vRes[floor] = vRes[floor - 1] + vRes[floor - 2];
        }

        return vRes[n];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int climbStairs(int n) {
        if (2 >= n)
        {
            return n;
        }

        int pre1 = 1;
        int pre2 = 2;
        int res = 0;

        for (int i = 3; i <= n; i++)
        {
            res = pre1 + pre2; 
            pre1 = pre2; 
            pre2 = res;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="72"></div>

```c++

// 72. Edit Distance
// 动态规划 滚动数组

class Solution {
public:
    int minDistance(string word1, string word2) {
        /*
        * 状态方程：case1:word1和word2天然相等 => dp[i][j] = dp[i - 1][j - 1]
        *          case2:word1由插入、删除和替换变成
        *                word2 => dp[i][j] = 1 + MIN{dp[i - 1][j], 
        *                                            dp[i][j - 1], 
        *                                            dp[i - 1][j - 1]}
        * 边界条件：dp[0][j] = j, dp[i][0] = i
        * 初始条件：dp[0][0] = 0 （空出一格）
        */

        // 每个结点为一维数组的顺序表
        // 多一位为空字符
        std::vector<std::vector<int>> vDp(word1.size() + 1, std::vector<int>(word2.size() + 1));

        // 初始条件、边界条件
        for (int row = 0; row <= word1.size(); row++)  
        {
            vDp[row][0] = row;
        }

        for (int col = 0; col <= word2.size(); col++)
        {
            vDp[0][col] = col;
        }

        // 状态转移方程
        for (int row = 1; row <= word1.size(); row++ )
        {
            for (int col = 1; col <= word2.size(); col++ )
            {
                if (word1[row - 1] == word2[col - 1])
                {
                    vDp[row][col] = vDp[row - 1][col - 1];
                }
                else
                {
                    vDp[row][col] = 1 + std::min(vDp[row][col - 1], 
                                        std::min(vDp[row - 1][col], 
                                                 vDp[row - 1][col - 1]));
                }
            }
        }

        return vDp[word1.size()][word2.size()];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int minDistance(string word1, string word2) {
        // 模板化
        std::vector<std::vector<int>> dp(word1.size() + 1, std::vector<int>(word2.size() + 1, 0));

        for (int row = 0; row <= word1.size(); row++) 
        {
            for (int col = 0; col <= word2.size(); col++)
            {
/***** ***** ***** ***** ***** 添加其他操作 ***** ***** ***** ***** *****/
                if (0 == row && 0 == col)
                {
                    dp[0][0] = 0;
                }
                else if (0 == row && 0 != col)
                {
                    dp[0][col] = col;
                }
                else if (0 != row && 0 == col)
                {
                    dp[row][0] = row;
                }
                else if (word1[row - 1] == word2[col - 1])
                {
                    dp[row][col] = dp[row - 1][col - 1];
                }
                else
                {
                    dp[row][col] = 1 + min(dp[row - 1][col - 1], 
                                       min(dp[row][col - 1], dp[row - 1][col]));
                }
/***** ***** ***** ***** ***** 添加其他操作 ***** ***** ***** ***** *****/
            }
        }
        return dp[word1.size()][word2.size()];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int minDistance(string word1, string word2) {
        // 模板化
        std::vector<std::vector<int>> dp(2, std::vector<int>(word2.size() + 1, 0));

        for (int row = 0; row <= word1.size(); row++) 
        {
            for (int col = 0; col <= word2.size(); col++)
            {
/***** ***** ***** ***** ***** 添加其他操作 ***** ***** ***** ***** *****/
                if (0 == row && 0 == col)
                {
                    dp[0][0] = 0;
                }
                else if (0 == row && 0 != col)
                {
                    dp[0][col] = col;
                }
                else if (0 != row && 0 == col)
                {
                    dp[row % 2][0] = row;
                }
                else if (word1[row - 1] == word2[col - 1])
                {
                    dp[row % 2][col] = dp[(row + 1) % 2][col - 1];
                }
                else
                {
                    dp[row % 2][col] = 1 + min(dp[(row + 1) % 2][col - 1], 
                                           min(dp[row % 2][col - 1], 
                                               dp[(row + 1) % 2][col]));
                }
/***** ***** ***** ***** ***** 添加其他操作 ***** ***** ***** ***** *****/
            }
        }
        return dp[word1.size() % 2][word2.size()];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 74. 搜索二维矩阵
// 二分法 数组 矩阵

class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        if (0 == matrix.size() || 0 == matrix[0].size())
        {
            return false;
        }
        // 从右上角开始
        int row = 0;
        int col = matrix[0].size() - 1;

        while (row <= matrix.size() - 1 && col >= 0)
        {
            if (target == matrix[row][col])
            {
                return true;
            }
            else if (target > matrix[row][col])
            {
                row++;
            }
            else if (target < matrix[row][col])
            {
                col--;
            }
        }
        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        if (0 == matrix.size() || 0 ==  matrix[0].size())
        {
            return false;
        }

        // 先从最后一列找出第几行
        int left = 0;
        int right = matrix.size() - 1;
        int row = -1;

        while (left + 1 < right)
        {
            int mid = left + (right - left) / 2;

            if (target == matrix[mid][matrix[0].size() - 1])
            {
                return true;
            }
            else if (target < matrix[mid][matrix[0].size() - 1])
            {
                right = mid;
            }
            else if (target > matrix[mid][matrix[0].size() - 1])
            {
                left = mid;
            }
        }

        if (target <= matrix[left][matrix[0].size() - 1])
        {
            row = left; // 此时下面的条件肯定成立，所以要用else if
        }
        else if (target <= matrix[right][matrix[0].size() - 1])
        {
            row = right;
        }
        else
        {
            return false;
        }

        // 再找出第几列
        left = 0;
        right = matrix[0].size() - 1;

        while (left + 1 < right)
        {
            int mid = left + (right - left) / 2;

            if (target == matrix[row][mid])
            {
                return true;
            }
            else if (target < matrix[row][mid])
            {   
                right = mid;
            }
            else if (target > matrix[row][mid])
            {
                left = mid;
            }
        }

        if (target == matrix[row][left] || target == matrix[row][right])
        {
            return true;
        }
        else
        {
            return false;
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 75. 颜色分类
// 计数排序 划分排序

class Solution {
public:
    void sortColors(vector<int>& nums) {
        std::vector<int> v(3, 0);

        for (auto num : nums)
        {
            v[num]++;
        }

        nums.clear();

        for (int count = 0; count <= 2; count++)
        {
            while (v[count]--)
            {
                nums.push_back(count);
            }
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    void sortColors(vector<int>& nums) {
        // 把数组分成[0,zero),[zero, one),(one, two]三个数段
        // 当nums[one] == 0, zero+=1,one+=1,two不变
        // 当nums[one] == 1, zero不变,one+=1,two不变
        // 当nums[one] == 2, zero不变,one不变,two-=1
        int zero = 0;
        int one = 0;
        int two = nums.size() - 1;

        while (one <= two)
        {
            if (0 == nums[one])
            {
                std::swap(nums[one++], nums[zero++]);
            }
            else if (1 == nums[one])
            {
                one++;
            }
            else if (2 == nums[one])
            {
                std::swap(nums[one], nums[two--]);
            }
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 77. 组合
// 深度优先 递归 回溯

class Solution {
public:
    vector<vector<int>> combine(int n, int k) {
        // 39题.给定数组没有重复数字，可以重复使用给定数字，结果不能是重复的
        // 40题.给定数组有重复数字，不能重复使用给定数字，结果不能是重复的
        // 77题.给定数组没有重复数字，不能重复使用给定数字，结果不能是重复的
        std::vector<std::vector<int>> vRes;
        std::vector<int> vBuf;
        dfs(n, k, vRes, vBuf, 1);
        return vRes;
    }
private:
    void dfs(int n, int k, 
             std::vector<std::vector<int>>& vRes, std::vector<int>& vBuf,
             int index)
    {
        if (0 == k)
        {
            vRes.push_back(vBuf);
            return;
        }

        for (int i = index; i <= n; i++)
        {
            vBuf.push_back(i);
            dfs(n, k - 1, vRes, vBuf, i + 1);
            vBuf.pop_back();
        }
    }    
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 78. 子集
// 深度优先 递归 回溯

class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        std::vector<std::vector<int>> vRes;
        std::vector<int> vBuf;
        dfs(nums, vRes, vBuf, 0);
        return vRes;
    }

private:
    void dfs(std::vector<int>& nums,
             std::vector<std::vector<int>>& vRes, std::vector<int>& vBuf,
             int index)
    {
        vRes.push_back(vBuf);

        for (int i = index; i <= nums.size() - 1; i++)
        {
            vBuf.push_back(nums[i]);
            dfs(nums, vRes, vBuf, i + 1);
            vBuf.pop_back();
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 82. 删除排序链表中的重复元素 II
// 链表 双指针（快慢指针）

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if (nullptr == head)
        {
            return nullptr;
        }

        ListNode* dummy = new ListNode(0);
        dummy->next = head;

        ListNode* fast = head->next; // 找不重复的
        ListNode* slow = head; // 表示重复的
        ListNode* pre = dummy; // 存不重复的

        while (fast)
        {
            while (fast && slow->val == fast->val)
            {
                // fast找不重复的
                fast = fast->next;
            }

            if (slow->next == fast) // 无重复
            {
                pre = slow;
                slow = fast;
            }
            else if (slow->next != fast) // 有重复
            {
                delete pre->next;
                pre->next = fast;
                slow = fast;
            }

            if (fast)
            {
                fast = fast->next;
            }
        }
        return dummy->next;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 83. 删除排序链表中的重复元素
// 双指针（快慢指针） 链表

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        if (nullptr == head)
        {
            return nullptr;
        }

        ListNode* fast = head->next;
        ListNode* slow = head;

        while (fast)
        {
            while (fast && slow->val == fast->val)
            {
                auto temp = fast;
                fast = fast->next;
                delete temp;
            }

            if (nullptr == fast)
            {
                slow->next = nullptr;
                break;
            }
            
            slow->next = fast;
            fast = fast->next;
            slow = slow->next;
        }

        return head;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 84. Largest Rectangle in Histogram
// 双指针（快慢指针） 动态规划 单调栈

class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        if (0 == heights.size())
        {
            return 0;
        }

        int max_area = 0;

        for (int slow = 0; slow <= heights.size() - 1; slow++)
        {
            int min_height = heights[slow];

            for (int fast = slow; fast <= heights.size() - 1; fast++)
            {
                min_height = std::min(heights[fast], min_height);
                int tmp_area = min_height * (fast - slow + 1);
                max_area = std::max(tmp_area, max_area);
            }
        }

        return max_area;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int largestRectangleArea(vector<int>& heights) {
        int max_area = 0;
        std::stack<int> s;
        heights.insert(heights.begin(), 0);
        heights.push_back(0);

        for (int index = 0; index <= (int)heights.size() - 1; index++)
        {
            while (false == s.empty() && heights[index] < heights[s.top()])
            {
                int h = heights[s.top()];
                s.pop();
                max_area = std::max(max_area, (index - s.top() - 1) * h);  
            }

            s.push(index);
        }

        return max_area;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 85. Maximal Rectangle
// 双指针（快慢指针） 滚动数组

class Solution {
public:
    int maximalRectangle(vector<vector<char>>& matrix) {
        if (0 == matrix.size())
        {
            return 0;
        }

        std::vector<int> vHeight(matrix[0].size(), 0);
        int max_area = 0;

        for (int row = 0; row <= matrix.size() - 1; row++)
        {
            // 一行一行往下扫
            for (int col = 0; col <= matrix[0].size() - 1; col++)
            {
                if ('1' == matrix[row][col])
                {
                    vHeight[col]++; // 高度累加
                }
                else if ('0' == matrix[row][col])
                {
                    vHeight[col] = 0; // 断了，归0
                }
            }

            int tmp_area = LargestRectangleArea(vHeight);
            max_area = std::max(tmp_area, max_area);
        }

        return max_area;
    }

private:
    int LargestRectangleArea(vector<int>& heights)
    {
        if (0 == heights.size())
        {
            return 0;
        }

        int max_area = 0;

        for (int slow = 0; slow <= heights.size() - 1; slow++)
        {
            int min_height = heights[slow];

            for (int fast = slow; fast <= heights.size() - 1; fast++)
            {
                min_height = std::min(heights[fast], min_height);
                int tmp_area = min_height * (fast - slow + 1);
                max_area = std::max(tmp_area, max_area);
            }
        }

        return max_area;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 88. 合并两个有序数组
// 数组

class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        int len_of_nums1 = m - 1;
        int len_of_nums2 = n - 1;
        int sum_len = m + n - 1;
        // 从后往前处理，都加到num1上去
        while (len_of_nums1 >= 0 && len_of_nums2  >= 0)
        {
            if (nums1[len_of_nums1] <= nums2[len_of_nums2])
            {
                nums1[sum_len--] = nums2[len_of_nums2--];
            }
            else if (nums1[len_of_nums1] > nums2[len_of_nums2])
            {
                nums1[sum_len--] = nums1[len_of_nums1--];
            }
        }
        // 要是nums2有剩余的，处理一下
        while (len_of_nums2 >= 0)
        {
            nums1[sum_len--] = nums2[len_of_nums2--];
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 90. 子集 II
// 深度优先 递归 回溯

class Solution {
public:
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        std::sort(nums.begin(), nums.end());
        std::vector<std::vector<int>> vRes;
        std::vector<int> vBuf;
        dfs(nums, vRes, vBuf, 0);
        return vRes;
    }

private:
    void dfs(std::vector<int>& nums,
             std::vector<std::vector<int>>& vRes, std::vector<int>& vBuf,
             int index)
    {
        vRes.push_back(vBuf);

        for (int i = index; i <= nums.size() - 1; i++)
        {
            if (i != index && nums[i] == nums[i - 1])
            {
                continue;
            }

            vBuf.push_back(nums[i]);
            dfs(nums, vRes, vBuf, i + 1);
            vBuf.pop_back();
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="91"></div>

```c++

// 91. 解码方法
// 动态规划 数学（进位） 解码

class Solution {
public:
    int numDecodings(string s) {
        // dp[i] 表示前i个数的方案数
        // dp[i] = dp[i - 1] + dp[i - 2]
        // 由于只和前两位有关，因此设置滚动数组
        // 当前为i，则变为i % 3，前一位为（i+2）% 3,前两位为（i+1）% 3
        std::vector<int> dp({0, 0, 1});
        int units = 0;
        int tens = 0;

        for (int index = 0; index <= s.length() - 1; index++)
        {
            dp[index % 3] = 0; // 清空当前位置（因为只要用其余两个位置就行）
            units = s[index] - '0'; // 个位数

            if (units != 0)
            {
                // 取一位，加上前一位
                dp[index % 3] += dp[(index + 2) % 3];
            }

            tens = tens * 10 + units;

            if (10 <= tens && tens <= 26)
            {
                // 取两位，加上前两位
                dp[index % 3] += dp[(index + 1) % 3];
            }

            tens = units; // 把个位数更新为十位数
        }

        return dp[(s.length() + 2) % 3];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int numDecodings(string s) {
        std::vector<int> dp(s.size() + 1);
        dp[0] = 1;

        int unit = 0;
        int tens = 0;

        for (int index = 0; index <= s.size() - 1; index++)
        {
            unit = s[index] - '0';
            tens = tens * 10 + unit; 

            if (0 != unit)
            {
                dp[index + 1] += dp[index];
            }

            if (tens >= 10 && tens <= 26)
            {
                dp[index + 1] += dp[index - 1];
            }

            tens = unit;
        }
        return dp[s.size()];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int numDecodings(string s) {
        int res = 0;
        int pre1 = 1;
        int pre2 = 0;

        int units = 0; 
        int tens = 0;


        for (int index = 0; index <= s.size() - 1; index++)
        {
            res = 0;
            units = s[index] - '0';

            if (units != 0)
            {
                res += pre1;
            }

            tens = tens * 10 + units;

            if (10 <= tens && tens <= 26)
            {
                res += pre2;
            }

            tens = units;
            pre2 = pre1;
            pre1 = res;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 92. Reverse Linked List II
// 链表 双指针（快慢指针） 头插法

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* reverseBetween(ListNode* head, int m, int n) {
        ListNode* psDumm = new ListNode(0);
        psDumm->next = head;
        // fast指向被翻好的链表末尾，其后节点curr每次被头插法
        ListNode* fast = head; 
        ListNode* slow = psDumm; // slow是要被翻转的前面那个点，每次不动
        ListNode* curr = nullptr; // 每次要被翻上去的节点，在fast后面

        // fast指向第m个节点，其后节点开始往头插
        int count = m;
        while (fast && --count)
        {
            slow = fast;
            fast = fast->next;
        }

        // 翻转n - m次，假设第m个已经翻好，
        // 只要翻m后面的就行，因此n - m
        count = n - m;

        while (fast && count--)
        {
            // 头插法，循环对称
            curr = fast->next; // 要被反转的就是fast后面的节点
            // fast断开和curr的连接，接到curr后面的节点
            fast->next = curr->next; 
            curr->next = slow->next; // slow每k-1次才动，都接到slow后面
            slow->next = curr; // curr接到slow后面
        }

        return psDumm->next;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 93. 复原IP地址
// 深度优先 递归 回溯

class Solution {
public:
    vector<string> restoreIpAddresses(string s) {
        std::vector<std::string> vs_res;
        std::string s_buf;
        dfs(s, vs_res, s_buf, 0, 0);
        return vs_res;
    }

private:
    // index表示的是字符串遍历
    // level表示的是最后分成几段
    void dfs1(std::string s, std::vector<std::string>& vs_res, 
             std::string s_buf, int index, int level)
    {
        if (4 == level || index == s.size()) // 停止条件
        {
            if (4 == level && index == s.size()) // 有效条件
            {
                s_buf.pop_back(); // 删除结尾"."
                vs_res.push_back(s_buf);
            }

            return;
        }

        for (int offset = 1; offset <= 3 && index + offset <= s.size(); offset++)
        {
            auto s_ip = s.substr(index, offset);

            if (std::stoi(s_ip) < 256 && 
               (s_ip == "0" || '0' != s_ip.front())) // 要么就是0，不然开头不能为0
            {
                dfs1(s, vs_res, s_buf + s_ip + ".", index + offset, level + 1);
            }
        }
    }

    void dfs2(std::string s, std::vector<std::string>& vs_res, 
             std::string s_buf, int index, int level)
    {
        if (4 == level || index == s.size()) // 停止条件
        {
            if (4 == level && index == s.size()) // 有效条件
            {
                s_buf.pop_back(); // 删除结尾"."
                vs_res.push_back(s_buf);
            }

            return;
        }

        for (int offset = 1; offset <= 3 && index + offset <= s.size(); offset++)
        {
            auto s_ip = s.substr(index, offset);

            if (std::stoi(s_ip) < 256 && 
               (s_ip == "0" || '0' != s_ip.front()))
            {
                s_buf += s_ip;
                s_buf += ".";
                dfs2(s, vs_res, s_buf, index + offset, level + 1);
                s_buf.erase(index + level, s_ip.size());
                s_buf.pop_back();
            }
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 94. 二叉树的中序遍历
// 中序遍历 迭代 栈 树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        if (nullptr == root)
        {
            return {};
        }

        std::vector<int> res;
        std::stack<TreeNode*> s;

        while (false == s.empty() || root)
        {
            while (root)
            {
                s.push(root);
                root = root->left;
            }

            root = s.top();
            s.pop();
            res.push_back(root->val);
            root = root->right;
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        if (nullptr == root)
        {
            return {};
        }
        std::vector<int> res;
        TreeNode* cur = root;
        TreeNode* most_right = nullptr; // 左子树上最右的结点

        while (cur)
        {
            most_right = cur->left;

            if (most_right) // 如果当前cur有左子树
            {
                while (most_right->right && most_right->right != cur)
                {
                    // 找到左子树上最右的结点
                    most_right = most_right->right;
                }
                // 此时most_right就是cur的左子树上最右的结点
                if (cur == most_right->right)
                {
                    most_right->right = nullptr;
                } 
                else if (nullptr == most_right->right)
                {
                    most_right->right = cur;
                    cur = cur->left;
                    continue;
                }
            }

            res.push_back(cur->val);
            // cur没有左子树，cur向右移
            // cur左子树最右结点右指针指向cur，也向右移
            cur = cur->right;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 95. 不同的二叉搜索树 II
// 树 深度优先 递归 分治

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<TreeNode*> generateTrees(int n) {
        if (0 == n)
        {
            return {};
        }

        return dfs(1, n);
    }

private:
    // 对于连续整数序列[left, right]中的一点i，若要生成以i为根节点的BST，则有如下规律：
    // i左边的序列可以作为左子树结点，且左儿子可能有多个，
    // 所以有vector<TreeNode *> left_nodes = generate(left, i - 1);；
    // i右边的序列可以作为右子树结点，同上
    // 所以有vector<TreeNode *> right_nodes = generate(i + 1, right);；
    // 产生的以当前i为根结点的BST（子）树有left_nodes.size() * right_nodes.size()个，
    // 遍历每种情况，即可生成以i为根节点的BST序列；
    // 然后以for循环使得[left, right]中每个结点都能生成子树序列。
    std::vector<TreeNode*> dfs(int left, int right)
    {
        std::vector<TreeNode*> v_res;

        if (left > right)
        {
            v_res.push_back(nullptr);
        }

        for (int index = left; index <= right; index++)
        {
            std::vector<TreeNode*> v_left_nodes = dfs(left, index - 1);
            std::vector<TreeNode*> v_right_nodes = dfs(index + 1, right);

            for (auto left_node : v_left_nodes)
            {
                for (auto right_node : v_right_nodes)
                {
                    TreeNode* new_root = new TreeNode(index);
                    new_root->left = left_node;
                    new_root->right = right_node;
                    v_res.push_back(new_root);
                }
            }
        }

        return v_res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 96. 不同的二叉搜索树
// 数学 树

class Solution {
public:
    int numTrees(int n) {
        // Catalan number：f(n) =  f(0)f(n-1) + f(1)f(n-2) + 
        //                        ... + f(n-2)f(1) + f(n-1)f(0)
        std::vector<int> v_res(n + 1, 0);

        v_res.at(0) = 1;

        for (int i = 1; i <= n; i++)
        {
            for (int j = 1; j <= i; j++)
            {
                v_res[i] += v_res[j - 1] * v_res[i - j];
            }
        }

        return v_res[n];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 98. Validate Binary Search Tree
// 二叉搜索树 深度优先 递归 中序遍历

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isValidBST(TreeNode* root) {
        pre_val = LONG_LONG_MIN;
        is_bst = true;
        dfs(root);
        return is_bst;
    }

private:
    long long pre_val;
    bool is_bst;

    void dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return;
        }

        dfs(root->left);
        if (pre_val >= root->val)
        {
            is_bst = false;
            return;
        }
        pre_val = root->val;
        dfs(root->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isValidBST(TreeNode* root) {
        return dfs(root,  LONG_MIN, LONG_MAX);
    }

private:
    bool dfs(TreeNode* root, long min, long max)
    {
        if (nullptr == root)
        {
            return true;
        }

        if (root->val < min || root->val > max)
        {
            return false;
        }

        return dfs(root->left, min, static_cast <long>(root->val) - 1) && 
               dfs(root->right, static_cast <long>(root->val) + 1, max);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 99. 恢复二叉搜索树
// 树 深度优先 中序遍历 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    void recoverTree(TreeNode* root) {
        if (nullptr == root)
        {
            return;
        }

        TreeNode* pPrev = nullptr;
        TreeNode* pErr1 = nullptr;
        TreeNode* pErr2 = nullptr;

        dfs(root, pPrev, pErr1, pErr2);

        int temp = pErr1->val;
        pErr1->val = pErr2->val;
        pErr2->val = temp;
    }

private:
    void dfs(TreeNode*& root, TreeNode*& pPrev, TreeNode*& pErr1, TreeNode*& pErr2)
    {
        if (nullptr == root)
        {
            return;
        }

        dfs(root->left, pPrev, pErr1, pErr2);

        if (pPrev && root->val < pPrev->val)
        {
            pErr1 = (nullptr == pErr1) ? pPrev : pErr1;
            pErr2 = root;
        }

        pPrev = root;

        dfs(root->right, pPrev, pErr1, pErr2);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 100. Same Tree
// 树 深度优先 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if (nullptr == p && nullptr == q)
        {
            return true;
        }

        if (nullptr == p || nullptr == q || p->val != q->val)
        {
            return false;
        }

        return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 101. 对称二叉树
// 树 深度优先 递归 回溯

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        return dfs(root, root);
    }

private:
    bool dfs(TreeNode* pst_left, TreeNode* pst_right)
    {
        if (nullptr == pst_left && nullptr == pst_right)
        {
            return true;
        }

        if (nullptr == pst_left || nullptr == pst_right)
        {
            return false;
        }

        return (pst_left->val == pst_right->val) && 
               dfs(pst_left->left, pst_right->right) && 
               dfs(pst_left->right, pst_right->left);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 102. 二叉树的层序遍历
// 广度优先 队 深度优先

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        if (nullptr == root)
        {
            return {};
        }

        std::vector<std::vector<int>> vv_res;
        std::queue<TreeNode*> q;

        q.push(root);

        while (false == q.empty())
        {
            int len = q.size();
            vv_res.push_back({});

            while (len--)
            {
                vv_res.back().push_back(q.front()->val);

                if (q.front()->left)
                {
                    q.push(q.front()->left);
                }

                if (q.front()->right)
                {
                    q.push(q.front()->right);
                }

                q.pop();
            }
        }

        return vv_res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        std::vector<std::vector<int>> res;
        dfs(res, root, 0);
        return res;
    }

private:
    void dfs(std::vector<std::vector<int>>& res, TreeNode* root, int depth)
    {
        if (nullptr == root)
        {
            return;
        }

        if (depth == res.size())
        {
            res.push_back({});
        }
        res[depth].push_back(root->val);
        dfs(res, root->left, depth + 1);
        dfs(res, root->right, depth + 1);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 103. 二叉树的锯齿形层次遍历
// 广度优先 队 树 深度优先

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        if (nullptr == root)
        {
            return {};
        }

        std::vector<std::vector<int>> res;
        std::deque<TreeNode*> q;
        bool zigzag = true;

        q.push_back(root);

        while (false == q.empty())
        {
            int len = q.size();
            res.push_back({});

            while (len--)
            {
                if (true == zigzag)
                {
                    auto cur = q.front();
                    res.back().push_back(cur->val);
                    q.pop_front();

                    if (cur->left)
                    {
                        q.push_back(cur->left);
                    }

                    if (cur->right)
                    {
                        q.push_back(cur->right);
                    }
                }
                else if (false == zigzag)
                {
                    auto cur = q.back();
                    res.back().push_back(cur->val);
                    q.pop_back();

                    if (cur->right)
                    {
                        q.push_front(cur->right);
                    }

                    if (cur->left)
                    {
                        q.push_front(cur->left);
                    }
                }   
            }
            zigzag = !zigzag;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        if (nullptr == root)
        {
            return {};
        }

        std::vector<std::vector<int>> res;
        dfs(res, root, 0);
        for (int index = 0; index <= res.size() - 1; index++)
        {
            if (index % 2)
            {
                std::reverse(res[index].begin(), res[index].end());
            }
        }
        return res;
    }

private:
    void dfs(std::vector<std::vector<int>>& res, TreeNode* root, int depth)
    {
        if (nullptr == root)
        {
            return;
        }

        if (depth == res.size())
        {
            res.push_back({});
        }

        res[depth].push_back(root->val);
        dfs(res, root->left, depth + 1);
        dfs(res, root->right, depth + 1);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 104. 二叉树的最大深度
// 树 深度优先 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (nullptr == root)
        {
            return 0;
        } 
        // 树的深度
        return std::max(maxDepth(root->left), maxDepth(root->right)) + 1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (nullptr == root)
        {
            return 0;
        }
        // 求深度模板
        int left_depth = maxDepth(root->left);
        int right_depth = maxDepth(root->right);

        return std::max(left_depth, right_depth) + 1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (nullptr == root)
        {
            return 0;
        }

        if (nullptr == root->left && nullptr == root->right)
        {
            // 全部砍掉
            return 1;
        }
        else if (nullptr == root->left)
        {
            // 砍掉左边
            return maxDepth(root->right) + 1;
        }
        else if (nullptr == root->right)
        {
            // 砍掉右边
            return maxDepth(root->left) + 1;
        }
        else // nullptr != root->left && nullptr != root->right
        {
            // 全部留下
            return std::max(maxDepth(root->left), maxDepth(root->right)) + 1;
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 105. 从前序与中序遍历序列构造二叉树
// 树 深度优先 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        return dfs(preorder, inorder, 0, 0, inorder.size() - 1);
    }

private:
    // 用前序中的值去遍历，去找到根
    // 然后在中序分成左右，来递归
    TreeNode* dfs(std::vector<int>& preorder, std::vector<int>& inorder, 
                  int preorder_index, int inorder_left, int inorder_right)
    {
        if (preorder_index > preorder.size() - 1 || 
            inorder_left > inorder_right)
        {
            return nullptr;
        }
        // 前序确定根
        TreeNode* new_root = new TreeNode(preorder[preorder_index]);
        int root_index = inorder_left;
        // 中序分左右
        for (; root_index <= inorder_right; root_index++)
        {
            if (new_root->val == inorder[root_index])
            {
                break;
            }
        }

        new_root->left = dfs(preorder, inorder, 
                             preorder_index + 1, 
                             inorder_left, root_index - 1);
        new_root->right = dfs(preorder, inorder, 
                              preorder_index + (root_index - inorder_left + 1), 
                              root_index + 1, inorder_right);

        return new_root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 106. 从中序与后序遍历序列构造二叉树
// 树 深度优先 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
        return dfs(inorder, postorder, 
                   postorder.size() - 1, 0, inorder.size() - 1);
    }

private:
    TreeNode* dfs(std::vector<int>& inorder, std::vector<int>& postorder, 
                  int postorder_index, int inorder_left, int inorder_right)
    {
        if (0 > postorder_index || inorder_left > inorder_right)
        {
            return nullptr;
        }

        TreeNode* new_root = new TreeNode(postorder.at(postorder_index));
        int root_index = inorder_right;

        for (; root_index >= inorder_left; root_index--)
        {
            if (new_root->val == inorder.at(root_index))
            {
                break;
            }
        }

        new_root->left = dfs(inorder, postorder, 
                             postorder_index - (inorder_right - root_index + 1), 
                             inorder_left, root_index - 1);
        new_root->right = dfs(inorder, postorder, 
                              postorder_index - 1, 
                              root_index + 1, inorder_right);

        return new_root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 107. 二叉树的层次遍历 II
// 广度优先 队

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> levelOrderBottom(TreeNode* root) {
        if (nullptr == root)
        {
            return {};
        }

        std::vector<std::vector<int>> vv_res;
        std::queue<TreeNode*> q;

        q.push(root);

        while (false == q.empty())
        {
            int len = q.size();
            vv_res.push_back({});

            while (len--)
            {
                vv_res.back().push_back(q.front()->val);

                if (q.front()->left)
                {
                    q.push(q.front()->left);
                }

                if (q.front()->right)
                {
                    q.push(q.front()->right);
                }

                q.pop();
            }
        }

        std::reverse(vv_res.begin(), vv_res.end());
        return vv_res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 108. 将有序数组转换为二叉搜索树
// 树 深度优先 递归 前序遍历

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        return build(nums, 0, nums.size() - 1);
    }

private:
    TreeNode* build(const vector<int>& nums, int left, int right)
    {
        if (left > right)
        {
            return nullptr;
        }

        int mid = left + (right - left) / 2;

        TreeNode* root = new TreeNode(nums[mid]);

        root->left = build(nums, left, mid - 1);
        root->right = build(nums, mid + 1, right);

        return root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 109. 有序链表转换二叉搜索树
// 树 深度优先 递归 链表 双指针（快慢指针）

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {} 
 * };
 */
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* sortedListToBST(ListNode* head) {
        if (nullptr == head)
        {
            return nullptr;
        }

        return dfs(head, nullptr);
    }

private:
    TreeNode* dfs(ListNode* head, ListNode* tail) // 左闭右开
    {
        if (head == tail)
        {
            return nullptr;
        }

        ListNode* fast = head;
        ListNode* slow = head;

        while (fast != tail && fast->next != tail)
        {
            fast = fast->next->next;
            slow = slow->next; // slow找到中点
        }

        TreeNode* new_root = new TreeNode(slow->val);
        new_root->left = dfs(head, slow); // 左闭右开，所以slow不会再算一次
        new_root->right = dfs(slow->next, tail);

        return new_root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 110. 平衡二叉树
// 树 深度优先 递归 后序遍历

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isBalanced(TreeNode* root) {
        if (nullptr == root)
        {
            return true;
        }

        bool balanced = true;

        cout<< dfs(root, balanced)  << endl; // 求高度

        return balanced;
    }

private:
    int dfs(TreeNode* root, bool& balanced)
    {
        if (nullptr == root)
        {
            return 0;
        }

        int left_hight = dfs(root->left, balanced);
        int right_hight = dfs(root->right, balanced);

        if (std::abs(left_hight - right_hight) > 1)
        {
            balanced = false; // 一旦不符合就改
            return 0;
        }

        return std::max(left_hight, right_hight) + 1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isBalanced(TreeNode* root) {
        return dfs(root).is_bst;
    }

    class CRes
    {
    public:
        int height;
        bool is_bst;

        CRes(int height, bool is_bst)
        : height(height), is_bst(is_bst)
        {}
    };

    CRes dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return CRes(0, true);
        }

        CRes left_res = dfs(root->left);
        CRes right_res = dfs(root->right);

        int cur_height = std::max(left_res.height, right_res.height) + 1;
        bool cur_is_bst = left_res.is_bst && right_res.is_bst && 
                          2 > std::abs(left_res.height - right_res.height);
        
        return CRes(cur_height, cur_is_bst);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 111. 二叉树的最小深度
// 深度优先 递归 树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int minDepth(TreeNode* root) {
        if (nullptr == root)
        {
            return 0;
        }

        if (nullptr == root->left && nullptr == root->right)
        {
            // 全部砍掉
            return 1;
        }
        else if (nullptr == root->left)
        {
            // 处理[1,2]这样的树，最小深度由题意为2
            // 砍掉左边
            return minDepth(root->right) + 1;
        }
        else if (nullptr == root->right)
        {
            // 砍掉右边
            return minDepth(root->left) + 1;
        }
        else // nullptr != root->left && nullptr != root->right
        {
            // 全部留下
            return std::min(minDepth(root->left), minDepth(root->right)) + 1;
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 112. 路径总和
// 树 深度优先 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool hasPathSum(TreeNode* root, int sum) {
        if (nullptr == root) // 父节点只有一个左右子树会出现的情况
        {
            return false; // 默认左右两边都是空才是叶子
        }

        if (nullptr == root->left && nullptr == root->right)
        {
            return (root->val == sum);
        }

        return hasPathSum(root->left, sum - root->val) || 
               hasPathSum(root->right, sum - root->val);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 113. 路径总和 II
// 深度优先 回溯 树 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> pathSum(TreeNode* root, int sum) {
        if (nullptr == root)
        {
            return {};
        }

        std::vector<std::vector<int>> vv_res;
        std::vector<int> v_buf;
        dfs(root, sum, vv_res, v_buf);
        return vv_res;
    }

private:
    void dfs(TreeNode* root, int sum, 
             std::vector<std::vector<int>>& vv_res, std::vector<int>& v_buf)
    {
        if (nullptr == root) 
        {
            return ;
        }

        if (nullptr == root->left && nullptr == root->right) // 叶
        {
            if (root->val == sum)
            {
                v_buf.push_back(root->val);
                vv_res.push_back(v_buf);
                v_buf.pop_back();
            }

            return ;
        }

        v_buf.push_back(root->val);

        dfs(root->left, sum - root->val, vv_res, v_buf);
        dfs(root->right, sum - root->val, vv_res, v_buf);

        v_buf.pop_back();
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> pathSum(TreeNode* root, int sum) {
        if (nullptr == root)
        {
            return {};
        }

        std::vector<std::vector<int>> res;
        std::vector<int> buf;

        dfs(root, sum, res, buf);
        return res;
    }

private:
    void dfs(TreeNode* root, int sum, 
             std::vector<std::vector<int>>& res, std::vector<int> buf)
    {
        if (nullptr == root)
        {
            return ;
        }

        if (nullptr == root->left && nullptr == root->right)
        {
            if (sum == root->val)
            {
                buf.push_back(root->val);
                res.push_back(buf);
            }
            return ;
        }
        
        buf.push_back(root->val);
        dfs(root->left, sum - root->val, res, buf);
        dfs(root->right, sum - root->val, res, buf);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 114. 二叉树展开为链表
// 链表 树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) 
 *              : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    void flatten(TreeNode* root) {
        while (root)
        {
            if (root->left) // 找左子树
            {
                TreeNode* left_right_node = root->left; // 找左子树的最右节点

                while (left_right_node->right)
                {
                    left_right_node = left_right_node->right;
                }

                left_right_node->right = root->right; 
                // 把当前根的右子树接到左子树最右子树的右子树上
                root->right = root->left; // 把左子树接到右子树上
                root->left = nullptr;
            }

            root = root->right; // 没有左子树往右走
        }     
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 116. 填充每个节点的下一个右侧节点指针
// 深度优先 树 递归 

/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;
    Node* next;

    Node() : val(0), left(NULL), right(NULL), next(NULL) {}

    Node(int _val) : val(_val), left(NULL), right(NULL), next(NULL) {}

    Node(int _val, Node* _left, Node* _right, Node* _next)
        : val(_val), left(_left), right(_right), next(_next) {}
};
*/

class Solution {
public:
    Node* connect(Node* root) {
        if (nullptr == root || 
           (nullptr == root->left && nullptr == root->right))
        {
            return root;
        }
        // 左孩子接到右孩子（连接孩子节点）
        root->left->next = root->right;

        if (root->next) // 说明不是右边的节点（连接堂兄弟节点）
        {
            root->right->next = root->next->left;
        }

        connect(root->left);
        connect(root->right);

        return root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="120"></div>

```c++

// 120. 三角形最小路径和
// 动态规划 树状DP

class Solution {
public:
    int minimumTotal(vector<vector<int>>& triangle) {
        if (0 == triangle.size())
        {
            return 0;
        }

        // 从倒数第二行开始,从下往上
        for (int row = triangle.size() - 2; row >= 0; row--)
        {
            for (int col = 0; col <= triangle[row].size() - 1; col++)
            {
                // 直接覆盖数组
                triangle[row][col] += std::min(triangle[row + 1][col], 
                                               triangle[row + 1][col + 1]);
            }
        }

        return triangle[0][0];
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="121"></div>

```c++

// 121. 买卖股票的最佳时机
// 动态规划 差分数组 双指针（跟随指针）

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int dp = 0;
        int max_profit = 0;

        for (int index = 1; index <= (int)prices.size() - 1; index++)
        {
            dp = std::max(0, dp + prices[index] - prices[index - 1]);
            max_profit = std::max(max_profit, dp);
        }
        return max_profit;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if (0 == prices.size())
        {
            return 0;
        }
        // 维护两个，最小值和最大收益
        int min_price = INT_MAX;
        int max_profit = 0;

        for (int day = 0; day <= prices.size() - 1; day++)
        {
            min_price = std::min(min_price, prices[day]);
            max_profit = std::max(max_profit, prices[day] - min_price);
        }

        return max_profit;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if (0 == prices.size())
        {
            return 0;
        }

        int max_profit = 0;
        int slow_dp = 0;
        int fast_dp = 0;

        for (int day = 1; day <= prices.size() - 1; day++)
        {
            int delta = prices[day] - prices[day - 1];
            // 如果变化量是负数就不更新
            // 即加上delta后值反而变小了
            fast_dp = std::max(delta, slow_dp + delta);
            slow_dp = fast_dp;

            max_profit = std::max(max_profit, fast_dp);
        }

        return max_profit;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="122"></div>

```c++

// 122. 买卖股票的最佳时机 II
// 动态规划

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int day = 1;
        int high = prices[0];
        int low = prices[0];
        int max_profit = 0;

        while (day <= prices.size() - 1)
        {
            while (day <= prices.size() - 1 && prices[day - 1] >= prices[day])
            {
                day++;
            }

            low = prices[day - 1];

            while (day <= prices.size() - 1 && prices[day - 1] <= prices[day])
            {
                day++;
            }

            high = prices[day - 1];

            max_profit += high - low;
        }

        return max_profit;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="123"></div>

```c++

// 123. 买卖股票的最佳时机 III
// 动态规划 滚动数组

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if (0 == prices.size())
        {
            return 0;
        }
        // 由于i依赖于i-1，所以删掉第一维
        std::vector<std::vector<int>> dp(3, std::vector<int>(2, INT_MIN));
        dp[0][0] = 0; // 没有
        dp[0][1] = -prices[0]; // 持有
        int res = 0;

        for (int day = 0; day <= prices.size() - 1; day++)
        {
            for (int cnt = 1; cnt <= 2; cnt++)
            {
                dp[cnt][0] = std::max(dp[cnt][0], dp[cnt][1] + prices[day]);
                dp[cnt][1] = std::max(dp[cnt][1], dp[cnt - 1][0] - prices[day]);

                res = std::max(res, dp[cnt][0]);
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 124. 二叉树中的最大路径和
// 深度优先 递归 树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int max = INT_MIN; // 负数
    int maxPathSum(TreeNode* root) {
        dfs(root);
        return max;
    }

private:
    int dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return 0;
        }
        // 求高度模板 （不加入负数）
        int left_depth = std::max(0, dfs(root->left));
        int right_depth = std::max(0, dfs(root->right));  

        max = std::max(max, (left_depth + right_depth + root->val));
        return std::max(left_depth, right_depth) + root->val;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 127. 单词接龙
// 广度优先 队 图 最短路径

class Solution {
public:
    int ladderLength(string beginWord, string endWord, 
                     vector<string>& wordList) {
        int len = wordList.size();
        // 本质就是无向连通图找最短路径
        // beginWord按题意可能不在wordlist中
        // 先插入，方便找最短路径
        wordList.push_back(beginWord);

        std::queue<int> q;
        std::vector<int> distance(len + 1, 0); // 加了begin
        distance[len] = 1; // beginWord
        q.push(len); // beginWord的下标入队
        // 广度优先每次会遍历一颗树出来
        while (false == q.empty())
        {
            int parent = q.front();
            q.pop();

            for (int child = 0; child < len; child++)
            {
                // 已经被访问过了的 或者 两个节点间没有边
                if (0 != distance[child] || 
                    false == canTrans(wordList[child], wordList[parent]))
                {
                    continue;
                }
                // 出口
                if (endWord == wordList[child])
                {
                    return distance[parent] + 1;
                }

                distance[child] = distance[parent] + 1;
                q.push(child);
            }
        }
        return 0;
    }

private:
    // 传引用比传整个字符串快
    bool canTrans(const string& a, const string& b)
    {
        int count = 0;

        for (int index = 0; index < a.size(); index++)
        {
            // 累计不同的字符
            count += (a[index] != b[index]); 
        }

        return 1 == count;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 128. 最长连续序列
// 哈希表 并查集

class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        // 要求算法的时间复杂度为 O(n)
        // 说明暗示只能用哈希表了
        std::unordered_set<int> s(nums.begin(), nums.end());
        int res = 0;

        for (auto num : nums)
        {
            // 每次从最小的值开始检查
            // 所以首先看看num - 1在不在集合中
            // 如果在就不考虑当前值
            if (0 == s.count(num - 1)) // 当前为最小值
            {
                int len = 1;
                // 找连续的值
                while (1 == s.count(++num))
                {
                    len++;
                }
                res = std::max(res, len);
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        // 并查集
        std::unordered_map<int, int> m; // num=>length
        int res = 0;

        for (int num : nums)
        {
            // 如果当前节点已经在map中，就不处理
            if (1 == m.count(num))
            {
                continue;
            }
            // 先找当前节点左集合
            auto it_left = m.find(num - 1);
            int len_left = it_left == m.end() ? 0 : it_left->second;
            // 再找当前节点右集合
            auto it_right = m.find(num + 1);
            int len_right = it_right == m.end() ? 0 : it_right->second;
            // 并查集只关心边界值
            if (0 < len_left && 0 < len_right) 
            {
                // 说明当前节点连接左右两边节点
                // 更新边界长度值
                m[num - len_left] = m[num + len_right] = len_left + len_right + 1;
                // 将当前元素插入哈希表
                m[num] = len_left + len_right + 1;
            }
            else if (0 < len_left && 0 == len_right)
            {
                m[num] = m[num - len_left] = len_left + 1;  
            }
            else if (0 == len_left && 0 < len_right)
            {
                m[num] = m[num + len_right] = len_right + 1;
            }
            else if (0 == len_left && 0 == len_right)
            {
                m[num] = 1;
            }
        }

        for (auto n : m)
        {
            res = std::max(res, n.second);
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 130. 被围绕的区域
// 深度优先 递归

class Solution {
public:
    void solve(vector<vector<char>>& board) {
        if (0 == board.size())
        {
            return;
        }
        // 从边缘找O
        for (int row = 0; row <= board.size() - 1; row++)
        {
            dfs(board, row, 0);
            dfs(board, row, board[0].size() - 1);
        }

        for (int col = 0; col <= board[0].size() - 1; col++)
        {
            dfs(board, 0, col);
            dfs(board, board.size() - 1, col);
        }
        // 把'#'换成'O'，把'O'换成'X'
        for (int row = 0; row <= board.size() - 1; row++)
        {
            for (int col = 0; col <= board[0].size() - 1; col++)
            {
                if ('O' == board[row][col])
                {
                    board[row][col] = 'X';
                }

                if ('#' == board[row][col])
                {
                    board[row][col] = 'O';
                }
            }
        }
    }

private:
    void dfs(std::vector<std::vector<char>>& board, int row, int col)
    {
        if (row < 0 || row >= board.size() ||
            col < 0 || col >= board[0].size() ||
            'O' != board[row][col]) // 可能是'#'或'X'
        {
            return;
        }

        board[row][col] = '#';

        dfs(board, row - 1, col);
        dfs(board, row + 1, col);
        dfs(board, row, col - 1);
        dfs(board, row, col + 1);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 133. 克隆图
// 广度优先 队 深度优先 迭代 图 邻接表

/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> neighbors;
    
    Node() {
        val = 0;
        neighbors = vector<Node*>();
    }
    
    Node(int _val) {
        val = _val;
        neighbors = vector<Node*>();
    }
    
    Node(int _val, vector<Node*> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
};
*/

class Solution {
public:
    Node* cloneGraph(Node* node) {
        if (nullptr == node)
        {
            return nullptr;
        }
        // 广度优先
        std::unordered_map<Node*, Node*> m; // old node=>new node
        // 先创建节点再连边
        Node* new_node = new Node(node->val); // 创建新节点
        m[node] = new_node;

        std::queue<Node*> q;
        q.push(node); // 队里进的是旧节点

        while (false == q.empty())
        {
            Node* old_cur = q.front();
            q.pop();
            Node* new_cur = m[old_cur];

            for (auto old_child : old_cur->neighbors)
            {
                if (m.find(old_child) != m.end())
                {
                    // 若已经复制过节点了，只要添加边就行了
                    new_cur->neighbors.push_back(m[old_child]);
                }
                else if (m.find(old_child) == m.end())
                {
                    Node* new_child = new Node(old_child->val);
                    m[old_child] = new_child;
                    new_cur->neighbors.push_back(new_child);
                    q.push(old_child);
                }
            } 
        }
        return new_node;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> neighbors;
    
    Node() {
        val = 0;
        neighbors = vector<Node*>();
    }
    
    Node(int _val) {
        val = _val;
        neighbors = vector<Node*>();
    }
    
    Node(int _val, vector<Node*> _neighbors) {
        val = _val;
        neighbors = _neighbors;
    }
};
*/

class Solution {
public:
    std::unordered_map<Node*, Node*> m; // old node=>new node
    // 深度优先
    Node* cloneGraph(Node* node) {
        if (nullptr == node)
        {
            return nullptr;
        }

        if (m.find(node) != m.end())
        {
            // 如果当前节点已经存在，就不要再创建了，添加这条边就行
            return m[node]; 
        }

        Node* new_node = new Node(node->val);
        m[node] = new_node;

        for (auto old_child : node->neighbors)
        {
            new_node->neighbors.push_back(cloneGraph(old_child));
        }
        return new_node;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 135. 分发糖果
// 贪心法 数组
老师想给孩子们分发糖果，有 N 个孩子站成了一条直线，老师会根据每个孩子的表现，预先给他们评分。
你需要按照以下要求，帮助老师给这些孩子分发糖果：
每个孩子至少分配到 1 个糖果。
相邻的孩子中，评分高的孩子必须获得更多的糖果。
那么这样下来，老师至少需要准备多少颗糖果呢？

class Solution {
public:
    int candy(vector<int>& ratings) {
        std::vector<int> v(ratings.size(), 1);
        for (int index = 1; index <= ratings.size() - 1; index++)
        {
            if (ratings[index - 1] < ratings[index])
            {
                v[index] = v[index - 1] + 1;
            }
        }

        for (int index = ratings.size() - 2; index >= 0; index--)
        {
            if (ratings[index] > ratings[index + 1])
            {
                v[index] = std::max(v[index], v[index + 1] + 1);
            }
        }

        return std::accumulate(v.begin(), v.end(), 0);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 136. 只出现一次的数字
// 位运算 数组

class Solution {
public:
    int singleNumber(vector<int>& nums) {
        // 任何数和本身异或则为0
        // 任何数和 0 异或是本身
        int res = 0;
        for (auto num : nums)
        {
            res ^= num;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 137. 只出现一次的数字 II
// 数组 位运算

class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int res = 0;
        for (int offset = 0; offset < 32; offset++)
        {
            int count = 0;
            int bit = 1 << offset;

            for (int index = 0; index <= nums.size() - 1; index++)
            {
                if (nums[index] & bit) // 查询
                {
                    count++;
                }
            }

            if (count % 3 != 0)
            {
                res |= bit; // 添加那个元素
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="139"></div>

```c++

// 139. 单词拆分
// 动态规划

class Solution {
public:
    bool wordBreak(string s, vector<string>& wordDict) {
        std::vector<bool> dp(s.size() + 1, false);
        dp[0] = true; // 空字符可以被匹配

        for (int index = 0; index <= s.size() - 1; index++)
        {
            if (false == dp[index])
            {
                continue;
            }

            for (auto& word : wordDict)
            {
                if (word == s.substr(index, word.size()))
                {
                    dp[index + word.size()] = true;
                } 
            }
        }
        return dp[s.size()];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 141. 环形链表
// 双指针（快慢指针）链表

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool hasCycle(ListNode *head) {
        ListNode* fast = head;
        ListNode* slow = head;

        while (fast && fast->next)
        {
            fast = fast->next->next;
            slow = slow->next;

            if (fast == slow)
            {
                return true;
            }      
        }
        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 144. 二叉树的前序遍历
// 前序遍历 迭代 栈 树 morris遍历

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        if (nullptr == root)
        {
            return {};
        }
        
        std::vector<int> res;
        std::stack<TreeNode*> s;
        s.push(root);

        while (false == s.empty())
        {
            root = s.top();
            res.push_back(root->val);
            s.pop();

            if (root->right)
            {
                s.push(root->right);
            }

            if (root->left)
            {
                s.push(root->left);
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        if (nullptr == root)
        {
            return {};
        }
        std::vector<int> res;
        TreeNode* cur = root;
        TreeNode* most_right = nullptr; // 左子树上最右的结点

        while (cur)
        {
            most_right = cur->left;

            if (most_right) // 如果当前cur有左子树
            {
                while (most_right->right && most_right->right != cur)
                {
                    // 找到左子树上最右的结点
                    most_right = most_right->right;
                }
                // 此时most_right就是cur的左子树上最右的结点
                if (cur == most_right->right)
                {
                    most_right->right = nullptr;
                } 
                else if (nullptr == most_right->right)
                {
                    most_right->right = cur;
                    res.push_back(cur->val);
                    cur = cur->left;
                    continue;
                }
            }
            else if (nullptr == most_right)
            {
                res.push_back(cur->val);
            }
            // cur没有左子树，cur向右移
            // cur左子树最右结点右指针指向cur，也向右移
            cur = cur->right;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 145. 二叉树的后序遍历
// 后序遍历 迭代 栈 树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        if (NULL == root)
        {
            return {};
        }

        std::vector<int> res;
        std::stack<TreeNode*> s;

        s.push(root);

        while (false == s.empty())
        {
            root = s.top();
            s.pop();
            // 往前插入
            res.insert(res.begin(), root->val);

            if (root->left)
            {
                s.push(root->left);
            }

            if (root->right)
            {
                s.push(root->right);
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 146. LRU缓存机制
// 类 哈希表 链表

class LRUCache {
public:
    // 构造函数
    LRUCache(int capacity)  
    : capacity(capacity) {}

    int get(int key) {
        auto it = m.find(key); // it指向(key, (key, value))

        if (it == m.end())
        {
            return -1;
        }
        // 如果原来哈希表中有，要更新其优先级
        // splice表示把cache中的it->second拼剪到cache前端
        // it指向(key, (key, value))所以it->second表示(key, value)
        cache.splice(cache.begin(), cache, it->second); // O(1)
        return it->second->second; // 返回值（value）
    }

    void put(int key, int value) {
        auto it = m.find(key);
        // key已存在
        if (it != m.end())
        {
            // 若已有该key,则更新值(覆盖)
            it->second->second = value;
            // 更新优先级
            cache.splice(cache.begin(), cache, it->second); // O(1)
            return;
        }
        // key不存在,但是容量不够了
        if (capacity == cache.size())
        {
            // 从哈希表中去除链表结尾节点的key
            auto& node = cache.back();
            m.erase(node.first);
            // 从链表中删除
            cache.pop_back();
        }
        // 添加
        // emplace_front会创建一个节点并插入开头
        cache.emplace_front(key, value);
        m[key] = cache.begin(); // 将节点迭代器存到哈希表
    }
private:
    int capacity;
    std::list<std::pair<int, int>> cache;
    // key->(key, value)
    std::unordered_map<int, std::list<std::pair<int, int>>::iterator> m; // O(1)
};

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache* obj = new LRUCache(capacity);
 * int param_1 = obj->get(key);
 * obj->put(key,value);
 */

```
<div STYLE="page-break-after: always;"></div>

<div id="152"></div>

```c++

// 152. 乘积最大子数组
// 动态规划 数学

class Solution {
public:
    int maxProduct(vector<int>& nums) {
        if (0 == nums.size())
        {
            return 0;
        }

        int max = nums[0]; // 两正数乘积
        int min = nums[0]; // 两负数乘积
        int res = nums[0];

        for (int index = 1; index <= nums.size() - 1; index++)
        {
            int max_temp = max;
            int min_temp = min;
            max = biggest(max_temp * nums[index], 
                          min_temp * nums[index], 
                          nums[index]);
            min = smallest(max_temp * nums[index], 
                           min_temp * nums[index], 
                           nums[index]);
            res = std::max(max, res);
        }
        return res;
    }

private:
    inline int biggest(int a, int b, int c)
    {
        int tmp = std::max(a, b);
        return std::max(tmp, c);
    }

    inline int smallest(int a, int b, int c)
    {
        int tmp = std::min(a, b);
        return std::min(tmp, c);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 153. 寻找旋转排序数组中的最小值
// 二分法

class Solution {
public:
    int findMin(vector<int>& nums) {
        // 最小值一定出现在不单调的那一边
        // 双闭[left, right]
        // 最后情况为[mid = left,right]或者[left, mid = right]
        int left = 0;
        int right = nums.size() - 1;

        while (left + 1 < right)
        {
            // 向下（左）取整, 所以和右边比
            int mid = left + (right - left) / 2;
            // 无重复
            if (nums[mid] < nums[right])
            {
                right = mid;
            }
            else if (nums[mid] > nums[right])
            {
                left = mid;
            }
        }

        if (nums[left] < nums[right])
        {   
            return nums[left];
        }
        else // if (nums[left] > nums[right])
        {
            return nums[right];
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int findMin(vector<int>& nums) {
        int left = 0;
        int right = nums.size() - 1;
        int res = INT_MAX;

        while (left <= right)
        {
            int mid = left + (right - left) / 2;
            res = std::min(res, nums[mid]);
            
            if (nums[left] <= nums[mid] && nums[mid] <= nums[right])
            {
                // 可行区间单调
                res = std::min(res, nums[left]); // 选左边的
                break;
            }
            else if (nums[left] > nums[mid]) // 哪边不单调往哪边移
            {
                // 左侧不单调，向左边转移
                right = mid - 1;
            }
            else if (nums[mid] > nums[right])
            {
                // 右侧不单调，向右侧转移
                left = mid + 1;
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 154. 寻找旋转排序数组中的最小值 II
// 二分法 数组

class Solution {
public:
    int findMin(vector<int>& nums) {
        for (int index = 1; index <= nums.size() - 1; index++)
        {
            // 肯定出现在接缝处
            if (nums[index - 1] > nums[index])
            {
                return nums[index];
            }
        }
        // 不然就是第一个
        return nums[0];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int findMin(vector<int>& nums) {
        int left = 0;
        int right = nums.size() - 1;

        while (left + 1 < right)
        {
            int mid = left + (right - left) / 2; // 向左取整，处理右边

            if (nums[mid] == nums[right])
            {
                right--;
            }
            else if (nums[mid] < nums[right])
            {
                right = mid;
            }
            else if (nums[mid] > nums[right])
            {
                left = mid;
            }
        }

        if (nums[left] <= nums[right])
        {
            return nums[left];
        }
        else
        {
            return nums[right];
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int findMin(vector<int>& nums) {
        int left = 0;
        int right = nums.size() - 1;
        int res;

        while (left <= right)
        {


            int mid = left + (right - left) / 2;
            res = std::min(res, nums[mid]);
            if (nums[left] < nums[right])
            {
                // 可行区间单调
                res = std::min(res, nums[left]);
                break;
            }
            else if (nums[left] < nums[mid]) // 哪边不单调往哪边移
            {
                // 右侧不单调，向右侧转移 
                left = mid + 1;
            }
            else if (nums[mid] < nums[right])
            {
                // 左侧不单调，向左边转移
                right = mid - 1;
            }
            else if (nums[left] == nums[mid] || nums[mid] == nums[right])
            {
                res = std::min(res, nums[right]);
                left++;
                right--;
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 155. 最小栈
// 类 栈

class MinStack {
private:
    std::vector<int> v;
    int min_val;
public:
    /** initialize your data structure here. */
    MinStack() 
    : min_val(INT_MAX) {}
    
    void push(int x) {
        v.push_back(x);
        min_val = std::min(min_val, x);
    }
    
    void pop() {
        int min_tmp = v.back();
        v.pop_back();
        // 如果被删的就是最小值
        if (min_val == min_tmp)
        {
            min_val = INT_MAX;

            for (int n : v)
            {
                min_val = std::min(min_val, n);
            }
        }
    }
    
    int top() {
        return v.back();
    }
    
    int getMin() {
        return min_val;
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->getMin();
 */

```
<div STYLE="page-break-after: always;"></div>

```c++

// 156. 上下翻转二叉树
// 深度优先 后序遍历 二叉树
// 给定一个二叉树，其中所有的右节点要么是具有兄弟节点（拥有相同父节点的左节点）的叶节点，要么为空，将此二叉树上下翻转并将它变成一棵树， 原来的右节点将转换成左叶节点。返回新的根。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* upsideDownBinaryTree(TreeNode* root) {
        if (nullptr == root || nullptr == root->left)
        {
            return root;
        }

        auto res = upsideDownBinaryTree(root->left);
        // 左孩子重新连接
        root->left->left = root->right;
        root->left->right = root;
        // 根节点重新连接
        root->left = nullptr;
        root->right = nullptr;
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 160. 相交链表
// 链表 哈希表

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        std::unordered_set<ListNode*> s;

        while (headA)
        {
            s.insert(headA);
            headA = headA->next;
        }

        while (headB)
        {
            if (s.end() != s.find(headB))
            {
                return headB;
            }
            headB = headB->next;
        }
        return nullptr;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 167. 两数之和 II - 输入有序数组
// 双指针（相向指针） 数组

class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int left = 0; 
        int right = numbers.size() - 1;

        while (left < right)
        {
            int sum = numbers[left] + numbers[right];

            if (sum == target)
            {
                return {left + 1, right + 1};
            }
            else if (sum > target)
            {
                right--;
            }
            else if (sum < target)
            {
                left++;
            }
        }
        return {};
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 169. 多数元素
// 哈希表 数组

class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int n = nums.size();

        std::map<int, int> m; // nums[index]->index

        for (auto num : nums)
        {
            m[num]++;

            if (n / 2 < m[num])
            {
                return num;
            }
        }
        return 0;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 173. 二叉搜索树迭代器
// 类 中序遍历 深度优先 二叉搜索树 队
// 实现一个二叉搜索树迭代器。你将使用二叉搜索树的根节点初始化迭代器。调用 next() 将返回二叉搜索树中的下一个最小的数。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class BSTIterator {
public:
    BSTIterator(TreeNode* root) {
        dfs(root);
    }
    
    /** @return the next smallest number */
    int next() {
        auto res = q.front();
        q.pop();
        return res;
    }
    
    /** @return whether we have a next smallest number */
    bool hasNext() {
        return false == q.empty();
    }
private:
    std::queue<int> q;
    size_t index;

    void dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return;
        }

        dfs(root->left);
        q.push(root->val);
        dfs(root->right);
    }
};

/**
 * Your BSTIterator object will be instantiated and called as such:
 * BSTIterator* obj = new BSTIterator(root);
 * int param_1 = obj->next();
 * bool param_2 = obj->hasNext();
 */

```
<div STYLE="page-break-after: always;"></div>

<div id="188"></div>

```c++

// 188. 买卖股票的最佳时机 IV
// 动态规划 滚动数组

class Solution {
public:
    int maxProfit(int k, vector<int>& prices) {
        if (1 >= prices.size())
        {
            return 0;
        }

        // dp[i][k][0] 表示第 i 天， 第 k 次交易，没有持有股票
        // dp[i][k][1] 表示第 i 天， 第 k 次交易，持有股票
        // i只依赖i-1,所以滚动数组，删掉第一位
        // dp[k][0], dp[k][1]

        if (k > prices.size() / 2) // 可以随意次数交易
        {
            int res = 0;
            for (int day = 1; day <= prices.size() - 1; day++) 
            {
                if (prices[day - 1] < prices[day]) 
                {
                    res += prices[day] - prices[day - 1];
                }
            }
            return res;
        }
        // k < prices.size() / 2的情况
        std::vector<std::vector<int>> dp(k + 1, vector<int>(2, INT_MIN));
        dp[0][0] = 0;
        dp[0][1] = -prices[0];

        for (int day = 0; day <= prices.size() - 1; day++)
        {
            for (int cnt = 1; cnt <= k; cnt++)
            { 
                dp[cnt][0] = std::max(dp[cnt][0], dp[cnt][1] + prices[day]);
                dp[cnt][1] = std::max(dp[cnt][1], dp[cnt - 1][0] - prices[day]);
            }
        }
        int res = 0;
        // 找最大的
        for (int cnt = 0; cnt <= k; cnt++)
        {
            res = std::max(res, dp[cnt][0]);
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 189. 旋转数组
// 数组 三次翻转

class Solution {
public:
    void rotate(vector<int>& nums, int k) {
        k = k % nums.size();

        reverse(nums, 0, nums.size() - 1);
        reverse(nums, 0, k - 1);
        reverse(nums, k, nums.size() - 1);
    }

private:
    void reverse(vector<int>& nums, int left, int right)
    {
        while (left < right)
        {
            auto temp = nums[left];
            nums[left] = nums[right];
            nums[right] = temp;
            left++;
            right--;
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 190. 颠倒二进制位
// 数学 位运算

class Solution {
public:
    uint32_t reverseBits(uint32_t n) {
        uint32_t res = 0;

        for (int index = 0; index < 32; index++)
        {
            // 当前位是1就添加到res
            //res不断左移，n不断右移
            res = (res << 1) | (n & 1);
            n >>= 1;
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 191. 位1的个数
// 数学 位运算

class Solution {
public:
    int hammingWeight(uint32_t n) {
        int res = 0;

        while (0 != n)
        {
            n = (n & (n - 1)); // 每次会把一个1变成0;
            res++;
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="198"></div>

```c++

// 198. 打家劫舍
// 动态规划 滚动数组 双指针（跟随指针）

class Solution {
public:
    int rob(vector<int>& nums) {
        std::vector<int> dp(nums.size() + 2, 0);

        for (int index = 0; index <= (int)nums.size() - 1; index++)
        {
            dp[index + 2] = std::max(dp[index + 1], dp[index] + nums[index]);
        }

        return dp[nums.size() + 1];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int rob(vector<int>& nums) {
        int prepre = 0;
        int pre = 0;
        int cur = 0;

        for (int index = 0; index <= (int)nums.size() - 1; index++)
        {
            cur = std::max(pre, prepre + nums[index]);

            prepre = pre;
            pre = cur;
        }
        return cur;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int rob(vector<int>& nums) {
        if (0 == nums.size())
        {
            return 0;
        }
        int cur = nums[0];
        int pre = 0;

        for (int index = 1; index <= nums.size() - 1; index++)
        {
            int cur_temp = cur;
            // 不偷则为前一天的值，偷则为当天值加前两天值
            cur = std::max(cur, pre + nums[index]); 
            pre = cur_temp;
        }
        return cur;   
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 199. 二叉树的右视图
// 树 队 广度优先

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> rightSideView(TreeNode* root) {
        if (nullptr == root)
        {
            return {};
        }

        std::vector<int> v_res;
        std::queue<TreeNode*> q;

        q.push(root);

        while (false == q.empty())
        {
            int len = q.size();
            
            while (len--)
            {
                if (0 == len)
                {
                    v_res.push_back(q.front()->val);
                }

                if (q.front()->left)
                {
                    q.push(q.front()->left);
                }

                if (q.front()->right)
                {
                    q.push(q.front()->right);
                }

                q.pop();
            }
        }

        return v_res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 200. 岛屿数量
// 深度优先 递归 回溯

class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        if (0 == grid.size())
        {
            return 0;
        }

        int res = 0;

        for (int row = 0; row <= grid.size() - 1; row++)
        {
            for (int col = 0; col <= grid[0].size() - 1; col++)
            {
                if ('1' == grid[row][col])
                {
                    res++;
                    dfs(grid, row, col); // 岛的其余部分清零
                }

            }
        }

        return res;
    }

private:
    void dfs(vector<vector<char>>& grid, int row, int col)
    {
        if (row < 0 || row >= grid.size() || 
            col < 0 || col >= grid[0].size() || 
            '0' == grid[row][col])
        {
            return ;
        }

        grid[row][col] = '0'; // 对岛清零, 沉岛

        dfs(grid, row + 1, col);
        dfs(grid, row - 1, col);
        dfs(grid, row, col + 1);
        dfs(grid, row, col - 1);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 202. 快乐数
// 哈希表 数学 进位
// 编写一个算法来判断一个数 n 是不是快乐数。「快乐数」定义为：对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和，然后重复这个过程直到这个数变为 1，也可能是 无限循环 但始终变不到 1。如果 可以变为  1，那么这个数就是快乐数。如果 n 是快乐数就返回 True ；不是，则返回 False 。

class Solution {
public:
    bool isHappy(int n) {
        std::unordered_set<int> m; // sum

        while (n != 1)
        {
            if (m.find(n) != m.end())
            {
                break; // 有循环
            }

            m.insert(n);
            n = sum(n);
        }

        return 1 == n;
    }

private:
    int sum(int n)
    {
        int res = 0;

        while (n)
        {
            res += (n % 10) * (n % 10);
            n /= 10;
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 203. 移除链表元素
// 链表

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        ListNode* dummy = new ListNode(0);
        dummy->next = head;
        ListNode* pre_node = dummy;

        while (pre_node->next)
        {
            if (val == pre_node->next->val)
            {
                auto del_node = pre_node->next;
                pre_node->next = pre_node->next->next;
                delete del_node;
            }
            else
            {
                pre_node = pre_node->next;
            }
        }
        return dummy->next;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 205. 同构字符串
// 字符串

class Solution {
public:
    bool isIsomorphic(string s, string t) {
        if (0 == s.size() && 0 == t.size())
        {
            return true;
        }

        for (int index = 0; index <= s.size() - 1; index++)
        {
            if (s.find(s[index]) != t.find(t[index]))
            {
                return false;
            }
        }

        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 206. 反转链表
// 链表 头插法

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        // 新链表的头尾(不断维护)
        ListNode* new_head = head;
        ListNode* new_tail = head;
        // 当前节点（用来头插法）
        ListNode* cur_node = new_tail->next;

        while (cur_node)
        {
            new_tail->next = cur_node->next; // 先维护链尾
            cur_node->next = new_head; // 当前节点往头插
            new_head = cur_node; // 维护链首
            cur_node = new_tail->next; // 当前节点遍历
        }

        return new_head;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 207. 课程表
// 拓扑排序 深度优先 递归

class Solution {
public:
    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
        std::vector<std::vector<int>> vv_graph(numCourses); // 邻接表
        std::vector<int> v_finish(numCourses, unknow);

        for (auto course : prerequisites)
        {
            vv_graph[course[0]].push_back(course[1]);
        }

        for (int index = 0; index <= numCourses - 1; index++)
        {
            if (finished == v_finish[index])
            {
                continue;
            }

            if (false == dfs(vv_graph, v_finish, index))
            {
                return false;
            }
        }

        return true;
    }

private:
    enum state {unknow, finishing, finished};
    // index表示课程编号，从0开始
    bool dfs(std::vector<std::vector<int>> vv_graph, 
             std::vector<int> v_finish, int index)
    {
        // 每次递归结束都会置成finished，当finished时说明已经完成了
        // 可以进行下一个课
        if (finished == v_finish[index])
        {
            return true;
        }
        // 当前课还没完成，说明是个环
        if (finishing == v_finish[index])
        {
            return false;
        }
        // 当前课状态未知，那么开始完成
        if (unknow == v_finish[index])
        {
            v_finish[index] = finishing;
        }
        // 查看当前的先导课有否全部完成
        for (auto index_course : vv_graph[index])
        {
            if (false == dfs(vv_graph, v_finish, index_course))
            {
                return false; // 若dfs进入的课是finishing，说明有环
            }
        }
        // 若当前先导课全部完成，那么当前课也可以完成
        v_finish[index] = finished;
        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 208. 实现 Trie (前缀树)
// 类 智能指针 前缀树

class Trie {
public:
    /** Initialize your data structure here. */
    Trie() // 通过智能指针构造，无需析构函数了
    : root(new TrieNode())
    {

    }

    /** Inserts a word into the trie. */
    void insert(string word) {
        TrieNode* p = root.get(); // p指向root
        for (const char c : word)
        {
            if (nullptr == p->children[c - 'a'])
            {
                p->children[c - 'a'] = new TrieNode();
            }
            p = p->children[c - 'a'];
        }
        // 表示以当前字符结尾的字符串是单词
        p->is_word = true; 
    }

    /** Returns if the word is in the trie. */
    bool search(string word) {
        const TrieNode* p = find(word);
        return p && p->is_word;
    }

    /** Returns if there is any word in the trie that starts with the given prefix. */
    bool startsWith(string prefix) {
        return find(prefix) != nullptr;
    }

private:
    struct TrieNode 
    {
        bool is_word; // 是否为字符
        std::vector<TrieNode*> children;
        // 构造函数
        TrieNode () 
        : is_word(false), children(26, nullptr) 
        {

        }
        // 析构函数
        ~TrieNode()
        {
            for (TrieNode* child : children)
            {
                if (child)
                {
                    delete child;
                }
            }
        }
    };
    // 根节点智能指针，默认为空，类似虚节点
    std::unique_ptr<TrieNode> root;
    // 返回字符串结尾指针
    const TrieNode* find(const string& prefix) const
    {
        const TrieNode* p = root.get(); // p指向root指针

        for (const char c : prefix)
        {
            p = p->children[c - 'a'];
            if (nullptr == p)
            {
                break;
            }
        }
        return p;
    }
};

/**
 * Your Trie object will be instantiated and called as such:
 * Trie* obj = new Trie();
 * obj->insert(word);
 * bool param_2 = obj->search(word);
 * bool param_3 = obj->startsWith(prefix);
 */

```
<div STYLE="page-break-after: always;"></div>

```c++

// 210. 课程表 II
// 深度优先 递归 拓扑排序

class Solution {
public:
    vector<int> findOrder(int numCourses, vector<vector<int>>& prerequisites) {
        std::vector<std::vector<int>> vv_graph(numCourses);
        std::vector<int> v_finish(numCourses, unknow);
        std::vector<int> v_res;

        for (auto course : prerequisites)
        {
            vv_graph[course[0]].push_back(course[1]);
        }

        for (int index = 0; index <= numCourses - 1; index++)
        {
            if (false == dfs(vv_graph, v_finish, index, v_res))
            {
                return {};
            }
        }

        return v_res;
    }

private:
    enum state {unknow, finishing, finished};
    bool dfs(std::vector<std::vector<int>> vv_graph,
             std::vector<int>& v_finish, int index,
             std::vector<int>& v_res)
    {
        if (finished == v_finish[index])
        {
            return true;
        }

        if (finishing == v_finish[index])
        {
            return false;
        }

        if (unknow == v_finish[index])
        {
            v_finish[index] = finishing;
        }

        for (auto index_course : vv_graph[index])
        {
            if (false == dfs(vv_graph, v_finish, index_course, v_res))
            {
                return false;
            }
        }

        v_finish[index] = finished;
        v_res.push_back(index);// 当前课程完成就入栈
        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="213"></div>

```c++

// 213. 打家劫舍 II
// 动态规划 滚动数组 双指针（跟随指针）

class Solution {
public:
    int rob(vector<int>& nums) {
        if (0 == nums.size())
        {
            return 0;
        }

        if (1 == nums.size())
        {
            return nums[0];
        }
        
        return std::max(_rob(nums, 0, nums.size() - 2), 
                        _rob(nums, 1, nums.size() - 1));
    }

private:
    int _rob(std::vector<int>& nums, int left, int right)
    {
        int cur = nums[left];
        int pre = 0;

        for (int index = left + 1; index <= right; index++)
        {
            int cur_temp = cur;
            cur = std::max(cur, pre + nums[index]);
            pre = cur_temp;
        }

        return cur;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int rob(vector<int>& nums) {
        if (0 == nums.size())
        {
            return 0;
        }

        if (1 == nums.size())
        {
            return nums[0];
        }

        int prepre = 0;
        int pre = 0;
        int cur = 0;
        int res = 0;

        for (int index = 0; index <= (int)nums.size() - 2; index++)
        {
            cur = std::max(pre, prepre + nums[index]);

            prepre = pre;
            pre = cur;
        }
        
        res = cur;
        prepre = pre = cur = 0;
        
        for (int index = 1; index <= (int)nums.size() - 1; index++)
        {
            cur = std::max(pre, prepre + nums[index]);

            prepre = pre;
            pre = cur;
        }

        res = std::max(res, cur);
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 215. 数组中的第K个最大元素
// 排序 数组

class Solution {
public:
    int findKthLargest(vector<int>& nums, int k) {
        std::sort(nums.begin(), nums.end());
        return nums[nums.size() - k];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 216. 组合总和 III
// 深度优先 回溯 递归

class Solution {
public:
    vector<vector<int>> combinationSum3(int k, int n) {
        std::vector<std::vector<int>> res;
        std::vector<int> buf;
        dfs(res, buf, k, n);
        return res;
    }

private:
    void dfs(std::vector<std::vector<int>>& res, std::vector<int>& buf, 
             int num, int sum, int cnt = 1)
    {
        if (0 == num && 0 == sum)
        {
            res.push_back(buf);
            return;
        }

        for (int idx = cnt; idx <= 9; idx++)
        {
            if (idx > sum)
            {
                return;
            }

            buf.push_back(idx);
            dfs(res, buf, num - 1, sum - idx, idx + 1); // 下一个index
            buf.pop_back();
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 217. 存在重复元素
// 哈希表 数组

class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
        std::unordered_map<int, int> count;

        for (auto i : nums)
        {
            count[i]++;

            if (1 < count[i])
            {
                return true;
            }
        }

        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 219. 存在重复元素 II
// 数组 哈希表

class Solution {
public:
    bool containsNearbyDuplicate(vector<int>& nums, int k) {
        if (0 == nums.size())
        {
            return false;
        }
        // 无重复，为了向后更新index
        std::unordered_map<int, int> m; // nums[index]->index

        for (int index = 0; index <= nums.size() - 1; index++)
        {
            // 已经存在且差小于k，不然就更新value(即index)
            if (0 != m.count(nums[index]) && index - m[nums[index]] <= k)
            {
                return true;
            }

            m[nums[index]] = index;
        }

        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="221"></div>

```c++

// 221. 最大正方形
// 动态规划 滚动数组

class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        if (0 == matrix.size())
        {
            return 0;
        } 

        int row = matrix.size();
        int col = matrix[0].size();
        std::vector<std::vector<int>> vvDp(row + 1, std::vector<int>(col + 1, 0));
        // 边界和初始化条件都为0，所以加+1
        int max_side = 0;

        for (int i = 1; i <= row; i++)
        {
            for (int j = 1; j <= col; j++)
            {
                if ('1' == matrix[i - 1][j - 1])
                {
                    vvDp[i][j] = 1 + std::min(vvDp[i - 1][j - 1], 
                                     std::min(vvDp[i - 1][j], 
                                              vvDp[i][j - 1]));
                    max_side = std::max(max_side, vvDp[i][j]);
                }
            }
        }

        return max_side * max_side;  
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        if (0 == matrix.size())
        {
            return 0;
        } 
        // 模板化解题
        vector<std::vector<int>> 
        dp(matrix.size() + 1, vector<int>(matrix[0].size() + 1, 0));
        
        int res = 0;

        for (int row = 0; row <= matrix.size(); row++)
        {
            for (int col = 0; col <= matrix[0].size(); col++)
            {
                if (0 == row && 0 == col)
                {
                    dp[0][0] = 0;
                }
                else if (0 == row && 0 != col)
                {
                    dp[0][col] = 0;
                }
                else if (0 != row && 0 == col)
                {
                    dp[row][0] = 0;
                }
                else if ('1' == matrix[row - 1][col - 1])
                {
                    dp[row][col] = 1 + min(dp[row - 1][col - 1], 
                                       min(dp[row - 1][col], 
                                           dp[row][col - 1]));
                }

                if (dp[row][col])
                {
                    res = max(res, dp[row][col] * dp[row][col]);
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        if (0 == matrix.size())
        {
            return 0;
        } 
        // 模板化解题
        vector<std::vector<int>> dp(2, vector<int>(matrix[0].size() + 1, 0));
        
        int res = 0;

        for (int row = 0; row <= matrix.size(); row++)
        {
            for (int col = 0; col <= matrix[0].size(); col++)
            {
                if (0 == row && 0 == col)
                {
                    dp[0][0] = 0;
                }
                else if (0 == row && 0 != col)
                {
                    dp[0][col] = 0;
                }
                else if (0 != row && 0 == col)
                {
                    dp[row % 2][0] = 0;
                }
                else if ('1' == matrix[row - 1][col - 1])
                {
                    dp[row % 2][col] = 1 + min(dp[(row + 1) % 2][col - 1], 
                                           min(dp[(row + 1) % 2][col], 
                                               dp[row % 2][col - 1]));
                }
                else 
                {
                    dp[row % 2][col] = 0;
                }

                if (dp[row % 2][col])
                {
                    res = max(res, dp[row % 2][col] * dp[row % 2][col]);
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 221. 最大正方形
// 动态规划 矩阵
// 在一个由 0 和 1 组成的二维矩阵内，找到只包含 1 的最大正方形，并返回其面积。

class Solution {
public:
    int maximalSquare(vector<vector<char>>& matrix) {
        if (matrix.size() == 0 || matrix[0].size() == 0) 
        {
            return 0;
        }
        int res = 0;

        std::vector<std::vector<int>> dp(matrix.size(), std::vector<int>(matrix[0].size()));

        for (int row = 0; row <= (int)matrix.size() - 1; row++) 
        {
            for (int col = 0; col <= (int)matrix[row].size() - 1; col++) 
            {
                if (matrix[row][col] == '1') 
                {
                    if (row == 0 || col == 0) 
                    {
                        dp[row][col] = 1;
                    } 
                    else 
                    {
                        dp[row][col] = std::min(dp[row - 1][col - 1]， 
                                       std::min(dp[row - 1][col], dp[row][col - 1])) + 1;
                    }
                    res = max(res, dp[row][col] * dp[row][col]);
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 222. 完全二叉树的节点个数
// 树 深度优先

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int countNodes(TreeNode* root) {
        if (nullptr == root)
        {
            return 0;
        }

        int left_height = dfs(root->left);
        int right_height = dfs(root->right);

        if (left_height == right_height)
        {
            // 左子树和右子树高度相等
            // 左子树为满二叉树
            return (1 << left_height) - 1 + countNodes(root->right) + 1;
        }
        else // if (left_height == right_height + 1)
        {
            // 右子树为满二叉树
            return countNodes(root->left) + (1 << right_height) - 1 + 1;
        }
    }

private:
    // 求高度
    int dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return 0;
        }
        // 完全二叉树左边肯定存在
        return dfs(root->left) + 1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 225. 用队列实现栈
// 队 栈 

class MyStack {
public:
    /** Initialize your data structure here. */
    MyStack() {

    }

    /** Push element x onto stack. */
    void push(int x) {
        int len = q.size();
        q.push(x);

        while (len--)
        {
            int temp = q.front(); // 先弹出来再塞进去
            q.pop();
            q.push(temp);
        }
    }

    /** Removes the element on top of the stack and returns that element. */
    int pop() {
        int res = q.front();
        q.pop();
        return res;
    }

    /** Get the top element. */
    int top() {
        return q.front();
    }

    /** Returns whether the stack is empty. */
    bool empty() {
        return q.empty();
    }

private:
    std::queue<int> q;
};

/**
 * Your MyStack object will be instantiated and called as such:
 * MyStack* obj = new MyStack();
 * obj->push(x);
 * int param_2 = obj->pop();
 * int param_3 = obj->top();
 * bool param_4 = obj->empty();
 */

```
<div STYLE="page-break-after: always;"></div>

```c++

// 226. 翻转二叉树
// 深度优先 树 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        if (nullptr == root)
        {
            return nullptr;
        }

        auto temp = root->left;
        root->left = root->right;
        root->right = temp;

        root->left = invertTree(root->left);
        root->right = invertTree(root->right);

        return root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 230. 二叉搜索树中第K小的元素
// 深度优先 递归 中序遍历

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int kthSmallest(TreeNode* root, int k) {
        int res = 0;
        dfs(root, k, res);
        return res;
    }

private:
    int cnt = 0;
    void dfs(TreeNode* root, const int k, int& res)
    {
        if (nullptr == root)
        {
            return;
        }

        dfs(root->left, k, res);
        // 中序遍历
        if (++cnt == k)
        {
            res = root->val;
            return;
        }

        dfs(root->right, k, res);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 232. 用栈实现队列
// 栈 队列

class MyQueue {
public:
    /** Initialize your data structure here. */
    MyQueue() {

    }
    
    /** Push element x to the back of queue. */
    void push(int x) {
        std::stack<int> s_temp;
        // 把数据倒到临时垃圾桶里
        while (false == s.empty())
        {
            s_temp.push(s.top());
            s.pop();
        }
        // 把新的垃圾倒到旧的垃圾桶
        s.push(x);
        // 把垃圾再从新的垃圾桶倒到旧垃圾桶里
        while (false == s_temp.empty())
        {
            s.push(s_temp.top());
            s_temp.pop();
        }
    }
    
    /** Removes the element from in front of queue and returns that element. */
    int pop() {
        int x = s.top();
        s.pop();
        return x;
    }
    
    /** Get the front element. */
    int peek() {
        return s.top();
    }
    
    /** Returns whether the queue is empty. */
    bool empty() {
        return s.empty();
    }

private:
    std::stack<int> s;
};

/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue* obj = new MyQueue();
 * obj->push(x);
 * int param_2 = obj->pop();
 * int param_3 = obj->peek();
 * bool param_4 = obj->empty();
 */

```
<div STYLE="page-break-after: always;"></div>

```c++

// 234. 回文链表
// 链表

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        std::vector<int> buf;

        while (head)
        {
            buf.push_back(head->val);
            head = head->next;
        }

        for (int left = 0, right = buf.size() - 1; 
             left < right; left++, right--)
        {
            if (buf[left] != buf[right])
            {
                return false;
            }
        }

        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 235. 二叉搜索树的最近公共祖先
// 深度优先 递归 树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        // 三种情况：
        // p,q都在当前根节点左边
        // p,q都在当前根节点右边
        // p,q分别在当前根节点左后两边，此时根节点就是祖先

        if (nullptr == root)
        {
            return nullptr; // 全部砍掉
        }
        else if (p->val < root->val && q->val < root->val)
        {
            // 砍掉右边
            return lowestCommonAncestor(root->left, p, q);
        }
        else if (p->val > root->val && q->val > root->val)
        {
            // 砍掉左边
            return lowestCommonAncestor(root->right, p, q);
        }
        else // (p->val - root->val) * (q->val - root->val) <= 0
        {
            // 全部留着
            return root;
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 236. 二叉树的最近公共祖先
// 深度优先 递归 后序遍历 回溯 树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if (nullptr == root || p == root || q == root)
        {
            return root; // 递归出口
        }

        TreeNode* left = lowestCommonAncestor(root->left, p, q);
        TreeNode* right = lowestCommonAncestor(root->right, p, q);
        // 后序遍历 从底往上回溯
        if (nullptr == left && nullptr == right)
        {
            return nullptr;
        }
        else if (nullptr == left)
        {
            return right;
        }
        else if (nullptr == right)
        {
            return left;
        }
        else // left != nullptr && right != nullptr
        {
            return root;
        }
    }
};

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if (nullptr == root || p == root || q == root)
        {
            // 全部砍掉
            return root;
        }
        else if (nullptr == lowestCommonAncestor(root->left, p, q))
        {
            // 砍掉左边
            return lowestCommonAncestor(root->right, p, q);
        }
        else if (nullptr == lowestCommonAncestor(root->right, p, q))
        {
            // 砍掉右边
            return lowestCommonAncestor(root->left, p, q);
        }
        else // nullptr != left && nullptr != right
        {
            // 全部留着
            return root;
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 237. 删除链表中的节点
// 链表

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    void deleteNode(ListNode* node) {
        node->val = node->next->val;
        node->next = node->next->next;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 239. 滑动窗口最大值
// 滑动窗口 队

class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        std::deque<int> q;
        std::vector<int> res;

        for (int index = 0; index <= nums.size() - 1; index++)
        {
            while (false == q.empty() && nums[index] >= nums[q.back()])
            {
                q.pop_back();
            }
            q.push_back(index);

            if (index - k + 1 >= 0)
            {
                res.push_back(nums[q.front()]);
            }

            if (index - k + 1 >= q.front())
            {
                q.pop_front();
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 240. 搜索二维矩阵 II
// 二分法 矩阵

class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        if (0 == matrix.size() || 0 == matrix[0].size())
        {
            return false;
        }
        // 从右上角开始
        int row = 0;
        int col = matrix[0].size() - 1;

        while (row <= matrix.size() - 1 && col >= 0)
        {
            if (target == matrix[row][col])
            {
                return true;
            }
            else if (target > matrix[row][col])
            {
                row++;
            }
            else if (target < matrix[row][col])
            {
                col--;
            }
        }
        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 241. 为运算表达式设计优先级
// 分治 字符串 深度优先 递归

class Solution {
public:
    vector<int> diffWaysToCompute(string input) {
        return dfs(input);
    }

private:
    std::vector<int> dfs(std::string s)
    {
        std::vector<int> res;

        if (s.find_first_of("+-*") == std::string::npos)
        {
            res.push_back(std::stoi(s));
        }

        for (int index = 0; index <= s.size() - 1; index++)
        {
            if (std::isdigit(s[index]))
            {
                continue;
            }

            std::vector<int> left_s = dfs(s.substr(0, index));
            std::vector<int> right_s = dfs(s.substr(index + 1));

            for (auto l_s : left_s)
            {
                for (auto r_s : right_s)
                {
                    if ('+' == s[index])
                    {
                        res.push_back(l_s + r_s);
                    }
                    else if ('-' == s[index])
                    {
                        res.push_back(l_s - r_s);
                    }
                    else if ('*' == s[index])
                    {
                        res.push_back(l_s * r_s);
                    }
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 242. 有效的字母异位词
// 哈希表 字符串

class Solution {
public:
    bool isAnagram(string s, string t) {
        if (s.size() != t.size())
        {
            return false;
        }

        if (0 == s.size() && 0 == t.size())
        {
            return true;
        }

        std::vector<int> set(26,0);

        for (int index = 0; index <= s.size() - 1; index++)
        {
            set[s[index] - 'a']++;
            set[t[index] - 'a']--;
        }

        for (int index = 0; index < 26; index++)
        {
            if (0 != set[index])
            {
                return false;
            }
        }

        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 250. 统计同值子树
// 深度优先 后序遍历 二叉树 
// 给定一个二叉树，统计该二叉树数值相同的子树个数。同值子树是指该子树的所有节点都拥有相同的数值。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int countUnivalSubtrees(TreeNode* root) {
        return dfs(root).count;
    }

    class CRes
    {
    public:
        bool is_same;
        int count;

        CRes(bool is_same, int count)
        : is_same(is_same), count(count)
        {}
    };

    CRes dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return CRes(true, 0);
        }

        CRes left_res = dfs(root->left);
        CRes right_res = dfs(root->right);

        
        bool left_is_same = left_res.is_same && 
                            (nullptr == root->left || root->val == root->left->val);
        bool right_is_same = right_res.is_same && 
                             (nullptr == root->right || root->val == root->right->val);

        bool cur_is_same = left_is_same && right_is_same;

        int cur_count = (cur_is_same) ? left_res.count + right_res.count + 1 : 
                                        left_res.count + right_res.count;

        return CRes(cur_is_same, cur_count);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 254. 因子的组合
// 深度优先 减枝 递归
// 整数可以被看作是其因子的乘积。8 = 2 x 2 x 2 = 2 x 4; 请实现一个函数，该函数接收一个整数 n 并返回该整数所有的因子组合。

class Solution {
public:
    vector<vector<int>> getFactors(int n) {
        std::vector<int> buf;
        dfs(n, 2, buf);
        return res;
    }

private:
    std::vector<std::vector<int>> res;

    void dfs(int n, int index, std::vector<int>& buf)
    {
        if (1 == n)
        {
            return;
        }

        for (int i = index; i * i <= n; i++)
        {
            if (n % i != 0)
            {
                continue;
            }
            
            buf.push_back(i);
            buf.push_back(n / i); // 减枝 导致 i * i <= n
            res.push_back(buf);
            buf.pop_back();
            dfs(n / i, i, buf);
            buf.pop_back();
        }
    }  
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 255. 验证前序遍历序列二叉搜索树
// 二叉树 单调栈
// 给定一个整数数组，你需要验证它是否是一个二叉搜索树正确的先序遍历序列。你可以假定该序列中的数都是不相同的。

class Solution {
public:
    bool verifyPreorder(vector<int>& preorder) {
        std::stack<int> s; // increase stack
        int cur_min = INT_MIN;

        for (auto node : preorder)
        {
            if (node < cur_min) // 总体递增
            {
                return false; 
            }

            while (false == s.empty() && node > s.top()) // 局部递减
            {
                cur_min = s.top();
                s.pop();
            }

            s.push(node);
        }
        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 257. 二叉树的所有路径
// 二叉树 深度优先 回溯 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<string> binaryTreePaths(TreeNode* root) {
        std::vector<std::string> res; 
        std::string buf;
        dfs(root, res, buf);
        return res;
    }

private:
    void dfs(TreeNode* root, std::vector<std::string>& res, std::string buf)
    {
        if (nullptr == root)
        {
            return;
        }

        if (nullptr == root->left && nullptr == root->right)
        {
            buf += (buf.empty() ? "" : "->") + to_string(root->val);
            res.push_back(buf);
            return;
        }

        buf += (buf.empty() ? "" : "->") + to_string(root->val);

        dfs(root->left, res, buf);
        dfs(root->right, res, buf);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 268. 缺失数字
// 数学

class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int len = nums.size();
        int res = (len + 1) * len >> 1;

        while (len--)
        {
            res -= nums[len];
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 270. 最接近的二叉搜索树值
// 深度优先 二叉树 递归
// 给定一个不为空的二叉搜索树和一个目标值 target，请在该二叉搜索树中找到最接近目标值 target 的数值。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int closestValue(TreeNode* root, double target) {
        res = root->val; // 注意 不能是INT_MAX，这样会导致abs结果出现为0
        dfs(root, target);
        return res;
    }

private:
    double res;

    void dfs(TreeNode* root, double target)
    {
        if (nullptr == root)
        {
            return;
        }

        if (std::abs(root->val - target) < std::abs(res - target))
        {
            res = root->val;
        }

        dfs(root->left, target);
        dfs(root->right, target);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 274. H 指数
// 计数排序 数组

class Solution {
public:
    int hIndex(vector<int>& citations) {
        int len = citations.size();
        int h = len;
        int sum = 0;

        std::vector<int> count(len + 1, 0);

        for (auto citation : citations)
        {
            count[std::min(len, citation)] += 1;
        }

        sum = count[len];

        while (sum < h)
        {
            h--;
            sum += count[h];
        }

        return h;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 278. 第一个错误的版本
// 二分法

// The API isBadVersion is defined for you.
bool isBadVersion(int version);

class Solution {
public:
    int firstBadVersion(int n) {
        // 二分双闭区间流派
        // [L, R] 当L = R时，mid = L = R
        int left = 1;
        int right = n;
        int res = n;

        while (left <= right)
        {
            int mid = left + (right - left) / 2;

            if (true == isBadVersion(mid))
            {
                right = mid - 1;
                res = mid; // 等价于res = std::min(res, mid);
            }
            else if (false == isBadVersion(mid))
            {
                left = mid + 1;
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 279. 完全平方数
// 广度优先 队 动态规划 

class Solution {
public:
    int numSquares(int n) {
        std::vector<int> squ; // 存入完全平方数
        for (int i = 1; i * i <= n; i++)
        {
            squ.push_back(i * i);
        }

        std::queue<int> q; 
        q.push(n);
        int count = 0;

        while (false == q.empty())
        {
            count++;
            int len = q.size();

            while (len--)
            {
                int dif = q.front();
                q.pop();
                for (auto num : squ) // 对于可选完全数
                {
                    if (dif == num)
                    {
                        return count;
                    }
                    else if (dif < num)
                    {
                        break;
                    }
                    else if (dif > num)
                    {
                        q.push(dif - num);
                    }
                }
            }
        }
        return count;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int numSquares(int n) {
        std::vector<int> dp(n + 1, 0);

        for (int fast = 1; fast <= n; fast++)
        {
            dp[fast] = fast;
            for (int slow = 0; slow * slow <= fast; slow++)
            {
                dp[fast] = std::min(dp[fast], dp[fast - slow * slow] + 1);
            }
        }
        return dp[n];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 283. 移动零
// 数组 双指针（快慢指针）

class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        for (int fast = 0, slow = 0; fast <= nums.size() - 1; )
        {
            if (0 == nums[fast])
            {
                fast++;
            }
            else if (0 != nums[fast])
            {
                nums[slow++] = nums[fast++];
            }

            if (fast == nums.size())
            {
                while (slow <= nums.size() - 1)
                {
                    nums[slow++] = 0;
                }
            }
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 285. 二叉搜索树中的顺序后继
// 中序遍历 深度优先 二叉树
// 给你一个二叉搜索树和其中的某一个结点，请你找出该结点在树中顺序后继的节点。结点 p 的后继是值比 p.val 大的结点中键值最小的结点。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* inorderSuccessor(TreeNode* root, TreeNode* p) {
        res = nullptr;
        dfs(root, p);
        return res;
    }

private:
    TreeNode* res;

    void dfs(TreeNode* root, TreeNode* p)
    {
        if (nullptr == root)
        {
            return;
        }

        dfs(root->left, p);
        if (nullptr == res && root->val > p->val)
        {
            res = root;
            return ;
        }
        dfs(root->right, p);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 287. 寻找重复数
// 哈希表 数组

class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        // 原地哈希表
        // 对于第i个数，0<=nums[i]-1<=n-1，将nums[i]-1作为下标，
        // nums[nums[i]-1]也必定存在。
        // 循环时，将|nums[i]|作为原值，将|nums[i]|-1作为哈希值，
        // 使nums[|nums[i]|-1]从正数变为负数。
        // 如果nums[|nums[i]|-1]为负数，
        // 则表示之前已经搜索到过nums[i]，直接返回即可。

        for (int index = 0; index <= nums.size() - 1; index++)
        {
            if (nums[std::abs(nums[index]) - 1] < 0)
            {
                return std::abs(nums[index]);
            }
            nums[std::abs(nums[index]) - 1] *= -1;
        }
        return 0;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 289. 生命游戏
// 数组 位运算

class Solution {
public:
    void gameOfLife(vector<vector<int>>& board) {
        if (0 == board.size())
        {
            return;
        }

        /*
        利用一个 two bits 的状态机来记录细胞状态, 第一位表示
        下一状态, 第二位表示当前状态:
        00: dead (next state) <- dead (current state)
        01: dead (next state) <- live (current state) 
        10: live (next state) <- dead (current state)
        11: live (next state) <- live (current state) 
        初始情况对应就是 00 和 01 (默认下一状态是 dead state)
        统计每个位置周围的 live 细胞数决定高位置 1 (live)还是 
        0 (dead), 最后右移一位即为最终状态, 注意不需要考虑 01
        以及 00 的情况, 因为已经默认下一状态为 dead.
        */

        int row = board.size();
        int col = board[0].size();

        for (int i = 0; i <= row - 1; i++)
        {
            for (int j = 0; j <= col - 1; j++)
            {
                int live_count = 0;
                // 扫描 3x3 矩阵统计存活细胞,包括当前自己
                for (int x = std::max(i - 1, 0); 
                     x < std::min(row, i + 2); x++)
                {
                    for (int y = std::max(j - 1, 0); 
                         y < std::min(col, j + 2); y++)
                    {
                        live_count += board[x][y] & 1;
                    }
                }
                // 压缩状态（2个+自己 || 3个不加自己（3-0），3个加自己（4-0））
                if (3 == live_count || live_count - (board[i][j] & 1) == 3)
                {
                    board[i][j] |= 0b10;
                }
            }
        }
        // 更新矩阵
        for (int i = 0; i <= row - 1; i++)
        {
            for (int j = 0; j <= col - 1; j++)
            {
                board[i][j] >>= 1;
            }
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 290. 单词规律
// 字符串分割 哈希表 字符串
// 给定一种规律 pattern 和一个字符串 str ，判断 str 是否遵循相同的规律。这里的 遵循 指完全匹配，例如， pattern 里的每个字母和字符串 str 中的每个非空单词之间存在着双向连接的对应规律。

class Solution {
public:
    bool wordPattern(string pattern, string str) {
        std::unordered_map<char, std::string> m1; // pattern => string
        std::unordered_map<std::string, char> m2; // string => pattern
        std::vector<std::string> v;

        split(str, v, " ");

        if (v.size() != pattern.size())
        {
            return false;
        }

        for (int index = 0; index <= (int)pattern.size() - 1; index++)
        {
            if (m1.find(pattern[index]) != m1.end() && m1[pattern[index]] != v[index] ||
                m2.find(v[index]) != m2.end() && m2[v[index]] != pattern[index])
            {
                return false;
            }

            m1[pattern[index]] = v[index];
            m2[v[index]] = pattern[index];
        }

        return true;
    }

private:
    // 字符串分割函数
    void split(const std::string& s, std::vector<std::string>& res, const std::string& c)
    {
        std::string::size_type slow = 0;
        std::string::size_type fast = s.find(c);

        while (std::string::npos != fast)
        {
            res.push_back(s.substr(slow, fast - slow));

            slow = fast + 1;
            fast = s.find(c, slow);
        }

        if (slow != s.size())
        {
            res.push_back(s.substr(slow));
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    bool wordPattern(string pattern, string str) {
        std::unordered_map<char, std::string> m1; // pattern => string
        std::unordered_map<std::string, char> m2; // string => pattern
        std::vector<std::string> v;

        split(str, v, " ");

        if (v.size() != pattern.size())
        {
            return false;
        }

        for (int index = 0; index <= (int)pattern.size() - 1; index++)
        {
            if (m1.find(pattern[index]) != m1.end())
            {
                if (m1[pattern[index]] != v[index])
                {
                    return false;
                }
            }

            if (m2.find(v[index]) != m2.end())
            {
                if (m2[v[index]] != pattern[index])
                {
                    return false;
                }
            }

            m1[pattern[index]] = v[index];
            m2[v[index]] = pattern[index];
        }

        return true;
    }

private:
    // 字符串分割函数
    void split(const std::string& s, std::vector<std::string>& res, const string& c)
    {
        std::string::size_type slow = 0;
        std::string::size_type fast = s.find(c);

        while (std::string::npos != fast)
        {
            res.push_back(s.substr(slow, fast - slow));

            slow = fast + 1;
            fast = s.find(c, slow);
        }

        if (slow != s.size())
        {
            res.push_back(s.substr(slow));
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 292. Nim 游戏
// 数学

class Solution {
public:
    bool canWinNim(int n) {
        return (n % 4 != 0);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 298. 二叉树最长连续序列
// 后序遍历 深度优先 递归 二叉树
// 给你一棵指定的二叉树，请你计算它最长连续序列路径的长度。该路径，可以是从某个初始结点到树中任意结点，通过「父 - 子」关系连接而产生的任意路径。这个最长连续的路径，必须从父结点到子结点，反过来是不可以的。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int longestConsecutive(TreeNode* root) {
        dfs(root);
        return res;
    }

private:
    int res;
    int dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return 0;
        }

        int left_len = dfs(root->left) + 1;
        int right_len = dfs(root->right) + 1;

        if (root->left && root->val + 1 != root->left->val)
        {
            left_len = 1;
        }

        if (root->right && root->val + 1 != root->right->val)
        {
            right_len = 1;
        }

        int cur_len = std::max(left_len, right_len);
        res = std::max(res, cur_len);
        return cur_len;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int longestConsecutive(TreeNode* root) {
        return dfs(root).res;
    }

    class CRes
    {
    public:
        int res;
        int len;

        CRes(int res, int len)
        : res(res), len(len)
        {}
    };

    CRes dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return CRes(0, 0);
        }

        CRes left_res = dfs(root->left);
        CRes right_res = dfs(root->right);

        int left_len = (root->left && root->left->val != root->val + 1) ? 1 : left_res.len + 1;
        int right_len = (root->right && root->right->val != root->val + 1) ? 1 : right_res.len + 1;
        int cur_len = std::max(left_len, right_len);
        int cur_res = std::max(left_res.res, right_res.res);
        cur_res = std::max(cur_len, cur_res);

        return CRes(cur_res, cur_len);
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="300"></div>

```c++

// 300. 最长上升子序列
// 动态规划 双指针（快慢指针）二分查找 单调栈

class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        // dp[i] 表示以i结尾且选i时的LIS长度
        // dp[i] = max dp[j] + 1 (0 <= j <= i - 1 且 nums[j] < nums[i])
        int len = nums.size();

        if (0 == len)
        {
            return 0;
        }

        std::vector<int> dp(len, 1); // 初始化为1
        int res = 1; // 至少有1

        for (std::size_t fast = 1; fast <= len - 1; fast++)
        {
            for (std::size_t slow = 0; slow <= fast - 1; slow++)
            {
                if (nums[slow] < nums[fast])
                {
                    dp[fast] = std::max(dp[fast], dp[slow] + 1); 
                }

                res = std::max(res, dp[fast]);
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int lengthOfLIS(vector<int>& nums) {
        int len = nums.size();
        std::vector<int> res; // 单调栈

        for (auto num : nums)
        {
            // 二分查找,从返回数组里找到下标
            int pos = std::lower_bound(res.begin(), res.end(), num) \
                      - res.begin();

            if (pos == res.size()) // 最小尾巴值
            {
                res.push_back(num);
            }
            else // 如果找到的位置在res原来尾巴前面
            {
                res[pos] = num; // 更新pos对应的值
            }
        }

        return res.size();
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 303. 区域和检索 - 数组不可变
// 前缀和 

class NumArray {
public:
    std::vector<int> sums;

    NumArray(vector<int>& nums) {
        sums.push_back(0); // 第一位空和，这样可以不用特判
        for (auto num : nums)
        {
            // 下标从1开始是有效值
            sums.push_back(sums.back() + num);
        }
    }
    
    int sumRange(int i, int j) {
        return sums[j + 1] - sums[i];
    }
};

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray* obj = new NumArray(nums);
 * int param_1 = obj->sumRange(i,j);
 */

```
<div STYLE="page-break-after: always;"></div>

```c++

// 304. 二维区域和检索 - 矩阵不可变
// 前缀和 数组

class NumMatrix {
public:
    std::vector<std::vector<int>> sums;

    NumMatrix(vector<vector<int>>& matrix) {
        if (0 == matrix.size() || 0 == matrix[0].size())
        {
            return;
        }
        // 多一行多一列
        sums.assign(matrix.size() + 1, std::vector<int>(matrix[0].size() + 1, 0));
        // row,col是二维数组下标，填到sums里,和sums差一行
        for (int row = 0; row <= matrix.size() - 1; row++)
        {       
            for (int col = 0; col <= matrix[0].size() - 1; col++)
            {
                sums[row + 1][col + 1] = \
                sums[row][col + 1] + sums[row + 1][col] \
                - sums[row][col] + matrix[row][col];
            }
        }   
    }
    
    int sumRegion(int row1, int col1, int row2, int col2) {
        return sums[row2 + 1][col2 + 1] 
               - sums[row1][col2 + 1] 
               - sums[row2 + 1][col1] 
               + sums[row1][col1];
    }
};

/**
 * Your NumMatrix object will be instantiated and called as such:
 * NumMatrix* obj = new NumMatrix(matrix);
 * int param_1 = obj->sumRegion(row1,col1,row2,col2);
 */

```
<div STYLE="page-break-after: always;"></div>

<div id="309"></div>

```c++

// 309. 最佳买卖股票时机含冷冻期
// 动态规划 滚动数组

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        // “冷冻期”=卖出的那一天的后一天，题目设置冷冻期的意思是，
        // 如果昨天卖出了，今天不可买入，那么关键在于哪一天卖出，
        // 只要在今天想买入的时候判断一下前一天是不是刚卖出。
        // 因为当天卖出股票实际上也是属于“不持有”的状态，
        // 那么第i天如果不持有，那这个“不持有”就有了两种状态：
        //   1.本来就不持有，指不是因为当天卖出了才不持有的；
        //   2.第i天因为卖出了股票才变得不持有.

        // dp[i][0]表示不持股且当天没卖出的最大收益
        // dp[i][1]表示持有
        // dp[i][2]表示不持股且当天卖出了的最大收益
        std::vector<std::vector<int>> 
        dp(prices.size(), std::vector<int>(3, 0)); 
        dp[0][0] = 0;
        dp[0][1] = -prices[0];
        dp[0][2] = 0;

        for (int day = 1; day <= prices.size() - 1; day++)
        {
            dp[day][0] = std::max(dp[day - 1][0], dp[day - 1][2]);
            dp[day][1] = std::max(dp[day - 1][1], dp[day - 1][0] - prices[day]);
            dp[day][2] = dp[day - 1][1] + prices[day];
        }
        return std::max(dp[prices.size() - 1][0], dp[prices.size() - 1][2]);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if (2 > prices.size())
        {
            return 0;
        }
        // 滚动数组
        int cash = 0;
        int hold = 0 - prices[0];
        int sold = 0;

        for (int day = 1; day <= prices.size() - 1; day++)
        {
            int had_cash = cash;
            cash = std::max(cash, sold);
            hold = std::max(hold, had_cash - prices[day]);
            sold = hold + prices[day];
        }
        return std::max(cash, sold);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 314. 二叉树的垂直遍历
// 层次遍历 二叉树 广度优先 队 哈希表

给定一个二叉树，返回其结点 垂直方向（从上到下，逐列）遍历的值。
如果两个结点在同一行和列，那么顺序则为 从左到右。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> verticalOrder(TreeNode* root) {
        std::vector<std::vector<int>> res;
        if (nullptr == root)
        {
            return res;
        }
        std::map<int, std::vector<int>> m; // col => node->vals
        std::queue<std::pair<TreeNode*, int>> q; // node => col
        q.push({root, 0});

        while (!q.empty())
        {
            TreeNode* cur_node = q.front().first;
            int cur_col = q.front().second;
            q.pop();

            m[cur_col].push_back(cur_node->val);

            if (cur_node->left)
            {
                q.push({cur_node->left, cur_col - 1});
            }

            if (cur_node->right)
            {
                q.push({cur_node->right, cur_col + 1});
            }   
        }

        for (auto& nodes : m)
        {
            res.push_back(std::move(nodes.second));
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 316. 去除重复字母
// 单调栈 字符串

class Solution {
public:
    string removeDuplicateLetters(string s) {
        if (0 == s.size())
        {
            return s;
        }
        // 题设是不重复的序列，肯定没有aab和abb这种比较
        std::unordered_map<char, int> m;
        for (char c : s)
        {
            m[c]++;
        }

        std::string res; // 单调栈

        // 单调栈
        for (char c : s)
        {
            if (res.find(c) == std::string::npos) // 去重
            {
                while (res.size() && res.back() > c && m[res.back()] > 0)  
                {
                    // 每次取尽可能小的
                    // 当栈顶元素大于当前元素、有重复就能删
                    res.pop_back();
                }

                res += c; // push
            }

            m[c]--; // 后面c个数少一个
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="322"></div>

```c++

// 322. 零钱兑换
// 动态规划 滚动数组 双指针（快慢指针）

class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {
        // 完全背包
        // 对于要凑出某个数的题，可以初始化为不可能的值比如-1

        std::vector<int> dp(amount + 1, -1); // 滚动数组
        dp[0] = 0; // 0元只要0个硬币

        for (auto slow : coins)
        {
            for (int fast = slow; fast <= amount; fast++)
            {
                if (-1 == dp[fast - slow])
                {
                    // 初始的时候只有fast - slow = 0才符合
                    // 即刚好凑上
                    // 要是-1都是凑不上的那些
                    continue; 
                }
                // 排除凑不上的那些
                // 因为是求最小的，-1最小，所以要特判
                if (-1 == dp[fast])
                {
                    dp[fast] = dp[fast - slow] + 1; // 加上本身的一个
                    continue;
                }
                // 转移方程
                // 上一行（不选）还是重新凑（选）
                dp[fast] = std::min(dp[fast], dp[fast - slow] + 1);
            }
        }
        return dp[amount];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 328. 奇偶链表
// 链表

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* oddEvenList(ListNode* head) {
        if (nullptr == head || nullptr == head->next)
        {
            return head;
        }

        ListNode* odd_head = head;
        ListNode* odd_tail = head;
        ListNode* even_head = head->next;
        ListNode* even_tail = head->next;

        while (odd_tail->next && even_tail->next)
        {
            odd_tail->next = even_tail->next;
            odd_tail = odd_tail->next;

            even_tail->next = odd_tail->next;
            even_tail = even_tail->next;
        }

        odd_tail->next = even_head;
        return head;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 332. 重新安排行程
// 哈希表 优先队列 深度优先 递归 图 邻接表

class Solution {
public:
    vector<string> findItinerary(vector<vector<string>>& tickets) {
        // 哈希表 key是字符串 value是vector实现的优先队列
        // 邻接表
        std::map<std::string, 
                 std::priority_queue<std::string, 
                                     std::vector<std::string>, 
                                     greater<std::string>>> map_graph;
        std::vector<std::string> v_res;

        for (auto& ticket : tickets)
        {
            map_graph[ticket[0]].push(ticket[1]);
        }

        dfs(map_graph, "JFK", v_res);

        std::reverse(v_res.begin(), v_res.end());

        return v_res;
    }

private:
    void dfs(std::map<std::string, 
             std::priority_queue<std::string, 
                                 std::vector<std::string>, 
                                 greater<std::string>>>& map_graph,
             std::string s_start, std::vector<std::string>& v_res)
    {
        // 邻接表中当前航班的表不为空
        while (false == map_graph[s_start].empty())
        {
            string s_next = map_graph[s_start].top(); // 下一班
            map_graph[s_start].pop(); // 飞走的出队列
            dfs(map_graph, s_next, v_res);
            // dfs一直到最后一班
        }
        // 最后一班会先压进去，所以最后要reverse
        v_res.push_back(s_start);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 333. 最大 BST 子树
// 二叉树 后序遍历 深度优先 树状DP 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int largestBSTSubtree(TreeNode* root) {
        return dfs(root).max_bst_size;
    }

    class CRes
    {
    public:
        TreeNode* max_bst_head;
        int max_bst_size;
        int min_val;
        int max_val;

        CRes(TreeNode* max_bst_head, int max_bst_size, int min_val, int max_val)
        : max_bst_head(max_bst_head), max_bst_size(max_bst_size), 
          min_val(min_val), max_val(max_val)
        {}
    };

    CRes dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return CRes(nullptr, 0, INT_MAX, INT_MIN);
        }

        CRes left_res = dfs(root->left);
        CRes right_res = dfs(root->right);

        int cur_min = std::min(root->val, std::min(left_res.min_val, right_res.min_val));
        int cur_max = std::max(root->val, std::max(left_res.max_val, right_res.max_val));
        int cur_bst_size = std::max(left_res.max_bst_size, right_res.max_bst_size);
        TreeNode* cur_head = left_res.max_bst_size > right_res.max_bst_size ?
                             left_res.max_bst_head : right_res.max_bst_head;
        
        if (left_res.max_bst_head == root->left &&
            right_res.max_bst_head == root->right &&
            left_res.max_val < root->val &&
            right_res.min_val > root->val)
        {
            cur_bst_size = left_res.max_bst_size + right_res.max_bst_size + 1;
            cur_head = root;
        }

        return CRes(cur_head, cur_bst_size, cur_min, cur_max);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 337. 打家劫舍 III
// 深度优先 递归 二叉树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int rob(TreeNode* root) {
        std::pair<int, int> p_res = dfs(root);
        // first表示不抢
        // second表示抢
        return std::max(p_res.first, p_res.second);
    }

private:
    std::pair<int, int> dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return make_pair(0, 0);
        }

        std::pair<int, int> res; 
        std::pair<int, int> res_left = dfs(root->left);
        std::pair<int, int> res_right = dfs(root->right);
        // 不抢(左子树和左子树抢不抢都行)
        res.first = std::max(res_left.first, res_left.second) +
                    std::max(res_right.first, res_right.second);
        // 抢(左子树和右子树都不能抢)
        res.second = res_left.first + res_right.first + root->val;
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="343"></div>

```c++

// 343. 整数拆分
// 动态规划 双指针（快慢指针） 数学

class Solution {
public:
    int integerBreak(int n) { 
        std::vector<int> dp(n + 1, 1); // 用1初始化，因为dp[2] = 1

        for (int fast = 3; fast <= n; fast++)
        {
            for (int slow = 1; slow <= fast - 1; slow++)
            {
                // 分割点分成三种情况
                // 1. dp[fast]表示当前不分割
                // 2. 分割点为slow,分成两段：
                //    slow * (fast - slow)
                // 3. slow * dp[fast - slow],这里表示fast - slow还要拆
                dp[fast] = biggest(dp[fast], 
                                   slow * (fast - slow), // 这句可以省略
                                   slow * dp[fast - slow]);
            }
        }

        return dp[n];
    }

private:
    int biggest(int a, int b, int c)
    {
        int temp = std::max(a, b);
        return std::max(temp, c);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int integerBreak(int n) {
        if (n <= 3)
        {
            return n - 1;
        }
        std::vector<int> dp(n + 1, 1); // 用1初始化，因为dp[2] = 1
        dp[1] = 1;
        dp[2] = 2;
        dp[3] = 3;
        for (int fast = 3; fast <= n; fast++)
        {
            for (int slow = 1; slow <= fast - 1; slow++)
            {
                dp[fast] = std::max(dp[fast], slow * dp[fast - slow]);
            }
        }

        return dp[n];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 344. 反转字符串
// 数组 双指针（相向指针）

class Solution {
public:
    void reverseString(vector<char>& s) {
        for (int index = 0; index < s.size() / 2; index++)
        {
            std::swap(s[index], s[s.size() - 1 - index]);
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 345. 反转字符串中的元音字母
// 双指针（相向指针） 字符串

class Solution {
public:
    string reverseVowels(string s) {
        std::string vowels("aeiouAEIOU");
        int left = 0;
        int right = s.size() - 1;

        while (left < right)
        {
            while (left < right && 
                   vowels.find(s[left]) == std::string::npos)
            {
                left++;
            }

            while (left < right && 
                   vowels.find(s[right]) == std::string::npos)
            {
                right--;
            }

            if (left < right)
            {
                std::swap(s[left++], s[right--]);
            }
        }
        return s;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 347. 前 K 个高频元素
// 排序 桶排序 哈希表 数组 计数排序

class Solution {
public:
    vector<int> topKFrequent(vector<int>& nums, int k) {
        std::unordered_map<int, int> m; // num=>count
        int max_freq = 0;
        for (auto num : nums)
        {
            m[num]++;
            max_freq = std::max(max_freq, m[num]); // 维护最大频率值
        }

        std::unordered_map<int, std::vector<int>> buckets; // count=>{n1, n2, n3}
        for (auto key : m)
        {
            buckets[key.second].push_back(key.first);
        }

        std::vector<int> res;
        for (int index = max_freq; index >= 1; index--)
        {
            if (res.size() == k)
            {
                return res;
            }

            if (buckets.find(index) != buckets.end())
            {
                res.insert(res.end(), buckets.find(index)->second.begin(), 
                                      buckets.find(index)->second.end());
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 349. 两个数组的交集
// 哈希表 数组

class Solution {
public:
    vector<int> intersection(vector<int>& nums1, vector<int>& nums2) {
        std::unordered_set<int> s(nums1.begin(), nums1.end());
        std::vector<int> res;

        for (auto num : nums2)
        {
            if (1 == s.count(num))
            {
                res.push_back(num);
                s.erase(num);
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 350. 两个数组的交集 II
// 哈希表 数组

class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        std::unordered_multiset<int> s(nums1.begin(), nums1.end());
        std::vector<int> res;

        for (auto num : nums2)
        {
            auto it = s.find(num); // 删重复的用迭代器
            if (s.end() != it)
            {
                res.push_back(num);
                s.erase(it);
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 355. 设计推特
// 系统设计

class Twitter {
private:
    // pull拉模型，每个用户从关注好友中获取消息
    // 每个人都有一个数据库
    std::unordered_map<int, std::vector<std::pair<int, int>>> tweets; 
    // userID->{time, tweetID}
    std::unordered_map<int, std::unordered_set<int>> friends; 
    // userID->followeeIDs
    long time_stamp; // 时间戳

public:
    /** Initialize your data structure here. */
    Twitter() {
        time_stamp = 0;
    }
    
    /** Compose a new tweet. */
    void postTweet(int userId, int tweetId) {
        Twitter::follow(userId, userId);
        time_stamp++;
        tweets[userId].push_back({time_stamp, tweetId});
    }
    
    /** Retrieve the 10 most recent tweet ids in the user's news feed. 
     * Each item in the news feed must be posted by users 
     * who the user followed or by the user herself. 
     * Tweets must be ordered from most recent to least recent. */
    vector<int> getNewsFeed(int userId) {
        std::set<std::pair<int, int>> news;

        for (auto f : friends[userId]) // f:followeeID
        {
            for (int index = tweets[f].size() - 1; index >= 0; index--)
            {
                if (news.size() < 10)
                {
                    news.insert(tweets[f][index]);
                }
                else if (tweets[f][index].first > news.begin()->first)
                {
                    news.insert(tweets[f][index]);
                    news.erase(news.begin());
                }
                else
                {
                    break;
                }
            }
        }

        std::vector<int> vRes;

        for (auto n : news)
        {
            vRes.push_back(n.second);
        }

        reverse(vRes.begin(), vRes.end()); // 按时间推送

        return vRes;
    }
    
    /** Follower follows a followee. If the operation is invalid, 
     * it should be a no-op. */
    void follow(int followerId, int followeeId) {
        friends[followerId].insert(followeeId);
    }
    
    /** Follower unfollows a followee. If the operation is invalid, 
     * it should be a no-op. */
    void unfollow(int followerId, int followeeId) {
        if (friends[followerId].find(followeeId) != 
            friends[followerId].end() && 
            followerId != followeeId) // 不能是自己
        {
            friends[followerId].erase(followeeId);
        }   
    }
};

/**
 * Your Twitter object will be instantiated and called as such:
 * Twitter* obj = new Twitter();
 * obj->postTweet(userId,tweetId);
 * vector<int> param_2 = obj->getNewsFeed(userId);
 * obj->follow(followerId,followeeId);
 * obj->unfollow(followerId,followeeId);
 */

```
<div STYLE="page-break-after: always;"></div>

```c++

// 365. 水壶问题
// 数学
// 广度优先 队

class Solution {
public:
    bool canMeasureWater1(int x, int y, int z) {
        // x, y最大公约数能否被z除断
        if (x + y < z)
        {
            return false;
        }

        if (z == x || z == y)
        {
            return true;
        }

        if (0 == x || 0 == y)
        {
            return false;
        }

        return 0 == (z % std::__gcd(x, y));
    }

    bool canMeasureWater2(int x, int y, int z) {
        if (z < 0 || z > x + y)
        {
            return false;
        }

        std::set<int> s;
        std::queue<int> q({0});

        while (q.size() > 0)
        {
            int n = q.front();

            if (n + x <= x + y && true == s.insert(n + x).second)
            {
                q.push(n + x);
            }

            if (n + y <= x + y && true == s.insert(n + y).second)
            {
                q.push(n + y);
            }

            if (n - x >= 0 && true == s.insert(n - x).second)
            {
                q.push(n - x);
            }

            if (n - y >= 0 && true == s.insert(n - y).second)
            {
                q.push(n - y);
            }

            if (s.end() != s.find(z))
            {
                return true;
            }

            q.pop();
        }

        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 366. 寻找二叉树的叶子节点
// 深度优先 后序遍历 二叉树 递归
// 给你一棵二叉树，请按以下要求的顺序收集它的全部节点：依次从左到右，每次收集并删除所有的叶子节点；重复如上过程直到整棵树为空

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<vector<int>> findLeaves(TreeNode* root) {
        dfs(root);
        return res;
    }

private:
    std::vector<std::vector<int>> res;
    // 反向求深度
    int dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return 0;
        }

        int left_depth = dfs(root->left);
        int right_depth = dfs(root->right);

        int cur_depth = std::max(left_depth, right_depth) + 1;

        if (cur_depth == res.size() + 1) // res少一层
        {
            res.push_back({});
        }

        res[cur_depth - 1].push_back(root->val);
        return cur_depth;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 376. 摆动序列
// 动态规划 贪心 双指针（跟随指针）

class Solution {
public:
    int wiggleMaxLength(vector<int>& nums) {
        if (nums.size() < 2)
        {
            return nums.size();
        }

        int res = 1;
        // 双指针（跟随指针）维护两个状态
        int cur_state = 0;
        int pre_state = 0;
        // 贪心
        for (int index = 1; index <= nums.size() - 1; index++)
        {
            if (nums[index] != nums[index - 1]) // 有坡
            {
                // 1表示上升，-1表示下降，1和-1可以取随意值，不要和pre一样
                cur_state = (nums[index] > nums[index - 1]) ? 1 : -1;
                
                if (cur_state != pre_state) // 有拐
                {
                    res++;
                }

                pre_state = cur_state; // 跟随
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="377"></div>

```c++

// 377. 组合总和 Ⅳ
// 动态规划 背包问题

class Solution {
public:
    int combinationSum4(vector<int>& nums, int target) {
        // 背包问题三模板
        // 1.种类问题：
        // dp[i] += dp[i-num]
        // 2.存在性：
        // dp[i] = dp[i] or/and dp[i-num]
        // 3.极值问题：
        // dp[i] = min(dp[i], dp[i-num]+1)或者
        // dp[i] = max(dp[i], dp[i-num]+1)

        // dp[cur_sum] = sum(dp[cur_sum - num])
        // dp表示总数，下标表示当前和
        std::vector<unsigned int> dp(target + 1, 0);
        dp[0] = 1; // sum为0的默认有一种方法

        for (int sum = 1; sum <= target; sum++)
        {
            for (auto num : nums)
            {
                if (sum >= num) // num可能组成sum
                {
                    dp[sum] += dp[sum - num];
                }
            }
        }
        return dp[target];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 378. 有序矩阵中第K小的元素
// 优先队列 归并 矩阵

class Solution {
public:
    int kthSmallest(vector<vector<int>>& matrix, int k) {
        std::priority_queue<int, std::vector<int>, less<int>> q;
        // 求最小值就用最小堆
        for (auto m : matrix)
        {
            for (auto n : m)
            {
                q.push(n);
                if (q.size() > k)
                {
                    q.pop();
                }
            }
        }
        return q.top();
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 384. 打乱数组
// 数学 随机数

class Solution {
public:
    std::vector<int> v;

    Solution(vector<int>& nums) {
        v = nums;
    }
    
    /** Resets the array to its original configuration and return it. */
    vector<int> reset() {
        return v;
    }   
    
    /** Returns a random shuffling of the array. */
    vector<int> shuffle() {
        std::vector<int> vRes = v;
        int len = v.size();
        for (int index = 0; index <= len - 1; index++)
        {
            int rand = std::rand() % (index + 1);
            std::swap(vRes[index], vRes[rand]);
        } 

        return vRes;  
    }
};

/**
 * Your Solution object will be instantiated and called as such:
 * Solution* obj = new Solution(nums);
 * vector<int> param_1 = obj->reset();
 * vector<int> param_2 = obj->shuffle();
 */

```
<div STYLE="page-break-after: always;"></div>

```c++

// 387. 字符串中的第一个唯一字符
// 哈希表 字符串

class Solution {
public:
    int firstUniqChar(string s) {
        std::unordered_map<char, int> m; // char => count

        for (auto c : s)
        {
            m[c]++;
        }

        for (auto c : s)
        {
            if (1 == m[c])
            {
                for (int index = 0; index <= (int)s.size() - 1; index++)
                {
                    if (c == s[index])
                    {
                        return index;
                    }
                }
            }
        }

        return -1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 389. 找不同
// 计数排序 bitmap 哈希表
// 给定两个字符串 s 和 t，它们只包含小写字母。字符串 t 由字符串 s 随机重排，然后在随机位置添加一个字母。请找出在 t 中被添加的字母。

class Solution {
public:
    char findTheDifference(string s, string t) {
        std::vector<int> count(26, 0);

        for (auto c : t)
        {
            count[c - 'a']++;
        }

        for (auto c : s)
        {
            count[c - 'a']--;
        }

        for (int index = 0 ; index <= 26; index++)
        {
            if (1 == count[index])
            {
                return 'a' + index;
            }
        }
        return 0;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 392. 判断子序列
// 字符串 双指针（快慢指针） 子串

class Solution {
public:
    bool isSubsequence(string s, string t) {
        if (0 == s.size())
        {
            return true;
        }

        if (0 == t.size())
        {
            return false;
        }

        for (int slow = 0, fast = 0; 
             fast <= t.size() - 1 && slow <= s.size() - 1; fast++)
        {
            if (t[fast] == s[slow])
            {
                slow++;
            }

            if (slow == s.size())
            {
                return true;
            }
        }
        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 394. 字符串解码
// 栈 字符串 流程控制

class Solution {
public:
    string decodeString(string s) {
        std::vector<int> v_count;
        std::vector<std::string> v_str;
        std::string s_buf = "";
        int count = 0;

        for (auto& c : s)
        {
            if (std::isdigit(c)) // 是数字
            {
                count = count * 10 + (c - '0');
            }
            else if ('[' == c) // 是左括号
            {
                // 处理之前的数字和字符
                v_count.push_back(count);
                v_str.push_back(s_buf); // 将缓存入栈
                // 清空缓存
                s_buf.clear();
                count = 0;
            }
            else if (std::isalpha(c)) // 是字符
            {
                s_buf += c; // 把字符加入缓存
            }
            else if (']' == c) // 是右括号
            {
                // 弹出栈里的一个元素来连接buf
                std::string s_top = v_str.back(); 
                v_str.pop_back();
                int cnt = v_count.back();
                v_count.pop_back();

                for (int i = 0; i < cnt; i++)
                {
                    s_top += s_buf; // 连接cnt次
                }

                s_buf = s_top; // 更新缓存，连了新字符
            }
        }

        return s_buf;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 402. 移掉K位数字
// 单调栈 字符串

class Solution {
public:
    string removeKdigits(string num, int k) {
        if (k == num.size())
        {
            return "0";
        }

        std::string res; // 单调栈，最后截取规定长度
        int remain = num.size() - k; // k在后面会被改，先保存

        // 单调栈
        for (char c : num)
        {
            while (k > 0 && res.size() && res.back() > c)
            {
                res.pop_back(); // pop
                k -= 1;
            }

            res += c; // push
        }

        // 去掉前缀0
        size_t pos = res.find_first_of("123456789");

        if (pos != std::string::npos )
        {
            return res.substr(pos, remain);;
        }
        else // "0"
        {
            return "0";
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 404. 左叶子之和
// 深度优先 递归 回溯 前序遍历

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int sumOfLeftLeaves(TreeNode* root) {
        if (nullptr == root)
        {
            return 0;
        }
        // 左叶子
        int val = 0;

        if (root->left &&  
            nullptr == root->left->left &&  
            nullptr == root->left->right)
        {
            val = root->left->val;
        }

        return val + sumOfLeftLeaves(root->left) + 
                     sumOfLeftLeaves(root->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 406. 根据身高重建队列
// 数组 排序 lambda

class Solution {
public:
    vector<vector<int>> reconstructQueue(vector<vector<int>>& people) {
        std::sort(people.begin(), people.end(),
            [](const std::vector<int> a, const std::vector<int> b)
            {
                // 按第一个元素从大到小排
                // 按第二个元素从小到大排
                return (a[0] > b[0]) || (a[0] == b[0] && a[1] < b[1]);
            }
        );

        std::list<vector<int>> lRes; // list更快，vector也行

        for (auto p : people)
        {
            auto pos = lRes.begin();
            std::advance(pos, p[1]); // pos向后移动p[1]个长度
            lRes.insert(pos, p);
        }

        return std::vector<vector<int>>(lRes.begin(), lRes.end());
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 409. 最长回文串
// 字符串 哈希表

class Solution {
public:
    int longestPalindrome(string s) {
        // 计算偶数数次字符个数
        std::unordered_map<char, int> m; // char=>count
        int res = 0;

        for (char c : s)
        {
            m[c]++;
        }  

        for (auto it = m.begin(); it != m.end(); it++)
        {
            if (0 == it->second % 2)
            {
                res += it->second;
            }
            else if ((1 == it->second % 2) && it->second > 1)
            {
                res += it->second - 1; // 比如"ccc"
            }
        }
        return res < s.size() ? res + 1 : res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="410"></div>

```c++

// 410. 分割数组的最大值
// 动态规划 区间DP

class Solution {
public:
    int splitArray(vector<int>& nums, int m) {
        std::vector<long> sums(nums.size()); // 前缀和
        std::vector<std::vector<long>> 
        dp(m, std::vector<long>(nums.size(), INT_MAX));

        sums[0] = nums[0];
        // 求前缀和
        for (int col = 1; col <= nums.size() - 1; col++)
        {
            sums[col] = sums[col - 1] + nums[col];
        }
        // 边界条件
        for (int col = 0; col <= nums.size() - 1; col++)
        {
            dp[0][col] = sums[col];
        }

        for (int row = 1; row <= m - 1; row++)
        {
            for (int col = row - 1; col <= nums.size() - 1; col++)
            {
                for (int k = 0; k < col; k++) // 分区间
                {
                    dp[row][col] = 
                    std::min(dp[row][col], std::max(dp[row - 1][k], sums[col] - sums[k]));
                }
            }
        }
        return dp[m - 1][nums.size() - 1];
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="413"></div>

```c++

// 413. 等差数列划分
// 动态规划 滚动数组 数学

class Solution {
public:
    int numberOfArithmeticSlices(vector<int>& A) {
        int res = 0;
        int count = 0;
        // 三个数开始算数列，所以从2开始
        for (int index = 2; index <= (int)A.size() - 1; index++)
        {
            if (A[index] - A[index - 1] == A[index - 1] - A[index - 2])
            {
                count++; // 只要出现连续的，那么到它为止肯定包含它前面的
                // array    count
                // 1 2 3      1  即1 2 3 
                // 1 2 3 4    2  即2 3 4 和 1 2 3 4
                // 1 2 3 4 5  3  即3 4 5 和 2 3 4 5 和 1 2 3 4 5
                res += count;
            }
            else // 一旦有断开，重新计算
            {
                count = 0;
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 415. 字符串相加
// 字符串 进位

class Solution {
public:
    string addStrings(string num1, string num2) {
        int index_1 = num1.size() - 1;
        int index_2 = num2.size() - 1;
        std::string res;
        int carry = 0;

        while (0 <= index_1 && 0 <= index_2)
        {
            int real = num1[index_1] - '0' + num2[index_2] - '0' + carry;
            carry = real / 10;
            res += real % 10 + '0';
            index_1--;
            index_2--;
        }

        while (0 <= index_1)
        {
            int real = num1[index_1] - '0' + carry;
            carry = real / 10;
            res += real % 10 + '0';
            index_1--;
        }

        while (0 <= index_2)
        {
            int real = num2[index_2] - '0' + carry;
            carry = real / 10;
            res += real % 10 + '0';
            index_2--;
        }

        if (0 != carry)
        {
            res += '1';
        }

        std::reverse(res.begin(), res.end());

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="416"></div>

```c++

// 416. 分割等和子集
// 动态规划

class Solution {
public:
    bool canPartition(vector<int>& nums) {
        int sum = std::accumulate(nums.begin(), nums.end(), 0);

        if (sum % 2 != 0) // 奇数肯定不行
        {
            return false;
        }
        // 题设为全正数，所以每个值肯定小于sum / 2，
        // 这里减枝，只开sum / 2空间
        // dp[sum]表示和为sum可不可以
        // 最后目的是dp[sum / 2]要可以
        std::vector<bool> dp(sum / 2 + 1, false);
        dp[0] = true;

        for (auto num : nums)
        {
            // 从后往前，减枝
            for (int sum_temp = sum / 2; sum_temp >= 0; sum_temp--)
            {
                // 那些和大于sum / 2的不考虑
                if (true == dp[sum_temp] && sum_temp + num <= sum / 2)
                {
                    dp[sum_temp + num] = true; // 表示可以组成sum_temp + num
                }
            }
        }
        return dp[sum / 2];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 417. 太平洋大西洋水流问题
// 深度优先 递归

class Solution {
public:
    vector<vector<int>> pacificAtlantic(vector<vector<int>>& matrix) {
        if (0 == matrix.size())
        {
            return {};
        }

        // 分别从太平洋和大西洋流到山上
        // 也就是从四边往中间走
        // 最后求交集
        int row_length = matrix.size(); // 行
        int col_length = matrix[0].size(); // 列

        std::vector<std::vector<bool>> 
        v_p(row_length, std::vector<bool>(col_length, false));
        std::vector<std::vector<bool>> 
        v_a(row_length, std::vector<bool>(col_length, false));

        std::vector<std::vector<int>> v_res;

        for (int row = 0; row <= row_length - 1; row++)
        {
            dfs(matrix, row, 0, 0, v_p); // 太平洋回流
            dfs(matrix, row, col_length - 1, 0, v_a); // 大西洋回流
        }

        for (int col = 0; col <= col_length - 1; col++)
        {
            dfs(matrix, 0, col, 0, v_p); // 太平洋回流
            dfs(matrix, row_length - 1,  col, 0, v_a); // 大西洋回流
        }
        // 交集
        for (int row = 0; row <= row_length - 1; row++)
        {
            for (int col = 0; col <= col_length - 1; col++)
            {
                if (v_p[row][col] && v_a[row][col])
                {
                    v_res.push_back({row, col});
                }
            }
        }

        return v_res;
    }

private:
    // 转换思路，从海水流到山上，反过来思考
    void dfs(std::vector<std::vector<int>>& matrix, int row, int col,
             int height, std::vector<std::vector<bool>>& v_arrive)
    {
        if (0 > row || row >= matrix.size() ||
            0 > col || col >= matrix[0].size() ||
            true == v_arrive[row][col] ||
            matrix[row][col] < height)
        {
            return;
        }

        v_arrive[row][col] = true; // 找比它高的

        dfs(matrix, row + 1, col, matrix[row][col], v_arrive);
        dfs(matrix, row - 1, col, matrix[row][col], v_arrive);
        dfs(matrix, row, col + 1, matrix[row][col], v_arrive);
        dfs(matrix, row, col - 1, matrix[row][col], v_arrive);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 429. N叉树的层序遍历
// 广度优先 队 树 深度优先 递归

/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> children;

    Node() {}

    Node(int _val) {
        val = _val;
    }

    Node(int _val, vector<Node*> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution1 {
public:
    vector<vector<int>> levelOrder(Node* root) {
        if (nullptr == root)
        {
            return {};
        }

        std::vector<std::vector<int>> v_res;
        std::queue<Node*> q;
        q.push(root);

        while (false == q.empty())
        {
            int len = q.size();
            v_res.push_back({});

            while (len--)
            {
                for (auto child : q.front()->children)
                {
                    if (child)
                    {
                        q.push(child);
                    }
                }

                v_res.back().push_back(q.front()->val);
                q.pop();
            }
        }
        return v_res;
    }
};

class Solution2 {
public:
    vector<vector<int>> levelOrder(Node* root) {
        std::vector<std::vector<int>> vv_res;
        dfs(root, vv_res, 0);
        return vv_res;
    }

private:
    void dfs(Node* root, std::vector<std::vector<int>>& vv_res, int depth)
    {
        if (nullptr == root)
        {
            return;
        }

        if (vv_res.size() == depth) // 增加一层
        {
            vv_res.push_back({});
        }

        vv_res[depth].push_back(root->val);

        for (auto child : root->children)
        {
            dfs(child, vv_res, depth + 1);
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 435. 无重叠区间
// 排序 lambda 贪心法 区间

class Solution {
public:
    int eraseOverlapIntervals(vector<vector<int>>& intervals) {
        // 按照起点排序：选择结尾最短的，后面才可能连接更多的区间
        // 如果两个区间有重叠，应该保留结尾小的 
        // 把问题转化为最多能保留多少个区间，使他们互不重复，
        // 则按照终点排序，每个区间的结尾很重要，
        // 结尾越小，则后面越有可能容纳更多的区间
        if (0 == intervals.size())
        {
            return 0;
        }

        std::sort(intervals.begin(), intervals.end(),
                  [&](const std::vector<int>& a, const std::vector<int>& b)
                  {
                      return a[1] < b[1]; // 按第二位排序
                  });
        
        int right = intervals[0][1];
        int res = 1; // 最多不重叠区间个数，初始情况为1

        for (auto& i : intervals)
        {
            if (i[0] < right) // 表示重叠了
            {
                continue;
            }
            else if (i[0] >= right) // 表示无重叠
            {
                right = i[1];
                res++; // 无重叠个数加一
            }
        }

        return intervals.size() - res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 437. 路径总和 III
// 深度优先 树 双递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int pathSum(TreeNode* root, int sum) {
        if (nullptr == root)
        {
            return 0;
        }
        return dfs(root, sum) + 
               pathSum(root->left, sum) + 
               pathSum(root->right, sum);
    }

private:
    int dfs(TreeNode* root, int sum)
    {
        if (nullptr == root)
        {
            return 0;
        }

        return (0 == sum - root->val ? 1 : 0) +
               dfs(root->left, sum - root->val) + 
               dfs(root->right, sum - root->val);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 442. 数组中重复的数据
// 数组 哈希表

class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        std::vector<int> res;
        // 1 ≤ a[i] ≤ n
        // 没有0.考虑原地哈希
        // [1, n]映射到[0, n - 1],因此index=>index - 1
        for (int index = 0; index < nums.size(); index++)
        {
            if (0 < nums[std::abs(nums[index]) - 1])
            {
                nums[std::abs(nums[index]) - 1] *= -1;
            }
            else if (0 > nums[std::abs(nums[index]) - 1])
            {
                // 说明已经存过一次了
                res.push_back(std::abs(nums[index]));
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 445. 两数相加 II
// 链表 数学（进位） 栈

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        std::stack<int> stack_l1;
        std::stack<int> stack_l2;
        ListNode* ps_l1 = l1;
        ListNode* ps_l2 = l2;

        while (ps_l1 || ps_l2)
        {
            if (ps_l1)
            {
                stack_l1.push(ps_l1->val);
                ps_l1 = ps_l1->next;
            }

            if (ps_l2)
            {
                stack_l2.push(ps_l2->val);
                ps_l2 = ps_l2->next;
            }
        }

        ListNode* ps_dummy = new ListNode(0);
        ListNode* ps_new = ps_dummy;
        int carry = 0;

        while (!stack_l1.empty() || !stack_l2.empty())
        {
            int num_l1 = (false == stack_l1.empty()) ? stack_l1.top() : 0;
            int num_l2 = (false == stack_l2.empty()) ? stack_l2.top() : 0;

            int real = num_l1 + num_l2 + carry;
            carry = real / 10;
            ListNode* ps_cur = new ListNode(real % 10);
            ps_cur->next = ps_dummy->next; // 头插法
            ps_dummy->next = ps_cur;

            if (false == stack_l1.empty())
            {
                stack_l1.pop();
            }

            if (false == stack_l2.empty())
            {
                stack_l2.pop();
            }
        }

        if (carry)
        {
            ListNode* ps_carry = new ListNode(carry);
            ps_carry->next = ps_dummy->next;
            ps_dummy->next = ps_carry;
        }

        return ps_dummy->next;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 448. 找到所有数组中消失的数字
// 哈希表 数组

class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
        std::vector<int> res;
        // 原地哈希
        // [1, n]映射到[0, n - 1],因此index=>index - 1
        for (int index = 0; index < nums.size(); index++)
        {
            // 可能有重复的数字已经改变过一次了
            nums[std::abs(nums[index]) - 1] = -abs(nums[std::abs(nums[index]) - 1]);
        }

        for (int index = 0; index < nums.size(); index++)
        {
            if (0 < nums[index])
            {
                res.push_back(index + 1);
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 450. 删除二叉搜索树中的节点
// 树 递归 后序遍历

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* deleteNode(TreeNode* root, int key) {
        if (nullptr == root)
        {
            return nullptr;
        }

        if (key < root->val)
        {
            root->left = deleteNode(root->left, key);
        }
        else if (key > root->val)
        {
            root->right = deleteNode(root->right, key);
        }
        else if (key == root->val) // 找到要删节点
        {
            if (nullptr == root->left) // 左子树为空
            {
                root = root->right;
            }
            else if (nullptr == root->right) // 右子树为空
            {
                root = root->left;
            }
            else if (root->left && root->right)
            {
                // 找右子树中最小值替换root
                auto right_min = root->right;
                while (right_min->left) // 往左边找
                {
                    right_min = right_min->left;
                }
                root->val = right_min->val;
                // 右子树最左边是最小值，肯定没有左孩子
                root->right = deleteNode(root->right, right_min->val);
            }
        }
        return root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 451. 根据字符出现频率排序
// 排序 计数排序 哈希表 桶排序

class Solution {
public:
    string frequencySort(string s) {
        // 计数排序
        std::unordered_map<char, int> m; // char=>count

        for (char& c : s)
        {
            m[c]++;
        }

        std::sort(s.begin(), s.end(), 
                  [&m](char& a, char& b)
                  {
                      return m[a] > m[b] || (m[a] == m[b] && a > b);
                  });

        return s;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    string frequencySort(string s) {
        std::unordered_map<char, int> m; // char=>count
        int max_freq = 0;
        for (auto& c : s)
        {
            m[c]++;
            max_freq = std::max(max_freq, m[c]);
        }

        std::unordered_map<int, std::vector<char>> buckets; 
        // count=>{c1, c2, c3}
        for (auto& key : m)
        {
            buckets[key.second].push_back(key.first);
        }

        std::string res;

        for (int freq = max_freq; freq >= 1; freq--)
        {
            if (buckets.find(freq) != buckets.end())
            {
                for (auto& c : buckets.find(freq)->second)
                {
                    res.insert(res.size(), freq, c);
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 452. 用最少数量的箭引爆气球
// 贪心法 排序 lambda

class Solution {
public:
    int findMinArrowShots(vector<vector<int>>& points) {
        if (0 == points.size())
        {
            return 0;
        }

        std::sort(points.begin(), points.end(),
                  [&](const std::vector<int>& a, const std::vector<int>& b)
                  {
                      return a[1] < b[1]; // 按第二位排序
                  });
        
        int right = points[0][1];
        int res = 1;

        for (auto& p : points)
        {
            if (p[0] > right) // 下一行第一位大于右边
            {
                right = p[1];
                res++; // 多加一只箭
            }
            else if (p[0] <= right)
            {
                continue;
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 454. 四数相加 II
// 哈希表 数组
// 给定四个包含整数的数组列表 A , B , C , D ,计算有多少个元组 (i, j, k, l) ，使得 A[i] + B[j] + C[k] + D[l] = 0。

class Solution {
public:
    int fourSumCount(vector<int>& A, vector<int>& B, vector<int>& C, vector<int>& D) {
        std::unordered_map<int, int> m; // sum of A and B => count
        int res = 0;

        for (int index_a = 0; index_a <= (int)A.size() - 1; index_a++)
        {
            for (int index_b = 0; index_b <= (int)B.size() - 1; index_b++)
            {
                m[A[index_a] + B[index_b]]++;
            }
        }

        for (int index_c = 0; index_c <= (int)C.size() - 1; index_c++)
        {
            for (int index_d = 0; index_d <= (int)D.size() - 1; index_d++)
            {
                if (m.find(0 - C[index_c] - D[index_d]) != m.end())
                {
                    res += m[0 - C[index_c] - D[index_d]];
                }
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 455. 分发饼干
// 贪心法 排序

class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        std::sort(g.begin(), g.end());
        std::sort(s.begin(), s.end());
        int child = 0;

        for (int cookie = 0; child < g.size() && cookie < s.size(); cookie++)
        {
            if (g[child] <= s[cookie])
            {
                child++;
            }
            else if (g[child] > s[cookie])
            {
                continue;
            }
        }
        return child;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 463. 岛屿的周长
// 数学 数组 矩阵

class Solution {
public:
    int islandPerimeter(vector<vector<int>>& grid) {
        int res = 0;
        // 量子纠缠
        // 由于岛屿内没有湖,所以只需要求出北面(或南面) + 西面(或东面)的长度再乘2即可
        for (int row = 0; row <= (int)grid.size() - 1; row++)
        {
            for (int col = 0; col <= (int)grid[0].size() - 1; col++)
            {
                if (grid[row][col])
                {
                    if (0 == row || 0 == grid[row - 1][col]) // 前一个不是
                    {
                        res += 2;
                    }

                    if (0 == col || 0 == grid[row][col - 1]) // 上一行不是
                    {
                        res += 2;
                    }
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int islandPerimeter(vector<vector<int>>& grid) {
        int res = 0;
        // 由于岛屿内没有湖,所以只需要求出北面(或南面) + 西面(或东面)的长度再乘2即可
        for (int row = 0; row <= (int)grid.size() - 1; row++)
        {
            for (int col = 0; col <= (int)grid[0].size() - 1; col++)
            {
                if (grid[row][col])
                {
                    res += 4;

                    if (row > 0 && 1 == grid[row - 1][col]) // 前一个也是
                    {
                        res -= 2;
                    }

                    if (col > 0 && 1 == grid[row][col - 1]) // 上一行也是
                    {
                        res -= 2;
                    }
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 470. 用 Rand7() 实现 Rand10()
// 数学 概率

// The rand7() API is already defined for you.
// int rand7();
// @return a random integer in the range 1 to 7

class Solution {
public:
    int rand10() {
        /*
        已知 rand_N() 可以等概率的生成[1, N]范围的随机数
        那么：
        (rand_X() - 1) × Y + rand_Y() ==> 可以等概率的生成[1, X * Y]范围的随机数
        即实现了 rand_XY()
        但是这样实现的N不是10的倍数啊！这该怎么处理？
        这里就涉及到了“拒绝采样”的知识了，
        也就是说，如果某个采样结果不在要求的范围内，则丢弃它。
        */
        while (true)
        {
            int num = (rand7() - 1) * 7 + rand7(); // 等概率生成[1,49]范围的随机数
            if (num <= 40)
            {
                return num % 10 + 1; // 拒绝采样，并返回[1,10]范围的随机数
            }
        }  
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 473. 火柴拼正方形
// 深度优先 回溯 递归 减枝

class Solution {
public:
    bool makesquare(vector<int>& nums) {
        if (0 == nums.size())
        {
            return false;
        }

        int sum = 0;

        for (auto num : nums)
        {
            sum += num;
        }

        if (sum % 4 != 0)
        {
            return false;
        }

        std::sort(nums.begin(), nums.end());
        std::vector<bool> vUse(nums.size(), false);

        return Solution::dfs(nums, sum / 4, vUse, 0, 0, 0);
    }

private:
    // @param side_id 边长个数，只要找到3个就可以了，第四个肯定找到了
    // @param vUse 是否用过，做去重时用，一样的地方就不再dfs了
    bool dfs(const std::vector<int> nums, const int target, std::vector<bool>& vUse,
             int index, int sum_temp, int side_id)
    {
        if (4 == side_id)
        {
            return true; // 最外层出口，递归结束
        }

        if (sum_temp > target) // 这个值不行
        {
            return false;
        }

        if (sum_temp == target) // 找到一个边，找下一个
        {   
            // 从index = 0开始找，要是用过的值已经被标记了
            return dfs(nums, target, vUse, 0, 0, side_id + 1);
        }

        for (int i = index; i <= nums.size() - 1; i++)
        {
            if (true == vUse[i])
            {
                continue;
            }
            // 去重模板
            if (i > 0 && nums[i] == nums[i - 1] && false == vUse[i - 1])
            {
                continue;
            }

            vUse[i] = true;
            // 只有在正确时才返回
            if (dfs(nums, target, vUse, i + 1, sum_temp + nums[i], side_id))
            {
                return true;
            }

            vUse[i] = false;
        }

        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="485"></div>

```c++

// 485. 最大连续1的个数
// 数组 动态规划

class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int max_len = 0;
        int cur_len = 0;

        for (int index = 0; index <= nums.size() - 1; index++)
        {
            cur_len = (1 == nums[index]) ? cur_len + 1 : 0;
            max_len = std::max(max_len, cur_len);
        }

        return max_len;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 491. 递增子序列
// 深度优先 递归 回溯 集合

class Solution {
public:
    vector<vector<int>> findSubsequences(vector<int>& nums) {
        if (0 == nums.size())
        {
            return {};
        }

        std::set<std::vector<int>> set_res;
        std::vector<int> v_buf;
        dfs(nums, set_res, v_buf, 0);
        return std::vector<std::vector<int>> (set_res.begin(), set_res.end());
    }

private:
    void dfs(std::vector<int>& nums, std::set<std::vector<int>>& set_res, std::vector<int>& v_buf, int index)
    {
        if (v_buf.size() > 1)
        {
            set_res.insert(v_buf); // 自动去重
        }

        for (int i = index; i <= nums.size() - 1; i++)
        {
            if (v_buf.size() >= 1 && v_buf.back() > nums[i]) // 跳过比当前元素小的
            {
                continue;
            }

            v_buf.push_back(nums[i]);
            dfs(nums, set_res, v_buf, i + 1);
            v_buf.pop_back();
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 493. 翻转对
// 归并排序 数组 分治

class Solution {
public:
    int reversePairs(vector<int>& nums) {
        v = nums;
        mergeSort(nums, 0, nums.size() - 1);
        return ans;
    }

private:
    int ans;
    std::vector<int> v; // 归并数组
    void mergeSort(vector<int>& nums, int left, int right)
    {
        if (left >= right)
        {
            return;
        }

        int mid = left + (right - left) / 2;

        mergeSort(nums, left, mid);
        mergeSort(nums, mid + 1, right);
        // 统计答案
        for (int left_index = left, right_index = mid + 1; 
             right_index <= right; right_index++)
        {
            for (; left_index <= mid && 
                   nums[left_index] <= 2 * (long)nums[right_index];
                   left_index++
            ) {}
            ans += mid - left_index + 1;
        }

        // 归并
        int new_index = left;

        for (int left_index = left, right_index = mid + 1;
             left_index <= mid || right_index <= right; )
        {
            if (right_index > right || left_index <= mid &&
                nums[left_index] <= nums[right_index])
            {
                v[new_index++] = nums[left_index++];
            }
            else
            {
                v[new_index++] = nums[right_index++];
            }   
        }

        for (int index = left; index <= right; index++)
        {
            nums[index] = v[index];
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 494. 目标和
// 深度优先 回溯 递归

class Solution {
public:
    int findTargetSumWays(vector<int>& nums, int S) {
        int sum = std::accumulate(nums.begin(), nums.end(), 0);

        if (S > std::abs(sum))
        {
            return 0;
        }

        int res = 0;
        dfs(nums, 0, S, res);
        return res;
    }

private:
    void dfs(std::vector<int>& nums, int index, int S, int& res)
    {
        if (index == nums.size())
        {
            if (0 == S)
            {
                res++;
            }
            return;
        }

        dfs(nums, index + 1, S - nums[index], res); // 减法
        dfs(nums, index + 1, S + nums[index], res); // 加法
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="501"></div>

```c++

// 501. 二叉搜索树中的众数
// 深度优先 递归 中序遍历 动态规划 滚动数组

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> findMode(TreeNode* root) {
        std::vector<int> arr;
        std::vector<int> res;

        dfs(root, arr);

        if (0 == arr.size())
        {
            return {};
        }
        
        res.push_back(arr[0]);

        int max = 1;
        int cnt = 1;

        for (int index = 1; index <= arr.size() - 1; index++)
        {
            // 动态规划 滚动数组
            cnt = (arr[index - 1] == arr[index]) ? cnt + 1 : 1;
            // 更新max
            if (cnt == max)
            {
                res.push_back(arr[index]);
            }
            else if (cnt > max)
            {
                res.clear();
                res.push_back(arr[index]);
                max = cnt;
            }
        }

        return res;
    }

private:
    void dfs(TreeNode* root, std::vector<int>& arr)
    {
        if (nullptr == root)
        {
            return;
        }
        // 中序遍历
        dfs(root->left, arr);

        arr.push_back(root->val);

        dfs(root->right, arr);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 503. 下一个更大元素 II
// 单调栈 数组

class Solution {
public:
    vector<int> nextGreaterElements(vector<int>& nums) {
        if (0 == nums.size())
        {
            return {};
        }
        
        std::vector<int> res(nums.size(), -1);
        std::stack<int> s;

        // 扩张数组，保证最后一个能搜到他前面的数就行
        for (int index = 0; index <= 2 * nums.size() - 2; index++)
        {
            // 当前元素大于栈顶元素，更新栈
            while (false == s.empty() && 
                   nums[index % (nums.size())] > nums[s.top()])
            {
                res[s.top()] = nums[index % (nums.size())];
                s.pop();
            }
            s.push(index % (nums.size()));
        }
        return res;
    }
}; 

```
<div STYLE="page-break-after: always;"></div>

```c++

// 508. 出现次数最多的子树元素和
// 深度优先 后序遍历 二叉树 递归 哈希表
// 给你一个二叉树的根结点，请你找出出现次数最多的子树元素和。一个结点的「子树元素和」定义为以该结点为根的二叉树上所有结点的元素之和（包括结点本身）。你需要返回出现次数最多的子树元素和。如果有多个元素出现的次数相同，返回所有出现次数最多的子树元素和（不限顺序）。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> findFrequentTreeSum(TreeNode* root) {
        std::vector<int> res;
        int count_max = 0;
        dfs(root);

        for (auto sum : m)
        {
            if (sum.second > count_max)
            {
                count_max = sum.second;
                res.clear();
                res.push_back(sum.first);
            }
            else if (sum.second == count_max)
            {
                res.push_back(sum.first);
            }
        }

        return res;
    }

private:
    std::unordered_map<int, int> m; // sum => count

    int dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return 0;
        }

        int left_sum = dfs(root->left);
        int right_sum = dfs(root->right);

        int sum = root->val + left_sum + right_sum;

        m[sum] = m.find(sum) != m.end() ? m[sum] + 1 : 1;

        return sum;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="509"></div>

```c++

// 509. 斐波那契数
// 迭代 动态规划

class Solution {
public:
    int fib(int N) {
        if (N <= 1)
        {
            return N;
        }

        if (2 == N)
        {
            return 1;
        }

        int res = 0;
        int pre1 = 1;
        int pre2 = 1;

        for (int n = 3; n <= N; n++)
        {
            res = pre1 + pre2;
            pre2 = pre1;
            pre1 = res;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 510. 二叉搜索树中的中序后继 II
// 深度优先 中序遍历 递归
// 给定一棵二叉搜索树和其中的一个节点 node ，找到该节点在树中的中序后继。如果节点没有中序后继，请返回 null 。一个结点 node 的中序后继是键值比 node.val大所有的结点中键值最小的那个。

/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;
    Node* parent;
};
*/

class Solution {
public:
    Node* inorderSuccessor(Node* node) {
        Node* p = node;

        while (p->parent) // 找到根结点
        {
            p = p->parent;
        }
        tar = node;
        res = nullptr;
        dfs(p);
        return res;
    }

private:
    Node* res;
    Node* pre;
    Node* tar;

    void dfs(Node* root)
    {
        if (nullptr == root)
        {
            return;
        }

        dfs(root->left);
        if (pre == tar)
        {
            res = root;
        }  
        pre = root; 
        dfs(root->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;
    Node* parent;
};
*/

class Solution {
public:
    Node* inorderSuccessor(Node* node) {
        if (node->right) // 右孩子存在就找右子树最左边
        {
            node = node->right;
            while (node->left)
            {
                node = node->left;
            }
            return node;
        }
        else if (node->parent && node->parent->left == node) // 左孩子
        {
            return node->parent;
        }
        else // 右孩子
        {
            while (node->parent && node->parent->right == node)
            {
                node = node->parent; // 直到左孩子
            }
            return node->parent; // 可能为空
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 513. 找树左下角的值
// 广度优先 队 二叉树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int findBottomLeftValue(TreeNode* root) {
        if (nullptr == root)
        {
            return 0;
        }

        int res = root->val;
        queue<TreeNode*> que;
        que.push(root);

        while (!que.empty())
        {
            int len = que.size();

            while (len--)
            {
                res = que.front()->val;

                if (que.front()->left)
                {
                    que.push(que.front()->left);
                }

                if (que.front()->right)
                {
                    que.push(que.front()->right);
                }

                que.pop();
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="518"></div>

```c++

// 518. 零钱兑换 II
// 动态规划 背包 双指针（快慢指针）滚动数组

class Solution {
public:
    int change(int amount, vector<int>& coins) {
        // 完全背包
        // dp[i]表示i个元素的方案数

        std::vector<int> dp(amount + 1, 0); // 滚动数组
        dp[0] = 1; // 如果i - slow = 0，表示刚好符合
        
        for (auto slow : coins)
        {
            for (int fast = slow; fast <= amount; fast++)
            {
                // 上一行（即本身）（不选的情况）加上选的情况
                dp[fast]  = dp[fast] + dp[fast - slow];
            }
        }
        return dp[amount];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 524. 通过删除字母匹配到字典里最长单词
// 双指针（快慢指针） 字符串 子串

class Solution {
public:
    string findLongestWord(string s, vector<string>& d) {
        if (0 == s.size())
        {
            return "";
        }
        
        std::string res;

        for (string& dic : d)
        {
            for (int slow = 0, fast = 0; 
                 slow <= dic.size() - 1 && fast <= s.size() - 1; fast++)
            {
                if (s[fast] == dic[slow])
                {
                    slow++;
                }

                if (slow == dic.size())
                {
                    if (dic.size() > res.size() || 
                        (dic.size() == res.size() && res > dic))
                    {
                        res = dic;
                    }
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 525. 连续数组
// 哈希表 前缀和 数组
// 给定一个二进制数组, 找到含有相同数量的 0 和 1 的最长连续子数组（的长度）。
// 思路：把0看成-1，即为找和为0的最长数组

class Solution {
public:
    int findMaxLength(vector<int>& nums) {
        int pre_sum = 0;
        int res = 0;
        std::unordered_map<int, int> m; // pre sum => index
        m[0] = -1; // 前缀后为0时下标为-1
        
        for (int index = 0; index <= (int)nums.size() - 1; index++)
        {
            // 同步更新前缀和
            pre_sum = (1 == nums[index]) ? pre_sum + 1 : pre_sum - 1;
            // 哈希表查找，找前缀和相同的
            if (m.find(pre_sum) != m.end())
            {
                res = std::max(res, index - m[pre_sum]);
                continue; // 保证pre_sum为最前，因为重新插入会更新下标
            }
            // 哈希表插入
            m[pre_sum] = index;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 528. 按权重随机选择
// 数学 概率空间

class Solution {
public:
    std::vector<int> v;

    Solution(vector<int>& w) {
        v = w;
        for (int index = 1; index <= v.size() - 1; index++)
        {
            v[index] += v[index - 1];
        }
    }
    
    int pickIndex() {
        int key = std::rand() % (v.back()) + 1;
        return std::lower_bound(v.begin(), v.end(), key) - v.begin();
    }
};

/**
 * Your Solution object will be instantiated and called as such:
 * Solution* obj = new Solution(w);
 * int param_1 = obj->pickIndex();
 */

```
<div STYLE="page-break-after: always;"></div>

```c++

// 530. 二叉搜索树的最小绝对差
// 深度优先 递归 中序遍历

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int getMinimumDifference(TreeNode* root) {
        std::vector<int> arr;
        dfs(root, arr);
        int min = arr[1] - arr[0];

        for (int index = 2; index <= arr.size() - 1; index++)
        {
            min = std::min(arr[index] - arr[index - 1], min);
        }

        return min;
    }

private:
    void dfs(TreeNode* root, std::vector<int>& arr)
    {
        if (nullptr == root)
        {
            return;
        }
        // 中序遍历
        dfs(root->left, arr);

        arr.push_back(root->val);

        dfs(root->right, arr);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 538. 把二叉搜索树转换为累加树
// 深度优先 树 中序遍历 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* convertBST(TreeNode* root) {
        dfs(root);
        return root;
    }

private:
    int sum; // 保存累计和

    void dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return;
        }
        // 中序遍历
        dfs(root->right);

        sum += root->val;
        root->val = sum;

        dfs(root->left);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 540. 有序数组中的单一元素
// 双指针（相向指针） 二分法 数组

class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        // 左闭右开区间，只判断偶数下标项
        // 因为原数组是奇数个元素，所以末尾元素下标为偶数
        int left = 0;
        int right = nums.size() - 1;

        while (left < right)
        {
            int mid = left + (right - left) / 2;

            if (mid % 2 == 1)
            {
                mid--; // mid若为奇数，往左边闭区间靠
            }

            if (nums[mid] < nums[mid + 1]) // 在左边
            {
                // 不排序数组改成nums[mid] != nums[mid + 1]
                // 右开，mid已经不可能，right找不可能的值
                right = mid; // 因为num[mid - 1] == nums[mid]
            }
            else if (nums[mid] == nums[mid + 1]) // 在右边
            {
                left = mid + 2; // mid已经不可能，所以+1，left找可能的值
            }
        }
        return nums[left]; // 返回左闭区间
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        // 双闭区间
        int left = 0;
        int right = nums.size() - 1;

        while (left <= right)
        {
            int mid = left + (right - left) / 2;

            if (mid % 2 == 1)
            {
                mid--;
            }

            if (mid == nums.size() - 1)
            {
                return nums[mid];
            }
            else if (nums[mid] == nums[mid + 1]) // 在右边
            {
                left = mid + 2;
            }
            else if (nums[mid] < nums[mid + 1]) // 在左边
            {
                right = mid - 2; // 不排序数组改成nums[mid] != nums[mid + 1]
            }
        }
        // 最后肯定是mid、left、right指向同一个不重复的值
        // 此时nums[mid] < nums[mid + 1],所以right会前移
        return nums[left];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 542. 01 矩阵
// 广度优先 队

class Solution {
public:
    vector<vector<int>> updateMatrix(vector<vector<int>>& matrix) {
        std::vector<std::pair<int, int>> v_dir = {{0, -1}, {0, 1}, {-1, 0}, {1, 0}};
        std::vector<std::vector<int>> v_res(matrix.size(), std::vector<int>(matrix[0].size(), INT_MAX)); // 先置为无穷大
        std::queue<std::pair<int, int>> q;

        for (int row = 0; row <= matrix.size() - 1; row++)
        {
            for (int col = 0; col <= matrix[0].size() - 1; col++)
            {
                if (0 == matrix[row][col])
                {
                    v_res[row][col] = 0;
                    q.push({row, col});
                }
            }
        }

        while (false == q.empty())
        {
            auto top_value = q.front();
            q.pop();

            for (int index = 0; index < 4; index++)
            {
                // 通过数组上下左右遍历
                int row = top_value.first + v_dir[index].first;
                int col = top_value.second + v_dir[index].second;

                if (0 <= row && row <= matrix.size() - 1 && 
                    0 <= col && col <= matrix[0].size() - 1 &&
                    v_res[row][col] > 
                    v_res[top_value.first][top_value.second] + 1)
                {
                    v_res[row][col] = \
                    v_res[top_value.first][top_value.second] + 1;
                    q.push({row, col});
                }
            }
        }

        return v_res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 543. 二叉树的直径
// 深度优先 树 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int max = 0;
    int diameterOfBinaryTree(TreeNode* root) {
        dfs(root);
        return max;
    }

private:
    int dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return 0;
        }
        // 求高度模板
        int left_depth = dfs(root->left);
        int right_depth = dfs(root->right);  

        max = std::max(max, (left_depth + right_depth));
        return std::max(left_depth, right_depth) + 1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 547. 朋友圈
// 邻接矩阵 深度优先 递归 连通分量 图

class Solution {
public:
    int findCircleNum(vector<vector<int>>& M) {
        std::vector<bool> visited(M.size(), false);
        int res = 0;

        for (int in_index = 0; in_index <= M.size() - 1; in_index++)
        {
            if (false == visited[in_index]) // 入度节点没有被访问
            {
                dfs(M, in_index, visited);
                res++;
            }
        }

        return res;
    }

private:
    // 求连通分量
    void dfs(std::vector<std::vector<int>> adjmatrix, int in_index,
             std::vector<bool>& visited)
    {
        if (true == visited[in_index])
        {
            return;
        }

        visited[in_index] = true;
        // 对每一个出度节点
        for (int out_index = 0; out_index <= adjmatrix.size() - 1; out_index++)
        {
            if (1 == adjmatrix[in_index][out_index] && 
                false == visited[out_index])
            {
                dfs(adjmatrix, out_index, visited);
            }
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 549. 二叉树中最长的连续序列
// 深度优先 后序遍历 递归 二叉树
// 给定一个二叉树，你需要找出二叉树中最长的连续序列路径的长度。请注意，该路径可以是递增的或者是递减。例如，[1,2,3,4] 和 [4,3,2,1] 都被认为是合法的，而路径 [1,2,4,3] 则不合法。另一方面，路径可以是 子-父-子 顺序，并不一定是 父-子 顺序

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int longestConsecutive(TreeNode* root) {
        return dfs(root).max_len;
    }

    class CRes
    {
    public:
        int max_len;
        int inc_len;
        int dec_len;

        CRes(int max_len, int inc_len, int dec_len)
        : max_len(max_len), inc_len(inc_len), dec_len(dec_len)
        {}
    };

    CRes dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return CRes(0, 0, 0);
        }

        CRes res_left = dfs(root->left);
        CRes res_right = dfs(root->right);

        int cur_inc_len_left = (root->left && root->left->val + 1 == root->val) ?
                               res_left.inc_len : 0;
        int cur_inc_len_right = (root->right && root->right->val - 1 == root->val) ?
                                res_right.dec_len : 0;
        int cur_dec_len_left = (root->left && root->left->val - 1 == root->val) ?
                               res_left.dec_len : 0;
        int cur_dec_len_right = (root->right && root->right->val + 1 == root->val) ?
                                res_right.inc_len : 0;
        int cur_inc_len = std::max(cur_inc_len_left, cur_dec_len_right) + 1;
        int cur_dec_len = std::max(cur_dec_len_left, cur_inc_len_right) + 1;
        int cur_max_len = std::max(res_left.max_len, res_right.max_len);
        cur_max_len = std::max(cur_max_len, cur_inc_len_left + cur_inc_len_right + 1);
        cur_max_len = std::max(cur_max_len, cur_dec_len_left + cur_dec_len_right + 1);

        return CRes(cur_max_len, cur_inc_len, cur_dec_len);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 554. 砖墙
// 哈希表 矩阵 前缀和
// 你的面前有一堵矩形的、由多行砖块组成的砖墙。 这些砖块高度相同但是宽度不同。你现在要画一条自顶向下的、穿过最少砖块的垂线。砖墙由行的列表表示。 每一行都是一个代表从左至右每块砖的宽度的整数列表。如果你画的线只是从砖块的边缘经过，就不算穿过这块砖。你需要找出怎样画才能使这条线穿过的砖块数量最少，并且返回穿过的砖块数量。你不能沿着墙的两个垂直边缘之一画线，这样显然是没有穿过一块砖的。

class Solution {
public:
    int leastBricks(vector<vector<int>>& wall) {
        std::unordered_map<int, int> m; // length => count
        int res = wall.size();

        for (int row = 0; row <= (int)wall.size() - 1; row++)
        {
            int pre_sum = 0; // 每一行求宽度的前缀和
            for (int col = 0; col <= (int)wall[row].size() - 2; col++)
            {
                pre_sum += wall[row][col]; // 更新前缀和
                m[pre_sum]++; // 插入哈希表
                res = std::min(res, (int)wall.size() - m[pre_sum]);
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 557. 反转字符串中的单词 III
// 字符串 双指针（相向指针）

class Solution {
public:
    string reverseWords(string s) {
        for (int index = 0, left = 0; index <= s.size(); index++)
        {
            if (' ' == s[index] || index == s.size())
            {
                for (int right = index - 1; left < right; left++, right--)
                {
                    std::swap(s[left], s[right]);
                }
                left = index + 1;
            }
        }

        return s;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 559. N叉树的最大深度
// 广度优先 树 队 

/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> children;

    Node() {}

    Node(int _val) {
        val = _val;
    }

    Node(int _val, vector<Node*> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution {
public:
    int maxDepth(Node* root) {
        if (nullptr == root)
        {
            return 0;
        }

        int depth = 0;
        std::queue<Node*> q;
        q.push(root);

        while (false == q.empty())
        {
            int len = q.size();

            while (len--)
            {
                auto cur = q.front();
                q.pop();

                for (auto child : cur->children)
                {
                    if (child)
                    {
                        q.push(child);
                    }
                }
            }
            depth++;
        }
        return depth;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 560. 和为K的子数组
// 前缀和 数组 哈希表

class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        std::unordered_map<int, int> m; // sum[i]=>count
        m[0] = 1; // 和为0的有一种情况[]

        int sum = 0; // 动态维护前缀和
        int res = 0;
        // sum[i] - sum[i - 1] = nums[i]
        for (auto num : nums)
        {
            sum += num; // 动态维护前缀和
            // 找有没有和为sum - k这样的前缀
            if (1 == m.count(sum - k)) 
            {
                res += m[sum - k];
            }

            m[sum]++;
        } 
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="562"></div>

```c++

// 562. 矩阵中最长的连续1线段
// 深度优先 方向（方位）数组 递归 矩阵 动态规划 滚动数组

class Solution {
public:
    int longestLine(vector<vector<int>>& M) {
        if (0 == M.size() || 0 == M[0].size())
        {
            return 0;
        }

        int max_len = 0;

        for (int row = 0; row <= M.size() - 1; row++)
        {
            for (int col = 0; col <= M[0].size() - 1; col++)
            {
                if (1 == M[row][col])
                {
                    for (int index = 0; index <= 3; index++)
                    {
                        int len = 0;
                        len = dfs(M, row, col, index);
                        max_len = std::max(max_len, len);
                    }
                }
            }
        }
        return max_len;
    }

private:
    // 方向数组，四连通，右，右下，下，左下
    int dx[4] = {1, 1, 0, -1};
    int dy[4] = {0, 1, 1, 1};

    int dfs(vector<vector<int>>& M, int row, int col, int index)
    {
        if (row < 0 || row >= M.size() ||  
            col < 0 || col >= M[0].size() ||  
            0 == M[row][col])
        {
            return 0;
        }

        int len = 1;
        len += dfs(M, row + dx[index], col + dy[index], index);
        return len;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int longestLine(vector<vector<int>>& M) {
        if (0 == M.size() || 0 == M[0].size())
        {
            return 0;
        }
        
        int res = 0;
        std::vector<std::vector<std::vector<int>>> 
        dp(M.size() + 1, std::vector<std::vector<int>>
          (M[0].size() + 2, std::vector<int>(4, 0)));

        for (int row = 1; row <= M.size(); row++ )
        {
            for (int col = 1; col <= M[0].size(); col++)
            {
                if (1 == M[row - 1][col - 1])
                {
                    dp[row][col][0] = dp[row - 1][col][0] + 1;
                    dp[row][col][1] = dp[row][col - 1][1] + 1;
                    dp[row][col][2] = dp[row - 1][col + 1][2] + 1;
                    dp[row][col][3] = dp[row - 1][col - 1][3] + 1;
                    res = std::max(res, dp[row][col][0]);
                    res = std::max(res, dp[row][col][1]);
                    res = std::max(res, dp[row][col][2]);
                    res = std::max(res, dp[row][col][3]);
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int longestLine(vector<vector<int>>& M) {
        if (0 == M.size() || 0 == M[0].size())
        {
            return 0;
        }
        
        int res = 0;
        // 滚动数组优化
        std::vector<std::vector<std::vector<int>>> 
        dp(2, std::vector<std::vector<int>>
          (M[0].size() + 2, std::vector<int>(4, 0)));

        for (int row = 1; row <= M.size(); row++ )
        {
            for (int col = 1; col <= M[0].size(); col++)
            {
                if (1 == M[row - 1][col - 1])
                {
                    dp[row % 2][col][0] = dp[(row + 1) % 2][col][0] + 1;
                    dp[0][col][1] = dp[0][col - 1][1] + 1;
                    dp[row % 2][col][2] = dp[(row + 1) % 2][col + 1][2] + 1;
                    dp[row % 2][col][3] = dp[(row + 1) % 2][col - 1][3] + 1;
                    res = std::max(res, dp[row % 2][col][0]);
                    res = std::max(res, dp[0][col][1]);
                    res = std::max(res, dp[row % 2][col][2]);
                    res = std::max(res, dp[row % 2][col][3]);
                }
                else if (0 == M[row - 1][col - 1])
                {
                    dp[row % 2][col][0] = 0;
                    dp[0][col][1] = 0;
                    dp[row % 2][col][2] = 0;
                    dp[row % 2][col][3] = 0;
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int longestLine(vector<vector<int>>& M) {
        if (0 == M.size() || 0 == M[0].size())
        {
            return 0;
        }

        int res = 0;
        std::vector<std::vector<int>> dp1(2, std::vector<int>(M[0].size() + 2, 0));
        std::vector<std::vector<int>> dp2(1, std::vector<int>(M[0].size() + 2, 0));
        std::vector<std::vector<int>> dp3(2, std::vector<int>(M[0].size() + 2, 0));
        std::vector<std::vector<int>> dp4(2, std::vector<int>(M[0].size() + 2, 0));

        for (int row = 1; row <= M.size(); row++ )
        {
            for (int col = 1; col <= M[0].size(); col++)
            {
                if (1 == M[row - 1][col - 1])
                {
                    dp1[row % 2][col] = dp1[(row + 1) % 2][col] + 1; // 下
                    dp2[0][col] = dp2[0][col - 1] + 1; // 右
                    dp3[row % 2][col] = dp3[(row + 1) % 2][col + 1] + 1; // 左下
                    dp4[row % 2][col] = dp4[(row + 1) % 2][col - 1] + 1; // 右下
                    res = std::max(res, dp1[row % 2][col]);
                    res = std::max(res, dp2[0][col]);
                    res = std::max(res, dp3[row % 2][col]);
                    res = std::max(res, dp4[row % 2][col]);
                }
                else if (0 == M[row - 1][col - 1])
                {
                    // 别忘了清零
                    dp1[row % 2][col] = 0;
                    dp2[0][col] = 0;
                    dp3[row % 2][col] = 0;
                    dp4[row % 2][col] = 0;
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 563. 二叉树的坡度
// 深度优先 递归 树 后序遍历

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int findTilt(TreeNode* root) {
        dfs(root);
        return sum_tilt;
    }

private:
    int sum_tilt;

    int dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return 0;
        }

        int left_tilt = dfs(root->left);
        int right_tilt = dfs(root->right);

        sum_tilt += std::abs(left_tilt - right_tilt);

        return root->val + left_tilt + right_tilt;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 565. 数组嵌套
// 递归 深度优先 环

class Solution {
public:
    int arrayNesting(vector<int>& nums) {
        std::vector<bool> visited(nums.size(), false);
        int res = 0;
        for (int index = 0; index <= nums.size() - 1; index++) 
        {
            if (false == visited[index]) 
            {
                res = std::max(res, dfs(nums, index, visited));
            }
        }
        return res;
    }

private:
    int dfs(std::vector<int>& nums, int index, std::vector<bool>& visited) 
    {
        if (index == nums.size() || true == visited[index]) 
        {
            return 0;
        }

        visited[index] = true;
        return dfs(nums, nums[index], visited) + 1;
    }
};


```
<div STYLE="page-break-after: always;"></div>

```c++

// 566. 重塑矩阵
// 数组 矩阵

class Solution {
public:
    vector<vector<int>> matrixReshape(vector<vector<int>>& nums, int r, int c) {
        if (nums.size() * nums[0].size() != r * c)  
        {
            return nums;
        }

        std::vector<std::vector<int>> res(r, std::vector<int>(c));

        for (int index = 0; index <= nums.size() * nums[0].size() - 1; index++)
        {
            res[index / c][index % c] = 
            nums[index / nums[0].size()][index % nums[0].size()];
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 572. 另一个树的子树
// 深度优先 双递归 树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool isSubtree(TreeNode* s, TreeNode* t) {
        if (nullptr == s)
        {
            return false;
        }

        return dfs(s, t) ||
               isSubtree(s->left, t) ||
               isSubtree(s->right, t);
    }

private:
    bool dfs(TreeNode* s, TreeNode* t)
    {
        if (nullptr == s && nullptr == t)
        {
            return true;
        }

        if (nullptr == s || nullptr == t || s->val != t->val)
        {
            return false;
        }

        return dfs(s->left, t->left) && dfs(s->right, t->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="583"></div>

```c++

// 575. 分糖果
// 哈希表 集合

class Solution {
public:
    int distributeCandies(vector<int>& candies) {
        std::unordered_set<int> m;

        for (int index = 0; index <= (int)candies.size() - 1; index++)
        {
            m.insert(candies[index]);
        }

        return std::min(m.size(), candies.size() / 2);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 576. 出界的路径数
// 动态规划 

给定一个 m × n 的网格和一个球。球的起始坐标为 (i,j) ，你可以将球移到相邻的单元格内，或者往上、下、左、右四个方向上移动使球穿过网格边界。但是，你最多可以移动 N 次。找出可以将球移出边界的路径数量。答案可能非常大，返回 结果 mod 109 + 7 的值。

class Solution {
public:
    int findPaths(int m, int n, int N, int i, int j) {
        constexpr int MOD = 1e9 + 7;
        std::vector<std::vector<std::vector<long long>>> dp(N + 1, std::vector<std::vector<long long>>(m, std::vector<long long>(n, 0)));
        // 从外到内
        for (int step = 1; step <= N; step++)
        {
            for (int row = 0; row <= m - 1; row++)
            {
                for (int col = 0; col <= n - 1; col++)
                {
                    long long from_up = 0 == row ? 1 : dp[step - 1][row - 1][col];
                    long long from_down = m - 1 == row ? 1 : dp[step - 1][row + 1][col];
                    long long from_left = 0 == col ? 1 : dp[step - 1][row][col - 1];
                    long long from_right = n - 1 == col ? 1 : dp[step - 1][row][col + 1];
                    dp[step][row][col] = (from_up + from_down + from_left + from_right) % MOD;
                }
            }
        }
        return dp[N][i][j];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 583. 两个字符串的删除操作
// 动态规划 滚动数组

class Solution {
public:
    int minDistance(string word1, string word2) {
        // 步数最少，说明公共部分最长
        // 转换成求最长公共子串
        std::vector<std::vector<int>>  
        dp(word1.size() + 1, std::vector<int>(word2.size() + 1, 0));
        for (int row = 1; row <= word1.size(); row++)
        {
            for (int col = 1; col <= word2.size(); col++)
            {
                // 注意字符串下标
                if (word1.at(row - 1) == word2.at(col - 1))  
                {
                    dp[row][col] = dp[row - 1][col - 1] + 1;
                }
                else if (word1.at(row - 1) != word2.at(col - 1))  
                {
                    dp[row][col] = std::max(dp[row - 1][col],  
                                            dp[row][col - 1]);
                }
            }
        }

        return (word1.size() - dp[word1.size()][word2.size()]) +
               (word2.size() - dp[word1.size()][word2.size()]);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int minDistance(string dst, string src) {
        vector<vector<int>> dp(dst.size() + 1, vector<int>(src.size() + 1, 0));

        for (int row = 0; row <= dst.size(); row++) 
        {
            for (int col = 0; col <= src.size(); col++)
            {
/***** ***** ***** ***** ***** 添加其他操作 ***** ***** ***** ***** *****/
                if (0 == row && 0 == col)
                {
                    dp[0][0] = 0;
                }
                else if (0 == row && 0 != col)
                {
                    dp[0][col] = 0;
                }
                else if (0 != row && 0 == col)
                {
                    dp[row][0] = 0;
                }
                else if (src[col - 1] == dst[row - 1])
                {
                    dp[row][col] = 1 + dp[row - 1][col - 1];
                }
                else if (src[col - 1] != dst[row - 1])
                {
                    dp[row][col] = max(dp[row - 1][col - 1], 
                                   max(dp[row - 1][col], 
                                       dp[row][col - 1]));
                }
/***** ***** ***** ***** ***** 添加其他操作 ***** ***** ***** ***** *****/
            }
        }
        return (dst.size() - dp[dst.size()][src.size()]) +
               (src.size() - dp[dst.size()][src.size()]);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int minDistance(string word1, string word2) {
        // 步数最少，说明公共部分最长
        // 转换成求最长公共子串
        std::vector<std::vector<int>> 
        dp(2, std::vector<int>(word2.size() + 1, 0));
        // 滚动数组
        // row % 2 当前行
        // (row + 1) % 2 上一行
        // word1.size() % 2 最后一行
        for (int row = 1; row <= word1.size(); row++)
        {
            for (int col = 1; col <= word2.size(); col++)
            {
                // 注意字符串下标
                if (word1.at(row - 1) == word2.at(col - 1))  
                {
                    dp[row % 2][col] = dp[(row + 1) % 2][col - 1] + 1;
                }
                else if (word1.at(row - 1) != word2.at(col - 1))  
                {
                    dp[row % 2][col] = std::max(dp[(row + 1) % 2][col],  
                                                dp[row % 2][col - 1]);
                }
            }
        }

        return (word1.size() - dp[word1.size() % 2][word2.size()]) +
               (word2.size() - dp[word1.size() % 2][word2.size()]);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 589. N叉树的前序遍历
// 深度优先 递归 树

/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> children;

    Node() {}

    Node(int _val) {
        val = _val;
    }

    Node(int _val, vector<Node*> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution {
public:
    vector<int> preorder(Node* root) {
        std::vector<int> res;
        dfs(root, res);
        return res;
    }

private:
    void dfs(Node* root, std::vector<int>& res)
    {
        if (nullptr == root)
        {
            return;
        }

        res.push_back(root->val);

        for (auto node : root->children)
        {
            dfs(node, res);
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 590. N叉树的后序遍历
// 深度优先 树 递归

/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> children;

    Node() {}

    Node(int _val) {
        val = _val;
    }

    Node(int _val, vector<Node*> _children) {
        val = _val;
        children = _children;
    }
};
*/

class Solution {
public:
    vector<int> postorder(Node* root) {
        std::vector<int> res;
        dfs(root, res);
        return res;
    }

private:
    void dfs(Node* root, std::vector<int>& res)
    {
        if (nullptr == root)
        {
            return;
        }

        for (auto node : root->children)
        {
            dfs(node, res);
        }

        res.push_back(root->val);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 594. 最长和谐子序列
// 数组 排序 双指针（快慢指针） 哈希表

class Solution {
public:
    int findLHS(vector<int>& nums) {
        if (0 == nums.size())
        {
            return 0;
        }
        // 时间复杂度O(nlogn)
        // 空间复杂度O(1)
        // 排序+双指针
        std::sort(nums.begin(), nums.end());
        int res = 0;

        for (int fast = 0, slow = 0; fast <= nums.size() - 1;)
        {
            if (nums[fast] - nums[slow] == 1)
            {
                res = std::max(res, fast - slow + 1);
                fast++;
            }
            else if (nums[fast] - nums[slow] > 1)
            {
                slow++;
            }
            else if (nums[fast] - nums[slow] < 1)
            {
                fast++;
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int findLHS(vector<int>& nums) {
        // 时间复杂度O(n)
        // 空间复杂度O(n)
        // 哈希表
        std::unordered_map<int, int> m; // nums[i]=>count
        int res = 0;

        for (int num : nums)
        {
            m[num]++;
        }

        for (auto it = m.begin(); it != m.end(); it++)
        {
            if (m.find(it->first + 1) != m.end())
            {
                res = std::max(res, m[it->first] + m[it->first + 1]);
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int findLHS(vector<int>& nums) {
        // 时间复杂度O(n)
        // 空间复杂度O(n)
        // 哈希表 单次扫描（速度更慢，不如单独建好哈希表）
        std::unordered_map<int, int> m; // nums[i]=>count
        int res = 0;

        for (int num : nums)
        {
            m[num]++;

            if (m.find(num - 1) != m.end())
            {
                res = std::max(res, m[num - 1] + m[num]);
            }

            if (m.find(num + 1) != m.end())
            {
                res = std::max(res, m[num + 1] + m[num]);
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 599. 两个列表的最小索引总和
// 哈希表 数组
// 假设Andy和Doris想在晚餐时选择一家餐厅，并且他们都有一个表示最喜爱餐厅的列表，每个餐厅的名字用字符串表示。你需要帮助他们用最少的索引和找出他们共同喜爱的餐厅。 如果答案不止一个，则输出所有答案并且不考虑顺序。 你可以假设总是存在一个答案。

class Solution {
public:
    vector<string> findRestaurant(vector<string>& list1, vector<string>& list2) {
        std::unordered_map<std::string, int> m;
        std::vector<std::string> res;
        int sum = INT_MAX;

        for (int index = 0; index <= (int)list1.size() - 1; index++)
        {
            m[list1[index]] = index;
        }

        for (int index = 0; index <= (int)list2.size() - 1; index++)
        {
            if (m.find(list2[index]) != m.end())
            {
                if (m[list2[index]] + index < sum) // 更新数组模板
                {
                    sum = m[list2[index]] + index;
                    res.clear();
                    res.push_back(list2[index]);
                }
                else if (m[list2[index]] + index == sum)
                {
                    res.push_back(list2[index]);
                }
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 605. 种花问题
// 数组 贪心法

class Solution {
public:
    bool canPlaceFlowers(vector<int>& flowerbed, int n) {
        int res = 0; // 可以种花的地方个数

        for (int index = 0; index <= flowerbed.size() - 1; index++)
        {
            // 左边界可以不要考虑左侧，右边界可以不要考虑右侧
            if (0 == flowerbed[index] && 
                (0 == index || 0 == flowerbed[index - 1]) && 
                (flowerbed.size() - 1 == index || 0 == flowerbed[index + 1])) 
            {
                res++;
                flowerbed[index] = 1;
            }

            if (res >= n) // n可能是0
            {
                return true;
            }
        }
        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 606. 根据二叉树创建字符串
// 深度优先 树 递归 

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    string tree2str(TreeNode* t) {
        if (nullptr == t)
        {
            return "";
        }
        // 二叉树[root,left,right]，则转换为root(left)(right)。
        // 如果只有left为空节点，则输出root()(right)；
        // 如果只有right为空节点则可以忽略右节点的()，输出为root(left)。

        std::string s = std::to_string(t->val);
        std::string left = tree2str(t->left);
        std::string right = tree2str(t->right);

        if (nullptr == t->left && nullptr == t->right)
        {
            return s;
        }

        if (nullptr == t->right)
        {
            return s + "(" + left + ")";
        }

        return s + "(" + left + ")" + "(" + right + ")";
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 617. 合并二叉树
// 深度优先 递归 树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* mergeTrees(TreeNode* t1, TreeNode* t2) {
        if (nullptr == t1)
        {
            return t2;
        }

        if (nullptr == t2)
        {
            return t1;
        }

        TreeNode* root = new TreeNode(t1->val + t2->val);

        root->left = mergeTrees(t1->left, t2->left);
        root->right = mergeTrees(t1->right, t2->right);

        return root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 633. 平方数之和
// 双指针

class Solution {
public:
    bool judgeSquareSum(int c) {
        long a = 0;
        long b = std::sqrt(c);

        while (a <= b)
        {
            if (a * a + b * b == c)
            {
                return true;
            }
            else if (a * a + b * b > c)
            {
                b--;
            }
            else if (a * a + b * b < c)
            {
                a++;
            }
        }
        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 637. 二叉树的层平均值
// 广度优先 层次遍历 队 树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<double> averageOfLevels(TreeNode* root) {
        if (nullptr == root)
        {
            return {};
        }

        std::vector<double> res;
        std::queue<TreeNode*> q;

        q.push(root);

        while (false == q.empty())
        {
            int len = q.size();
            double cnt = len;
            double sum = 0;

            while (len--)
            {
                auto cur = q.front();
                q.pop();
                sum += cur->val;

                if (cur->left)
                {
                    q.push(cur->left);
                }

                if (cur->right)
                {
                    q.push(cur->right);
                }
            }
            res.push_back(sum / cnt);
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 645. 错误的集合
// 数学 数组 哈希表

class Solution {
public:
    vector<int> findErrorNums(vector<int>& nums) {
        int cur_sum = std::accumulate(nums.begin(), nums.end(), 0);
        int pre_sum = (1 + nums.size()) * nums.size() / 2;
        int dif = pre_sum - cur_sum;

        std::unordered_multiset<int> s;

        for (int num : nums)
        {
            s.insert(num);
            if (2 == s.count(num))
            {
                return {num, num + dif};
            }
        }
        
        return {};
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="646"></div>

```c++

// 646. 最长数对链
// 动态规划 Lambda函数 双指针（快慢指针）

class Solution {
public:
    int findLongestChain(vector<vector<int>>& pairs) {
        if (0 == pairs.size())
        {
            return 0;
        }
        // 300题的follow up
        std::sort(pairs.begin(), pairs.end(),
                  [](const std::vector<int>& a, const std::vector<int>& b)
                  {
                      return (a[0] < b[0]) || (a[0] == b[0] && a[1] < b[1]);
                  });
        
        std::vector<int> dp(pairs.size(), 1); // 至少1个
        int res = 1;

        for (int fast = 1; fast <= pairs.size() - 1; fast++)
        {
            for (int slow = 0; slow <= fast - 1; slow++)
            {
                if (pairs[slow][1] < pairs[fast][0])
                {
                    dp[fast] = std::max(dp[fast], dp[slow] + 1);
                }
                
                res = std::max(res, dp[fast]);
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="647"></div>

```c++

// 647. 回文子串
// 动态规划 字符串 马拉车 双指针（相向指针）

class Solution {
public:
    int countSubstrings(string s) {
        // 状态转移：左下=>右上：dp[i + 1][j - 1]=>dp[i][j]
        // 最后统计上三角true个数就行了
        // dp[row][col] 表示截取字符串中i到j
        std::vector<std::vector<bool>> dp(s.size(), std::vector<bool>(s.size(), false));
        int res = 0;

        for (int row = s.size() - 1; row >= 0; row--) // 填上三角就行
        {
            for (int col = row; col <= s.size() - 1; col++)
            {
                if (s[row] == s[col])
                {
                    if (row == col) // 主对对角线
                    {
                        dp[row][col] = true;
                    }
                    else if (col - row == 1) // 相邻元素
                    {
                        dp[row][col] = true;
                    }
                    else if (col - row > 1)
                    {
                        dp[row][col] = dp[row + 1][col - 1];
                    }
                }
                else if (s[row] == s[col])
                {
                    dp[row][col] = false;
                }
                // 统计true个数
                if (true == dp[row][col])
                {
                    res++;
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int countSubstrings(string s) {
        int res = 0;
        std::string m_s = "#";

        for (char c : s)
        {
            m_s += c;
            m_s += "#";
        }

        for (int index = 0; index <= m_s.size() - 1; index++)
        {
            for (int left = index, right = index; 
                 left >= 0 && right <= m_s.size() - 1; 
                 left--, right++)
            {
                if (m_s[left] != m_s[right])
                {
                    break;
                }

                if ('#' != m_s[left] && '#' != m_s[right])
                {
                    res++;
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 648. 单词替换
// 哈希表 字符串 字符串分割
// 在英语中，我们有一个叫做 词根(root)的概念，它可以跟着其他一些词组成另一个较长的单词——我们称这个词为 继承词(successor)。例如，词根an，跟随着单词 other(其他)，可以形成新的单词 another(另一个)。现在，给定一个由许多词根组成的词典和一个句子。你需要将句子中的所有继承词用词根替换掉。如果继承词有许多可以形成它的词根，则用最短的词根替换它。你需要输出替换之后的句子。

class Solution {
public:
    string replaceWords(vector<string>& dictionary, string sentence) {
        std::unordered_set<std::string> m;
        std::vector<std::string> v;
        std::string res;

        split(sentence, v, " ");

        for (auto word : dictionary)
        {
            m.insert(word);
        }

        for (int row = 0; row <= (int)v.size() - 1; row++)
        {
            for (int len = 1; len <= v[row].size() - 1; len++)
            {
                if (m.find(v[row].substr(0, len)) != m.end())
                {
                    std::string tmp = v[row].substr(0, len);
                    v[row].clear();
                    v[row] = tmp;
                    break;
                }
            }
            res = res + v[row] + " ";
        }
        return res.substr(0, res.size() - 1);
    }

private:
    // 字符串分割函数
    void split(const std::string& s, std::vector<std::string>& res, const std::string& c)
    {
        std::string::size_type slow = 0;
        std::string::size_type fast = s.find(c);

        while (std::string::npos != fast)
        {
            res.push_back(s.substr(slow, fast - slow));
            slow = fast + 1;
            fast = s.find(c, slow);
        }

        if (slow != s.size())
        {
            res.push_back(s.substr(slow));
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 653. 两数之和 IV - 输入 BST
// 广度优先 哈希表 队

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool findTarget(TreeNode* root, int k) {
        std::set<int> s;
        std::queue<TreeNode*> q;
        q.push(root);

        while (false == q.empty())
        {
            auto cur = q.front();
            q.pop();

            if (0 != s.count(k - cur->val))
            {
                return true;
            }

            s.insert(cur->val);

            if (cur->left)
            {
                q.push(cur->left);
            }

            if (cur->right)
            {
                q.push(cur->right);
            }
        }
        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 658. 找到 K 个最接近的元素
// 二分法 双指针（相向指针） 数组

class Solution {
public:
    vector<int> findClosestElements(vector<int>& arr, int k, int x) {
        // 找左边界
        int left = 0;
        int right = arr.size() - k; // 腾出右边
        // 假设 mid 是左边界，则当前区间覆盖的范围是 [mid, mid + k -1]
        // 如果发现 a[mid] 与 x 距离比 a[mid + k] 与 x 的距离要大，说明解一定在右侧
        while (left < right)
        {
            int mid = left + (right - left) / 2;

            if (x - arr[mid] > arr[mid + k] - x)
            {
                left = mid + 1;
            }
            else if (x - arr[mid] < arr[mid + k] - x)
            {
                right = mid;
            }
            else if (x - arr[mid] == arr[mid + k] - x)
            {
                right = mid;
            }
        }

        return std::vector<int> (arr.begin() + left, arr.begin() + left + k);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 662. 二叉树最大宽度
// 深度优先 递归 二叉树 前序遍历
// 给定一个二叉树，编写一个函数来获取这个树的最大宽度。树的宽度是所有层中的最大宽度。这个二叉树与满二叉树（full binary tree）结构相同，但一些节点为空。每一层的宽度被定义为两个端点（该层最左和最右的非空节点，两端点间的null节点也计入长度）之间的长度。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int widthOfBinaryTree(TreeNode* root) {
        res = 0;
        dfs(root, 0, 1);
        return res;
    }

private:
    std::vector<int> v; // 保存每一层开头结点
    int res;

    void dfs(TreeNode* root, unsigned long long index, int depth)
    {
        if (nullptr == root)
        {
            return;
        }

        if (depth == v.size() + 1)
        {
            v.push_back(index); // 每一层最左边结点下标
        }

        res = std::max(res, (int)index - v[depth - 1] + 1); // 当前下标-开头下标

        dfs(root->left, index * 2 + 1, depth + 1);
        dfs(root->right, index * 2 + 2, depth + 1);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 663. 均匀树划分
// 深度优先 递归 后序遍历 二叉树
// 给定一棵有 n 个结点的二叉树，你的任务是检查是否可以通过去掉树上的一条边将树分成两棵，且这两棵树结点之和相等。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool checkEqualTree(TreeNode* root) {
        int total_sum = dfs(root);
        v.pop_back(); // 防止最后一个元素和为0

        if (total_sum % 2)
        {
            return false;
        }
        return v.end() != std::find(v.begin(), v.end(), total_sum / 2);
    }

private:
    std::vector<int> v; // sum

    int dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return 0;
        }

        int left_res = dfs(root->left);
        int right_res = dfs(root->right);

        int sum = root->val + left_res + right_res;
        v.push_back(sum);
        return sum;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 665. 非递减数列
// 数组 贪心

class Solution {
public:
    bool checkPossibility(vector<int>& nums) {
        if (1 >= nums.size())
        {
            return true;
        }

        int res = 0;  
        for (int index = 0; index <= nums.size() - 2; index++)
        {
            if (nums[index] <= nums[index + 1])
            {
                continue;
            }
            else if (nums[index] > nums[index + 1])
            {
                res++;
                if (res > 1) // 减枝
                {
                    return false;
                }
                // 分两种情况讨论
                if (index - 1 < 0 || nums[index - 1] <= nums[index + 1])
                {
                    nums[index] = nums[index + 1]; // 2 4 2 6=>2 2 2 6
                }
                else if (nums[index - 1] > nums[index + 1])
                {
                    nums[index + 1] = nums[index]; // 3 4 2 6=>3 4 4 6
                }
            }
        }
        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 669. 修剪二叉搜索树
// 深度优先 递归 树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* trimBST(TreeNode* root, int L, int R) {
        if (nullptr == root)
        {
            // 全部砍掉
            return nullptr;
        }
        else if (R < root->val)
        {
            // 砍掉右边
            return trimBST(root->left, L, R);
        }
        else if (root->val < L)
        {
            // 砍掉左边
            return trimBST(root->right, L, R);
        }
        else // L < root->val < R
        {
            // 全部留着
            root->left = trimBST(root->left, L, R);
            root->right = trimBST(root->right, L, R);
            return root;
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 671. 二叉树中第二小的节点
// 深度优先 树 递归 后序遍历

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int min_value = 0;
    int findSecondMinimumValue(TreeNode* root) {
        this->min_value = root->val;
        return dfs(root);
    }
private:
    int dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return -1; // 递归出口
        }

        if (root->val > min_value)
        {
            // 根节点肯定是最小值，只要比它就返回
            return root->val;
        }

        int left = dfs(root->left);
        int right = dfs(root->right);

        if (-1 == left && -1 == right)
        {
            return -1;
        }
        else if (-1 == left)
        {
            return right;
        }
        else if (-1 == right)
        {
            return left;
        }
        else // -1 != left && -1 != right
        {
            return std::min(left, right);
        }  
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 677. 键值映射
// 类 前缀树 哈希表

class MapSum {
public:
    /** Initialize your data structure here. */
    MapSum() {

    }

    void insert(string key, int val) {
        TrieNode* cur = &root;

        for (auto c : key)
        {  
            if (nullptr == cur->children[c - 'a'])
            {
                cur->children[c - 'a'] = new TrieNode();
            }
            // 此处m[key]为默认值0，之后输入相同的key将覆盖
            // 如先后输入["aa", 3]["aa", 2]，结果应为2
            cur->children[c - 'a']->sum += val - m[key];
            cur = cur->children[c - 'a'];
        }
        m[key] = val; // 最后才把键值对添加
    }

    int sum(string prefix) {
        TrieNode* cur = &root;
        for (auto c : prefix)
        {
            if (nullptr == cur->children[c - 'a'])
            {
                return 0;
            }
            cur = cur->children[c - 'a'];
        }
        return cur->sum;
    }

private:
    struct TrieNode
    {
        int sum;
        std::vector<TrieNode*> children;
        // 构造函数
        TrieNode ()
        : sum(0), children(26, nullptr)
        {

        }
        // 析构函数
        ~TrieNode ()
        {
            for (auto child : children)
            {
                if (child) // delete自动递归删除
                {
                    delete child;
                }
            }
            children.clear(); // 清空权值
        }
    };

    TrieNode root; // 空节点
    std::unordered_map<std::string, int> m; 
};

/**
 * Your MapSum object will be instantiated and called as such:
 * MapSum* obj = new MapSum();
 * obj->insert(key,val);
 * int param_2 = obj->sum(prefix);
 */

```
<div STYLE="page-break-after: always;"></div>

```c++

// 678. 有效的括号字符串
// 贪心法

class Solution {
public:
    bool checkValidString(string s) {
        /*
        lo、hi表示「可能多余的左括号」，一个下界，一个上界，很直观。执行起来就是
        遇到左括号：lo++, hi++
        遇到星号：lo--, hi++（因为星号有三种情况）
        遇到右括号：lo--, hi--
        lo要保持不小于0。（要理解lo的意思，考虑下这个例子(**)(
        如果hi < 0，说明把星号全变成左括号也不够了，False
        最後，如果lo > 0，说明末尾有多余的左括号，False
        */
        int max_match = 0; // 最多（数，也就是最多需要多少个）来匹配
        int min_match = 0; // 最少（数，也就是最少需要多少个）来匹配

        for (auto c : s)
        {
            if ('(' == c)
            {
                min_match++;
                max_match++;
            }
            else if (')' == c)
            {
                if (min_match > 0)
                {
                    min_match--;
                }

                max_match--; // 上界-1
            }
            else if ('*' == c)
            {
                if (min_match > 0) // 需要)
                {
                    min_match--;
                }

                max_match++; // 上界+1
            }

            if (-1 == max_match)
            {
                return false;
            }      
        }

        return 0 == min_match;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 680. 验证回文字符串 Ⅱ
// 双指针（相向指针）

class Solution {
public:
    bool validPalindrome(string s) {
        for (int left = 0, right = s.size() - 1; 
             left < right; left++, right--)
        {
            if (s[left] != s[right])
            {
                return two_point(s, left, right - 1) || 
                       two_point(s, left + 1, right);
            }
        }
        return true;
    }

private:
    bool two_point(std::string s, int left, int right)
    {
        while (left < right)
        {
            if (s[left++] != s[right--])
            {
                return false;
            }
        }
        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 684. 冗余连接
// 图 连通分量 环 深度优先 回溯 kruskal算法

class Solution {
public:
    vector<int> findRedundantConnection(vector<vector<int>>& edges) {
        // 题设给的是边和顶点的数组，转换为邻接数组
        // 由于不是从0开始定义边，用哈希表定义邻接表
        std::unordered_map<int, std::vector<int>> graph; // node=>{node list}
        for (auto edge : edges)
        {
            graph[edge[0]].push_back(edge[1]);
            graph[edge[1]].push_back(edge[0]);
        }

        // 因为要输出最后一条边，反向遍历边数组
        for (auto r_it = edges.rbegin(); r_it != edges.rend(); r_it++)
        {
            std::unordered_set<int> visited;
            // 先删除直接相连的那条边
            graph[(*r_it)[0]].erase(find(graph[(*r_it)[0]].begin(), 
                                         graph[(*r_it)[0]].end(), 
                                         (*r_it)[1]));
            // 深度优先，找环
            if (dfs(graph, (*r_it)[0], (*r_it)[1], visited))
            {
                return *r_it;
            }
            // 回溯，添加上那条边
            graph[(*r_it)[0]].push_back((*r_it)[1]);
        }
        return {};
    }

private:
    bool dfs(std::unordered_map<int, std::vector<int>>& graph,
             int start, int end, std::unordered_set<int>& visited)
    {
        if (start == end) // 有环
        {
            return true;
        }

        visited.insert(start); 

        for (auto next : graph[start])
        {
            if (visited.find(next) != visited.end())
            {
                continue;
            }

            if (dfs(graph, next, end, visited)) // 只要一次发现环，逐层返回
            {
                return true; // 有环
            }
        }
        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    vector<int> findRedundantConnection(vector<vector<int>>& edges) {
        // 题设给的是边和顶点的数组，转换为邻接数组
        // 由于不是从0开始定义边，用哈希表定义邻接表
        std::unordered_map<int, std::vector<int>> graph; // node=>{node list}
        // kruskal算法
        for (auto edge : edges)
        {
            std::unordered_set<int> visited;
            if (dfs(graph, edge[0], edge[1], visited))
            {
                return edge;
            }
            // 没环就添加这条边
            graph[edge[0]].push_back(edge[1]);
            graph[edge[1]].push_back(edge[0]);
        }
        return {};
    }

private:
    bool dfs(std::unordered_map<int, std::vector<int>>& graph,
             int start, int end, std::unordered_set<int>& visited)
    {
        if (start == end) // 有环
        {
            return true;
        }

        visited.insert(start); 

        for (auto next : graph[start])
        {
            if (visited.find(next) != visited.end())
            {
                continue;
            }

            if (dfs(graph, next, end, visited)) // 只要一次发现环，逐层返回
            {
                return true; // 有环
            }
        }
        return false;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 687. 最长同值路径
// 深度优先 树 递归 公共祖先

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int longestUnivaluePath(TreeNode* root) {
        if (nullptr == root)
        {
            return 0;
        }
        dfs(root, root->val);
        return max_len;
    }

private:
    int max_len;

    int dfs(TreeNode* root, int pre_val)
    {
        if (nullptr == root)
        {
            return 0;
        }
        // 每次求出左右子树最长路径
        int left_len = dfs(root->left, root->val);
        int right_len = dfs(root->right, root->val);

        max_len = std::max(max_len, left_len + right_len);
        // pre_val是上一个节点的值，若与当前节点相等则加1
        return (pre_val == root->val) ?  
               std::max(left_len, right_len) + 1 : 0;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 690. 员工的重要性
// 深度优先 递归 哈希表

/*
// Definition for Employee.
class Employee {
public:
    int id;
    int importance;
    vector<int> subordinates;
};
*/

class Solution {
public:
    int getImportance(vector<Employee*> employees, int id) {
        std::unordered_map<int, Employee*> m_employees;
        for (auto e : employees)
        {
            m_employees[e->id] = e;
        }

        return dfs(m_employees, id);
    }

private:
    int dfs(const std::unordered_map<int, Employee*> m_employees, 
            const int id)
    {
        int sum = 0;
        sum += m_employees.at(id)->importance;

        for (auto s : m_employees.at(id)->subordinates)
        {
            sum += dfs(m_employees, s);
        }

        return sum;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 692. 前K个高频单词
// 堆 优先队列 哈希表 字符串 排序

class Solution {
public:
    vector<string> topKFrequent(vector<string>& words, int k) {
        std::unordered_map<std::string, int> m; // word=>count
        for (auto& word : words)
        {
            m[word]++;
        }

        auto comp = [](const std::pair<std::string, int>& a, 
                       const std::pair<std::string, int>& b)
        {
            if (a.second == b.second)
            {
                return a.first < b.first; // 字典序
            }
            return a.second > b.second; // 次数(注意符号)
        };

        std::priority_queue<std::pair<std::string, int>, 
                            std::vector<std::pair<std::string, int>>, 
                            decltype(comp)> q(comp); // 小堆

        for (auto key : m)
        {
            q.push(key);
            if (q.size() > k)
            {
                q.pop();
            }
        }

        std::vector<std::string> res;

        while (false == q.empty())
        {
            res.push_back(q.top().first); // 从小到大弹出
            q.pop();
        }

        std::reverse(res.begin(), res.end());
        return res;
    }   
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 695. 岛屿的最大面积
// 深度优先 回溯 递归

class Solution {
public:
    int maxAreaOfIsland(vector<vector<int>>& grid) {
        if (0 == grid.size())
        {
            return 0;
        }

        int max_area = 0;

        for (int row  = 0; row <= grid.size() - 1; row++)
        {
            for (int col = 0; col <= grid[0].size() - 1; col++)
            {
                if (1 == grid[row][col])
                {
                    max_area = std::max(max_area, dfs(grid, row, col));
                }
            }
        }

        return max_area;
    }

private:
    int dfs(std::vector<std::vector<int>>& grid, int row, int col)
    {
        if (row < 0 || row >= grid.size() || 
            col < 0 || col >= grid[0].size() || 
            0 == grid[row][col])
        {
            return 0;
        }

        int area = 1;
        grid[row][col] = 0; // 沉岛
        area += dfs(grid, row + 1, col);
        area += dfs(grid, row - 1, col);
        area += dfs(grid, row, col + 1);
        area += dfs(grid, row, col - 1);

        return area;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 696. 计数二进制子串
// 字符串 双指针（快慢指针）

class Solution {
public:
    int countBinarySubstrings(string s) {
        int slow = 0; // 前一个数字连续出现的次数
        int fast = 1; // 当前数字连续出现的次数
        int res = 0;

        for (int index = 1; index <= s.size() - 1; index++)
        {
            if (s[index - 1] == s[index]) 
            {
                fast++; // 当前数字出现次数增加，fast去找不同数
            }
            else if (s[index - 1] != s[index])
            {
                slow = fast; // 前面有几个相反的连续的数字
                fast = 1; // fast重新开始数
            }

            res = (slow >= fast) ? res + 1 : res;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 697. 数组的度
// 数组 哈希表

class Solution {
public:
    int findShortestSubArray(vector<int>& nums) {
        std::unordered_map<int, int> m; // num=>count
        int depth = 0;
        for(auto num : nums){
            m[num]++;
            depth = std::max(depth, m[num]);
        }

        m.clear();
        int left = 0;
        int right = 0;
        int res = INT_MAX;

        while (right < nums.size())
        {
            m[nums[right]]++; // 重新输入
            
            if (depth == m[nums[right]]) // 右边界找到一个下标最小的
            {
                while (left <= right && depth == m[nums[right]]) // 找左边界
                {
                    // 只要depth没变，说明不是相对的
                    // 自动去除长的那一组，因为right是最靠近中间的
                    m[nums[left]]--;
                    left++;
                }
                res = std::min(res, right - left + 2); // left上面多加了一次
            }
            right++;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 700. 二叉搜索树中的搜索
// 二叉搜索树 递归
// 给定二叉搜索树（BST）的根节点和一个值。 你需要在BST中找到节点值等于给定值的节点。 返回以该节点为根的子树。 如果节点不存在，则返回 NULL。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* searchBST(TreeNode* root, int val) {
        if (nullptr == root)
        {
            return nullptr;
        }

        if (root->val == val)
        {
            return root;
        }
        else if (root->val > val)
        {
            return searchBST(root->left, val);
        }
        else
        {
            return searchBST(root->right, val);
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 701. 二叉搜索树中的插入操作
// 深度优先 二叉搜索树 递归 
// 给定二叉搜索树（BST）的根节点和要插入树中的值，将值插入二叉搜索树。 返回插入后二叉搜索树的根节点。 保证原始二叉搜索树中不存在新值。注意，可能存在多种有效的插入方式，只要树在插入后仍保持为二叉搜索树即可。 你可以返回任意有效的结果。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    TreeNode* insertIntoBST(TreeNode* root, int val) {
        if (nullptr == root)
        {
            return new TreeNode(val);
        }

        if (root->val > val)
        {
            root->left = insertIntoBST(root->left, val);
        }
        else
        {
            root->right = insertIntoBST(root->right, val);
        }

        return root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 704. 二分查找
// 二分法

class Solution {
public:
    int search(vector<int>& nums, int target) {
        // 双闭流派
        // left和right均为合法区间
        int left = 0;
        int right = nums.size() - 1;

        while (left <= right)
        {
            int mid = left + (right - left) / 2;

            if (target == nums[mid])
            {
                return mid;
            }
            else if (target < nums[mid])
            {
                right = mid - 1;
            }
            else if (target > nums[mid])
            {
                left = mid + 1;
            }
        }

        return -1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int search(vector<int>& nums, int target) {
        // 左闭右开流派
        // left为有效值，right为无效值
        int left = 0; // 闭区间
        int right = nums.size(); // 开区间

        while (left < right)
        {
            // mid向下取整，一定是合法位置，因为左边界是闭区间
            int mid = left + (right - left) / 2; 

            if (target == nums[mid])
            {
                return mid;
            }
            else if (target > nums[mid])
            {
                left = mid + 1; // mid已经不可能，所以+1，left找可能的值
            }
            else if (target < nums[mid])
            {
                right = mid; // mid已经不可能，right找不可能的值
            }
        }
        return -1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="714"></div>

```c++

// 714. 买卖股票的最佳时机含手续费
// 动态规划 滚动数组

class Solution {
public:
    int maxProfit(vector<int>& prices, int fee) {
        // dp[i][j] 表示 [0, i] 区间内，到第 i 天（从 0 开始）状态为 j 时的最大收益。
        // dp[i][0]：当天不持股，可以由昨天不持股和昨天持股转换而来。
        //           昨天不持股，今天仍然不持股，则说明今天什么都没做。
        //           昨天持股，今天不持股，则说明今天卖出了一股。
        //           手续费在买入股票的时候，一起扣掉。
        //           也可以规定在卖出一股的时候，扣除手续费，前后统一即可。
        // dp[i][1]：当天持股，也可以由昨天不持股和昨天持股转换而来。
        //           昨天不持股，今天持股，则说明今天买了一股，并且扣除了手续费。
        //           昨天持股，今天仍然持股，则说明今天什么都没做。
        std::vector<std::vector<int>> dp(prices.size(), std::vector<int>(2, 0));
        dp[0][0] = 0; // 在第 0 天，不持股的初始化值为 0
        dp[0][1] = -prices[0] - fee; // 持股的购买了，收益为 -prices[0] - fee

        for (int day = 1; day <= prices.size() - 1; day++)
        {
            dp[day][0] = std::max(dp[day - 1][0], dp[day - 1][1] + prices[day]);
            dp[day][1] = std::max(dp[day - 1][1], 
                                  dp[day - 1][0] - prices[day] - fee);
        }
        return dp[prices.size() - 1][0]; // 最优值在最后一天，并且是不持股的状态
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int maxProfit(vector<int>& prices, int fee) {
        // dp[i][j] 表示 [0, i] 区间内，到第 i 天（从 0 开始）状态为 j 时的最大收益。
        // profit：当天不持股，可以由昨天不持股和昨天持股转换而来。
        //         昨天不持股，今天仍然不持股，则说明今天什么都没做。
        //         昨天持股，今天不持股，则说明今天卖出了一股。
        //         手续费在买入股票的时候，一起扣掉。
        //         也可以规定在卖出一股的时候，扣除手续费，前后统一即可。
        // hold：当天持股，也可以由昨天不持股和昨天持股转换而来。
        //       昨天不持股，今天持股，则说明今天买了一股，并且扣除了手续费。
        //       昨天持股，今天仍然持股，则说明今天什么都没做。
        
        // 只跟前一天有关，设置滚动数组
        int profit = 0;
        int hold = -prices[0] - fee;
        // 差分数组少一天
        for (int day = 1; day <= prices.size() - 1; day++)
        {
            profit = std::max(profit, hold + prices[day]);
            hold = std::max(hold, profit - prices[day] - fee);
        }
        return profit;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 718. 最长重复子数组
// 动态规划 滚动数组 最长公共子数组
// 给两个整数数组 A 和 B ，返回两个数组中公共的、长度最长的子数组的长度。

class Solution {
public:
    int findLength(vector<int>& A, vector<int>& B) {
        std::vector<std::vector<int>> dp(A.size() + 1, std::vector<int>(B.size() + 1, 0));
        int res = 0;

        for (int row = 1; row <= (int)A.size(); row++)
        {
            for (int col = 1; col <= (int)B.size(); col++)
            {
                if (A[row - 1] == B[col - 1])
                {
                    dp[row][col] = dp[row - 1][col - 1] + 1;
                    res = std::max(res, dp[row][col]);
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int findLength(vector<int>& A, vector<int>& B) {
        std::vector<std::vector<int>> dp(2, std::vector<int>(B.size() + 1, 0));
        int res = 0;

        for (int row = 1; row <= (int)A.size(); row++)
        {
            for (int col = 1; col <= (int)B.size(); col++)
            {
                if (A[row - 1] == B[col - 1])
                {
                    dp[row % 2][col] = dp[(row + 1) % 2][col - 1] + 1;
                    res = std::max(res, dp[row % 2][col]);
                }
                else if (A[row - 1] != B[col - 1])
                {
                    dp[row % 2][col] = 0;
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 720. 词典中最长的单词
// 哈希表 字符串
// 给出一个字符串数组words组成的一本英语词典。从中找出最长的一个单词，该单词是由words词典中其他单词逐步添加一个字母组成。若其中有多个可行的答案，则返回答案中字典序最小的单词。若无答案，则返回空字符串。

class Solution {
public:
    string longestWord(vector<string>& words) {
        std::unordered_map<std::string, int> m; // word=>length
        std::string res;
        
        for (auto word : words)
        {
            m[word] = word.size();
        }

        for (auto word : words)
        {
            if (m[word] < res.size() || m[word] == res.size() && word > res)
            {
                continue;
            }

            for (int len = 1; len <= word.size(); len++)
            {
                if (m.find(word.substr(0, len)) == m.end())
                {
                    break;
                }

                if (len == word.size())
                {
                    res = word;
                }
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 725. 分隔链表
// 链表

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    vector<ListNode*> splitListToParts(ListNode* root, int k) {
        int len = 0;
        auto p = root;
        while (p)
        {
            p = p->next;
            len++;
        }
        int quotient = len / k;
        int remainder = len % k;

        std::vector<ListNode*> res(k, nullptr);
        ListNode* pre = nullptr;
        ListNode* cur = root;

        for (int index = 0; index <= k - 1; index++)
        {
            int length = remainder > 0 ? quotient + 1 : quotient;
            remainder = remainder > 0 ? remainder - 1: 0;
            res[index] = cur;

            while (length--) // 分出长度
            {
                pre = cur;
                cur = cur->next;
            }

            if (pre) // 割
            {
                pre->next = nullptr;
            }  
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 733. 图像渲染
// 深度优先 递归 

class Solution {
public:
    vector<vector<int>> floodFill(vector<vector<int>>& image, 
                                  int sr, int sc, int newColor) 
    {
        if (image[sr][sc] == newColor)
        {
            return image;
        }

        dfs(image, sr, sc, newColor, image[sr][sc]);

        return image;
    }

private:
    void dfs(std::vector<std::vector<int>>& image, 
             int row, int col, int newColor, int orgColor)
    {
        if (row < 0 || row >= image.size() || 
            col < 0 || col >= image[0].size())
        {
            return;
        }

        if (image[row][col] != orgColor) // 颜色不同，不在同一个像素
        {
            return; // 分成两种情况：原来就不同的和已经换颜色了的
        }

        image[row][col] = newColor;

        dfs(image, row - 1, col, newColor, orgColor);
        dfs(image, row + 1, col, newColor, orgColor);
        dfs(image, row, col - 1, newColor, orgColor);
        dfs(image, row, col + 1, newColor, orgColor);
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="739"></div>

```c++

// 739. 每日温度
// 单调栈 动态规划 双指针（快慢指针）

class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& T) {
        std::vector<int> res(T.size(), 0);
        std::stack<int> s;

        for (int index = 0; index <= T.size() - 1; index++)
        {
            // 当前温度大于栈顶温度，更新栈
            while (false == s.empty() && T[index] > T[s.top()]) // pop
            {
                res[s.top()] = index - s.top();
                s.pop();
            }
            s.push(index);
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& T) {
        std::vector<int> res(T.size(), 0);
        // 倒数第二个开始,从后往前
        for (int fast = T.size() - 2; fast >= 0; fast--)
        {
            for (int slow = fast + 1; slow <= T.size() - 1; slow += res[slow])
            {
                if (T[fast] >= T[slow] && 0 != res[slow])
                {
                    continue; // 去找更大的slow
                }
                else if (T[fast] >= T[slow] && 0 == res[slow])
                {
                    break; // 找不到更大的
                }
                else if (T[fast] < T[slow])
                {
                    res[fast] = slow - fast;
                    break; // 找到就退出
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 742. 二叉树最近的叶节点
// 深度优先 广度优先 图
// 给定一个 每个结点的值互不相同 的二叉树，和一个目标值 k，找出树中与目标值 k 最近的叶结点。 这里，与叶结点 最近 表示在二叉树中到达该叶节点需要行进的边数与到达其它叶结点相比最少。而且，当一个结点没有孩子结点时称其为叶结点。在下面的例子中，输入的树以逐行的平铺形式表示。实际上的有根树 root 将以TreeNode对象的形式给出。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int findClosestLeaf(TreeNode* root, int k) {
        m.clear();
        start = nullptr;
        dfs(nullptr, root, k);
        std::queue<TreeNode*> q;
        q.push(start);
        std::unordered_set<TreeNode*> visited;

        while (false == q.empty())
        {
            int len = q.size();

            while (len--)
            {
                TreeNode* cur = q.front();
                q.pop();
                visited.insert(cur);

                if (!cur->left && !cur->right) // 叶子结点
                {
                    return cur->val;
                }

                for (auto node : m[cur])
                {
                    if (0 == visited.count(node))
                    {
                        q.push(node);
                    }
                }
            }
        }
        return 0;
    }

private:
    std::unordered_map<TreeNode*, std::vector<TreeNode*>> m; // 邻接表
    TreeNode* start; // 起始点
    // 树转换为图 tree to graph
    void dfs(TreeNode* parent, TreeNode* child, int target)
    {
        if (nullptr == child)
        {
            return;
        }

        if (child->val == target)
        {
            start = child;
        }

        if (parent)
        {
            m[parent].push_back(child);
            m[child].push_back(parent);
        }

        dfs(child, child->left, target);
        dfs(child, child->right, target);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 744. 寻找比目标字母大的最小字母
// 双指针（相向指针） 二分法 数组

class Solution {
public:
    char nextGreatestLetter(vector<char>& letters, char target) {
        // 双闭区间流派
        int left = 0;
        int right = letters.size() - 1;

        while (left <= right)
        {
            int mid = left + (right - left) / 2;

            if (target == letters[mid])
            {
                left = mid + 1; // 重复的话往右走
            }
            else if (target < letters[mid])
            {
                right = mid - 1;
            }
            else if (target > letters[mid])
            {
                left = mid + 1;
            }
        }

        return letters[left % letters.size()];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    char nextGreatestLetter(vector<char>& letters, char target) {
        // 左闭右开流派
        // left为有效值，right为无效值
        int left = 0; // 闭区间
        int right = letters.size(); // 开区间

        while (left < right)
        {
            // mid向下取整，一定是合法位置，因为左边界是闭区间
            int mid = left + (right - left) / 2;

            if (target == letters[mid])
            {
                left = mid + 1; // 重复的话往右走
            }
            else if (target < letters[mid])
            {
                right = mid; // mid已经不可能，right找不可能的值
            }
            else if (target > letters[mid])
            {
                left = mid + 1; // mid已经不可能，所以+1，left找可能的值
            }
        }
        // 返回闭区间left
        return letters[left % letters.size()];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 754. 到达终点数字
// 数学

class Solution {
public:
    int reachNumber(int target) {
        /*
        等价于+(-) 1 +(-) 2 +(-) 3 +(-) 4 +(-) 5 +(-) ... +(-) n = sum
        等价于1...n中插入+-符号
        并且找到最小的n
        */
        target = std::abs(target);
        int n = 0;
        int sum = 0;
        while (sum < target)
        {
            sum += (++n);
        }

        const int d = sum - target;
        
        if (0 == d % 2)
        {
            return n;
        }

        return n + 1 + (n % 2);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 763. 划分字母区间
// 字符串 双指针（快慢指针）

class Solution {
public:
    vector<int> partitionLabels(string S) {
        std::vector<int> res;
        int fast = 0;
        int slow = 0;

        for (int index = 0; index <= S.size() - 1; index++)
        {
            // find_last_of返回索引
            fast = std::max(fast, (int)S.find_last_of(S[index]));

            if (index == fast)
            {
                res.push_back(fast - slow + 1);
                slow = fast + 1;
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 766. 托普利茨矩阵
// 矩阵

class Solution {
public:
    bool isToeplitzMatrix(vector<vector<int>>& matrix) {
        for (int row = 1; row <= matrix.size() - 1; row++)
        {
            for (int col = 1; col <= matrix[0].size() - 1; col++)
            {
                if (matrix[row][col] != matrix[row - 1][col - 1])
                {
                    return false;
                }
            }
        }
        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 769. 最多能完成排序的块
// 数组

class Solution {
public:
    int maxChunksToSorted(vector<int>& arr) {
        int res = 0;
        int max_num = 0;
        for (int index = 0; index <= arr.size() - 1; index++)
        {
            // 找到序号为最大值的那个点，排序完那一串肯定就是有序的
            max_num = std::max(max_num, arr[index]);
            res = max_num == index ? res + 1: res;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 776. 拆分二叉搜索树
// 递归 二叉搜索树
// 给你一棵二叉搜索树（BST）、它的根结点 root 以及目标值 V。请将该树按要求拆分为两个子树：其中一个子树结点的值都必须小于等于给定的目标值 V；另一个子树结点的值都必须大于目标值 V；树中并非一定要存在值为 V 的结点。除此之外，树中大部分结构都需要保留，也就是说原始树中父节点 P 的任意子节点 C，假如拆分后它们仍在同一个子树中，那么结点 P 应仍为 C 的子结点。你需要返回拆分后两个子树的根结点 TreeNode，顺序随意。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<TreeNode*> splitBST(TreeNode* root, int V) {
        if (nullptr == root)
        {
            return {nullptr, nullptr}; // 小树， 大树
        }

        if (root->val > V)
        {
            auto res_left = splitBST(root->left, V);
            root->left = res_left[1]; // 大树接上左边大的
            return {res_left[0], root}; // 小树， 大树
        }
        else // root->val < V
        {
            auto res_right = splitBST(root->right, V);
            root->right = res_right[0]; // 小树接上右边小的
            return {root, res_right[1]}; // 小树， 大树
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 778. 水位上升的泳池中游泳
// 广度优先 队列 方位（方向）数组 优先队列 堆

class Solution {
public:
    int dx[4] = {0, 0, -1, 1};
    int dy[4] = {-1, 1, 0, 0};

    int swimInWater(vector<vector<int>>& grid) {
        // 小堆：time=>postion(dy * N + dx)
        std::priority_queue<std::pair<int, int>, 
                            std::vector<std::pair<int, int>>, 
                            greater<std::pair<int, int>>> q; 

        std::vector<std::vector<bool>> 
        visited(grid.size(), std::vector<bool>(grid.size(), false));
        
        q.push({grid[0][0], 0 * grid.size() + 0});
        visited[0][0] = true;

        while (false == q.empty())
        {   
            auto cur = q.top();
            q.pop();

            if (cur.second % grid.size() == grid.size() - 1 &&
                cur.second / grid.size() == grid.size() - 1)
            {
                return cur.first;
            }

            for (int index = 0; index < 4; index++)
            {
                int next_x = cur.second % grid.size() + dx[index];
                int next_y = cur.second / grid.size() + dy[index];

                if (next_x < 0 || next_x >= grid.size() || 
                    next_y < 0 || next_y >= grid.size() ||
                    true == visited[next_x][next_y])
                {
                    continue;
                }

                visited[next_x][next_y] = true;
                q.push({std::max(grid[next_x][next_y], cur.first), 
                        next_y * grid.size() + next_x});
            }   
        }
        return -1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 783. 二叉搜索树节点最小距离
// 二叉搜索树 中序遍历 深度优先
// 给定一个二叉搜索树的根节点 root，返回树中任意两节点的差的最小值。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int minDiffInBST(TreeNode* root) {
        res = INT_MAX;
        pre = 0;
        dfs(root);
        return res;
    }

private:
    int res;
    int pre;

    void dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return;
        }

        dfs(root->left);
        if (pre)
        {
            res = std::min(res, root->val - pre);
        }
        pre = root->val;
        dfs(root->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 785. 判断二分图
// 二分图 染色问题 深度优先 递归 广度优先 队

class Solution1 {
public:
    bool isBipartite(vector<vector<int>>& graph) {
        std::vector<int> v_color(graph.size(), unknow);
        // 用for防止不连通图
        for (int index = 0; index <= graph.size() - 1; index++)
        {
            if (unknow == v_color[index]) // 还没染色
            {
                if (false == dfs(graph, index, white, v_color))
                {
                    return false;
                }
            }
        }
        return true;
    }

private:
    enum color_state {unknow, white, black};

    bool dfs(std::vector<std::vector<int>>& graph, 
             int parent, int color, std::vector<int>& v_color)
    {
        if (unknow != v_color[parent])
        {
            return color == v_color[parent];
        }

        v_color[parent] = color; // 当前节点着色

        for (auto child : graph[parent])
        {
            if (false == dfs(graph, child, 3 - color, v_color))
            {
                return false;
            }
        }

        return true;
    }
};

class Solution2 {
public:
    enum color_state {unknow, white, black};

    bool isBipartite(vector<vector<int>>& graph) {
        std::vector<int> v_color(graph.size(), unknow);
        std::queue<int> q;

        for (int index = 0; index <= graph.size() - 1; index++)
        {
            if (unknow != v_color[index])
            {
                continue; // 已经着色了，只要在下面判断就行
            }

            q.push(index); // 未着色点入队
            v_color[index] = white;

            while (false == q.empty())
            {
                int neighbor = v_color[q.front()] == white ? black : white;

                for (auto child : graph[q.front()]) // 当前队头的邻接点
                {
                    if (unknow == v_color[child])
                    {
                        v_color[child] = neighbor;
                        q.push(child);
                    }
                    else if (neighbor != v_color[child])
                    {
                        return false;
                    }
                }
                q.pop();
            }
        }
        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 787. K 站中转内最便宜的航班
// 广度优先 优先队列 最短路径 dijkstra 图 邻接矩阵

有 n 个城市通过 m 个航班连接。每个航班都从城市 u 开始，以价格 w 抵达 v。
现在给定所有的城市和航班，以及出发城市 src 和目的地 dst，你的任务是找到从 src 到 dst 最多经过 k 站中转的最便宜的价格。 如果没有这样的路线，则输出 -1。

class Solution {
public:
    int findCheapestPrice(int n, vector<vector<int>>& flights, int src, int dst, int K) {
        std::vector<std::vector<int>> v(n, std::vector<int>(n)); // 邻接矩阵

        for (auto flight : flights)
        {
            v[flight[0]][flight[1]] = flight[2];
        }

        std::priority_queue<std::vector<int>,
                            std::vector<std::vector<int>>,
                            greater<std::vector<int>>> q; // {cost, src, step}最小堆

        q.push({0, src, K + 1}); // 以cost排序
        int step = 0;
        int res = INT_MAX;

        while (false == q.empty())
        {
            int cost = q.top()[0]; 
            int cur = q.top()[1]; 
            int step = q.top()[2];
            q.pop();

            if (cur == dst)
            {
                return cost;
            }

            if (step > 0)
            {
                for (int index = 0; index <= n - 1; index++)
                {
                    if (v[cur][index])
                    {
                        q.push({cost + v[cur][index], index, step - 1}); 
                    }
                }
            }
        }
        return -1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="799"></div>

```c++

// 799. 香槟塔
// 动态规划

class Solution {
public:
    double champagneTower(int poured, int query_row, int query_glass) {
        constexpr int row_sum = 100;
        std::vector<std::vector<double>> vvDp(row_sum, std::vector<double>(row_sum));

        vvDp[0][0] = poured;

        for (int row = 0; row <= row_sum - 2; row++)
        {
            for (int col = 0; col <= row; col++) // 三角形数组
            {
                if (vvDp[row][col] > 1) // 才能继续往下倒酒
                {
                    vvDp[row + 1][col    ] += (vvDp[row][col] - 1) / 2.0; 
                    // 到了一杯分成两杯
                    vvDp[row + 1][col + 1] += (vvDp[row][col] - 1) / 2.0;
                }
            }
        }

        return std::min(1.0, vvDp[query_row][query_glass]);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 814. 二叉树剪枝
// 树 后序遍历 深度优先 递归

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* pruneTree(TreeNode* root) {
        if (nullptr == root)
        {
            return nullptr;
        }

        root->left = pruneTree(root->left);
        root->right = pruneTree(root->right);
        // 删掉0的叶子节点
        if (0 == root->val && nullptr == root->left && nullptr == root->right)
        {
            return nullptr;
        }   
        return root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 820. 单词的压缩编码
// 前缀 字符串

class Solution {
public:
    int minimumLengthEncoding(vector<string>& words) {
        // 翻转每一个f单词
        for (auto& word : words)
        {
            std::reverse(word.begin(), word.end());
        }
        // 对字符串排序（字典序）
        std::sort(words.begin(), words.end());

        int length = 0;

        for (int index = 0; 
             index <= static_cast <int>(words.size()) - 2; index++)
        {
            int cur_word_size = words[index].size();
            // 排在前面的肯定比在后面的短
            // 跳过前缀(当前字符串是下一个字符串的子串)
            if (words[index] == words[index + 1].substr(0, cur_word_size))
            {
                continue; 
            }

            length = length + cur_word_size + 1;
        }

        return length + words.back().size() + 1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 847. 访问所有节点的最短路径
// 广度优先 无向连通图 最短路 重边 队

class Solution {
public:
    int shortestPathLength(vector<vector<int>>& graph) {
        int n = graph.size();
        int end_state = (1 << n) - 1; // 11111111...(2)
        std::queue<std::pair<int, int>> q; // node=>state
        // 访问的状态有2^n种，即(1 << n)个
        std::vector<std::vector<bool>> 
        visited(n, std::vector<bool>(1 << n, false));
        // 所有节点入队并访问
        for (int index = 0; index <= n - 1; index++)
        {
            q.push({index, (1 << index)});
        }

        int step = 0;

        while (false == q.empty())
        {
            int len = q.size();

            while (len--)
            {
                auto node = q.front().first;
                auto state = q.front().second;
                q.pop();
                // 终止条件，肯定是最短路，
                // 因为是一层一层扩开，最先到的就是最短的
                if (state == end_state)
                {
                    return step;
                }

                if (true == visited[node][state])
                {
                    // 若这条(种)访问路径已经有了
                    continue;
                }
                else // 不然新增这种路径的情况
                {
                    visited[node][state] = true;
                }
                // 邻接点入队
                for (auto adj_node : graph[node])
                {
                    // state中增加这个节点
                    q.push({adj_node, state | (1 << adj_node)});
                }
            }
            step++;
        }
        return -1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 863. 二叉树中所有距离为 K 的结点
// 深度优先 广度优先 递归 邻接表 哈希表 图 二叉树 队

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> distanceK(TreeNode* root, TreeNode* target, int K) {
        dfs(nullptr, root); // 构建连接表
        std::vector<int> v_res;
        std::set<TreeNode*> s;
        std::queue<TreeNode*> q;

        int count = 0;

        q.push(target);
        s.insert(target);

        while (false == q.empty() && count <= K)
        {
            int len = q.size();
            while (len--)
            {
                if (count == K)
                {
                    v_res.push_back(q.front()->val);
                }

                for (auto node : adj_list[q.front()])
                {
                    if (1 == s.count(node))
                    {
                        continue;
                    }
                    q.push(node);
                    s.insert(node);
                }
                q.pop();
            }
            count++;
        }
        return v_res;
    }

private:
    std::unordered_map<TreeNode*, std::vector<TreeNode*>> adj_list;
    // map的好处就是通过target可以直接得出与它两连的节点
    void dfs(TreeNode* parent, TreeNode* child)
    {   
        // 构建邻接表
        if (parent)
        {
            adj_list[parent].push_back(child);
            adj_list[child].push_back(parent);
        }

        if (child->left)
        {
            dfs(child, child->left);
        }
        
        if (child->right)
        {
            dfs(child, child->right);
        }       
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 865. 具有所有最深结点的最小子树
// 深度优先 后序遍历 递归 二叉树
// 给定一个根为 root 的二叉树，每个结点的深度是它到根的最短距离。如果一个结点在整个树的任意结点之间具有最大的深度，则该结点是最深的。一个结点的子树是该结点加上它的所有后代的集合。返回能满足“以该结点为根的子树中包含所有最深的结点”这一条件的具有最大深度的结点。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* subtreeWithAllDeepest(TreeNode* root) {
        return dfs(root).res;
    }

    class CRes
    {
    public:
        int depth;
        TreeNode* res;

        CRes(int depth, TreeNode* res)
        : depth(depth), res(res)
        {}
    };

    CRes dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return CRes(0, nullptr);
        }

        CRes left_res = dfs(root->left);
        CRes right_res = dfs(root->right);

        int cur_depth = std::max(left_res.depth, right_res.depth) + 1;
        TreeNode* cur_res = (left_res.depth == right_res.depth) ? root :
                            (left_res.depth > right_res.depth) ?
                             left_res.res : right_res.res;

        return CRes(cur_depth, cur_res);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 872. 叶子相似的树
// 字符串 深度优先 递归 
// 请考虑一颗二叉树上所有的叶子，这些叶子的值按从左到右的顺序排列形成一个 叶值序列 。如果有两颗二叉树的叶值序列是相同，那么我们就认为它们是 叶相似 的。如果给定的两个头结点分别为 root1 和 root2 的树是叶相似的，则返回 true；否则返回 false 。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool leafSimilar(TreeNode* root1, TreeNode* root2) {
        std::string res1 = "";
        std::string res2 = "";
        dfs(root1, res1);
        dfs(root2, res2);
        return res1 == res2;
    }

private:
    void dfs(TreeNode* root, std::string& res)
    {
        if (nullptr == root)
        {
            return;
        }

        if (nullptr == root->left && nullptr == root->right)
        {
            res = res + std::to_string(root->val) + ' ';
        }

        dfs(root->left, res);
        dfs(root->right, res);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 889. 根据前序和后序遍历构造二叉树
// 深度优先 递归 二叉树
// 返回与给定的前序和后序遍历匹配的任何二叉树。
// LeetCode105 从前序与中序遍历序列构造二叉树
// LeetCode106 从中序与后序遍历序列构造二叉树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* constructFromPrePost(vector<int>& pre, vector<int>& post) {
        return dfs(pre, post, 0, (int)pre.size() - 1, 0, (int)post.size() - 1);
    }

    TreeNode* dfs(vector<int>& pre, vector<int>& post, 
                  int pre_start, int pre_end, 
                  int post_start, int post_end)
    {
        if (pre_start > pre_end || post_start > post_end)
        {
            return nullptr;
        }

        if (pre_start == pre_end)
        {
            return new TreeNode(pre[pre_start]);
        }

        TreeNode* root = new TreeNode(pre[pre_start]);
        // 去找左子树根节点，把后序遍历分开
        int left_index = post_start;
        while (pre[pre_start + 1] != post[left_index])
        {
            left_index++;
        }

        root->left = dfs(pre, post, 
                         pre_start + 1, pre_start + 1 + (left_index - post_start), 
                         post_start, left_index);
        root->right = dfs(pre, post, 
                          pre_start + 1 + (left_index - post_start) + 1, pre_end, 
                          left_index + 1, post_end - 1);
        return root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 894. 所有可能的满二叉树
// 分治 二叉树 后序遍历
// 满二叉树是一类二叉树，其中每个结点恰好有 0 或 2 个子结点。返回包含 N 个结点的所有可能满二叉树的列表。 答案的每个元素都是一个可能树的根结点。答案中每个树的每个结点都必须有 node.val=0。你可以按任何顺序返回树的最终列表。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<TreeNode*> allPossibleFBT(int N) {
        return dfs(1, N);
    }

private:
    std::vector<TreeNode*> dfs(int left, int right)
    {   
        std:vector<TreeNode*> res;

        if (left == right)
        {
            TreeNode* node = new TreeNode(0);
            res.push_back(node);
        }

        for (int root = left + 1; root <= right - 1; root += 2)
        {
            std::vector<TreeNode*> left_nodes = dfs(left, root - 1); // 左子树
            std::vector<TreeNode*> right_nodes = dfs(root + 1, right); // 右子树

            for (auto left_node : left_nodes)
            {
                for (auto right_node : right_nodes)
                {
                    TreeNode* new_root = new TreeNode(0);
                    new_root->left = left_node;
                    new_root->right = right_node;
                    res.push_back(new_root);
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 897. 递增顺序查找树
// 递归 深度优先 二叉树
// 给你一个树，请你 按中序遍历 重新排列树，使树中最左边的结点现在是树的根，并且每个结点没有左子结点，只有一个右子结点。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* increasingBST(TreeNode* root) {
        TreeNode* dummy = new TreeNode(0);
        res = dummy;
        dfs(root);
        return dummy->right;
    }

private:
    TreeNode* res;
    void dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return;
        }

        dfs(root->left);

        res->right = new TreeNode(root->val);
        res = res->right;
        
        dfs(root->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 912. 排序数组
// 双指针（相向指针） 快速排序

class Solution {
public:
    vector<int> sortArray(vector<int>& nums) {
        int n = nums.size();
        quickSort(nums, 0 ,nums.size() - 1, n);
        return nums;
    }

private:
    // 快排
    void quickSort(std::vector<int>& nums, int left, int right, int len)
    {
        if (left >= right)
        {
            return;
        }

        int pivot_pos = partition(nums, left, right);
        quickSort(nums, left, pivot_pos - 1, len);
        quickSort(nums, pivot_pos + 1, right, len);
    }

    int partition(std::vector<int>& nums, int left, int right)
    {
        int pivot = nums[left];
        while (left < right)
        {
            while (left < right && nums[right] >= pivot)
            {
                right--;
            }

            nums[left] = nums[right]; // 大的放左边,nums[left]保存在临时变量pivot中

            while (left < right && nums[left] <= pivot)
            {
                left++;
            }

            nums[right] = nums[left];
        }

        nums[left] = pivot;
        return left; // 划分点
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 930. 和相同的二元子数组
// 哈希表 前缀和
// 在由若干 0 和 1  组成的数组 A 中，有多少个和为 S 的非空子数组。

class Solution {
public:
    int numSubarraysWithSum(vector<int>& A, int S) {
        std::unordered_map<int, int> m; // sum => count
        m[0]++;
        int prefix = 0;
        int res = 0;

        for (int index = 0; index <= (int)A.size() - 1; index++)
        {
            prefix += A[index];
            res += m[prefix - S];
            m[prefix]++;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 938. 二叉搜索树的范围和
// 中序遍历 深度优先 二叉树 递归
// 给定二叉搜索树的根结点 root，返回 L 和 R（含）之间的所有结点的值的和。二叉搜索树保证具有唯一的值。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int rangeSumBST(TreeNode* root, int L, int R) {
        dfs(root, L, R);
        return res;
    }

private:
    int res;
    void dfs(TreeNode* root, int l, int r)
    {
        if (nullptr == root)
        {
            return;
        }

        dfs(root->left, l, r);
        if (l <= root->val && root->val <= r)
        {
            res += root->val;
        }
        dfs(root->right, l, r);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 945. 使数组唯一 的最小增量
// 排序 数组

class Solution {
public:
    int minIncrementForUnique(vector<int>& A) {
        /*
        {5,5,5,6}   res
        {5,6,5,6}   1
        {5,6,7,6}   3
        {5,6,7,8}   5
        */
        if (0 == A.size())
        {
            return 0;
        }
        
        std::sort(A.begin(), A.end());
        int res = 0;

        for (int index = 1; index <= A.size() - 1; index++)
        {
            if (A[index] <= A[index - 1])
            {
                res += A[index - 1] - A[index] + 1;
                A[index] = A[index - 1] + 1;
            }
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 951. 翻转等价二叉树
// 递归 深度递归 二叉树
// 我们可以为二叉树 T 定义一个翻转操作，如下所示：选择任意节点，然后交换它的左子树和右子树。只要经过一定次数的翻转操作后，能使 X 等于 Y，我们就称二叉树 X 翻转等价于二叉树 Y。编写一个判断两个二叉树是否是翻转等价的函数。这些树由根节点 root1 和 root2 给出。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool flipEquiv(TreeNode* root1, TreeNode* root2) {
        if (nullptr == root1 && nullptr == root2)
        {
            return true;
        }

        if (nullptr == root1 || nullptr == root2)
        {
            return false;
        }

        return root1->val == root2->val && 
               (flipEquiv(root1->left, root2->left) && flipEquiv(root1->right, root2->right) || 
                flipEquiv(root1->left, root2->right) && flipEquiv(root1->right, root2->left)); // 翻转
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 958. 二叉树的完全性检验
// 广度优先 树 队

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isCompleteTree(TreeNode* root) {
        if (nullptr == root)
        {
            return {};
        }

        std::vector<int> v_res;
        std::queue<TreeNode*> q;
        int flag = 0;

        q.push(root);

        while (false == q.empty())
        {
            int len = q.size();
            while (len--)
            {
                auto cur = q.front();
                q.pop();

                if (nullptr != cur)
                {
                    if (1 == flag)
                    {
                        return false;
                    }
                    // 放入空节点
                    q.push(cur->left);
                    q.push(cur->right);
                }
                else if (nullptr == cur)
                {
                    flag = 1; // 下一次不能有非空节点了
                }
            }
        }
        return true;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 965. 单值二叉树
// 深度优先 递归 二叉树
// 如果二叉树每个节点都具有相同的值，那么该二叉树就是单值二叉树。只有给定的树是单值二叉树时，才返回 true；否则返回 false。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isUnivalTree(TreeNode* root) {
        return dfs(root, root->val);
    }

private:
    bool dfs(TreeNode* root, int value)
    {
        if (nullptr == root)
        {
            return true;
        }
        return root->val == value && dfs(root->left, value) && dfs(root->right, value);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 971. 翻转二叉树以匹配先序遍历
// 深度优先 递归 二叉树 两层判断

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> flipMatchVoyage(TreeNode* root, vector<int>& voyage) {
        is_match = true;
        index = 0;
        dfs(root, voyage);
        if (false == is_match)
        {
            return {-1}; // 可能前面有转换过的，最后还是不符合，所以直接退出
        }
        return res;
    }

private:
    bool is_match;
    int index;
    std::vector<int> res; 
    void dfs(TreeNode* root, vector<int>& voyage)
    {
        if (nullptr == root)
        {
            return;
        }
        // 两层判断
        if (root->val != voyage[index]) // 交换后还不相等 或者 左边相等右边不相等
        {
            is_match = false;
            return;
        }
        // 下一个结点不匹配
        if (nullptr != root->left && root->left->val != voyage[index + 1])
        {
            TreeNode* temp = root->left;
            root->left = root->right;
            root->right = temp;
            res.push_back(root->val);
        }
        index++;

        dfs(root->left, voyage);
        dfs(root->right, voyage);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 974. 和可被 K 整除的子数组
// 前缀和 哈希表 子数组
// 给定一个整数数组 A，返回其中元素之和可被 K 整除的（连续、非空）子数组的数目。

class Solution {
public:
    int subarraysDivByK(vector<int>& A, int K) {
        std::unordered_map<int, int> m; // sum % K => count
        m[0]++;
        int prefix = 0;
        int res = 0;

        // 余数性质：(sum[j] − sum[i]) % K = sum[j] % K − sum[i] % K

        for (int index = 0; index <= (int)A.size() - 1; index++)
        {
            prefix += A[index];
            res += m[(prefix % K + K) % K]; // 处理负数
            m[(prefix % K + K) % K]++;
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 979. 在二叉树中分配硬币
// 后序遍历 深度优先 二叉树
// 给定一个有 N 个结点的二叉树的根结点 root，树中的每个结点上都对应有 node.val 枚硬币，并且总共有 N 枚硬币。在一次移动中，我们可以选择两个相邻的结点，然后将一枚硬币从其中一个结点移动到另一个结点。(移动可以是从父结点到子结点，或者从子结点移动到父结点。)。返回使每个结点上只有一枚硬币所需的移动次数。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int distributeCoins(TreeNode* root) {
        res = 0;
        dfs(root);
        return res;
    }

private:
    int res;

    int dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return 0;
        }

        int flow_left = dfs(root->left);
        int flow_right = dfs(root->right);

        res += std::abs(flow_left) + std::abs(flow_right);
        return flow_left + flow_right + root->val - 1; // 减去本身需要一个
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 988. 从叶结点开始的最小字符串
// 深度优先 递归 二叉树 前序遍历

给定一颗根结点为 root 的二叉树，树中的每一个结点都有一个从 0 到 25 的值，
分别代表字母 'a' 到 'z'：值 0 代表 'a'，值 1 代表 'b'，依此类推。
找出按字典序最小的字符串，该字符串从这棵树的一个叶结点开始，到根结点结束。
（小贴士：字符串中任何较短的前缀在字典序上都是较小的：例如，在字典序上 "ab" 比 "aba" 要小。叶结点是指没有子结点的结点。）

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    string smallestFromLeaf(TreeNode* root) {
        res = "zzz";
        dfs(root, "");
        return res;
    }

private:
    std::string res;

    void dfs(TreeNode* root, std::string buf)
    {
        if (nullptr == root)
        {
            return ;
        }

        buf += static_cast<char>('a' + root->val);

        if (nullptr == root->left && nullptr == root->right) // 叶子
        {
            std::reverse(buf.begin(), buf.end());
            res = std::min(res, buf);
            return ;
        }

        dfs(root->left, buf);
        dfs(root->right, buf);      
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 993. 二叉树的堂兄弟节点
// 深度优先 哈希表 递归 二叉树
// 在二叉树中，根节点位于深度 0 处，每个深度为 k 的节点的子节点位于深度 k+1 处。如果二叉树的两个节点深度相同，但父节点不同，则它们是一对堂兄弟节点。我们给出了具有唯一值的二叉树的根节点 root，以及树中两个不同节点的值 x 和 y。只有与值 x 和 y 对应的节点是堂兄弟节点时，才返回 true。否则，返回 false。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool isCousins(TreeNode* root, int x, int y) {
        dfs(nullptr, root);
        return m[x].first == m[y].first && m[x].second != m[y].second;
    }

private:
    std::unordered_map<int, std::pair<int, TreeNode*>> m; // node => {depth, parent}
    void dfs(TreeNode* parent, TreeNode* child)
    {
        if (nullptr == child)
        {
            return;
        }

        int cur_depth = nullptr == parent ? 1 : m[parent->val].first + 1;
        m.insert({child->val, {cur_depth, parent}});

        dfs(child, child->left);
        dfs(child, child->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1008. 先序遍历构造二叉树
// 深度优先 自顶向下递归 二叉树 前序遍历 分治

返回与给定先序遍历 preorder 相匹配的二叉搜索树（binary search tree）的根结点。
(回想一下，二叉搜索树是二叉树的一种，其每个节点都满足以下规则，对于 node.left 的任何后代，值总 < node.val，而 node.right 的任何后代，值总 > node.val。此外，先序遍历首先显示节点的值，然后遍历 node.left，接着遍历 node.right。）

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    TreeNode* bstFromPreorder(vector<int>& preorder) {
        return dfs(preorder, 0, preorder.size() - 1);
    }

private:
    TreeNode* dfs(vector<int>& preorder, int start, int end)
    {
        if (start > end)
        {
            return nullptr;
        }

        TreeNode* node = new TreeNode(preorder[start]);
        int index = start;

        while (index <= end && preorder[index] <= preorder[start])
        {
            index++;
        }

        node->left = dfs(preorder, start + 1, index - 1);
        node->right = dfs(preorder, index, end);
        return node;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1019. 链表中的下一个更大节点
// 链表 数组 单调栈 

给出一个以头节点 head 作为第一个节点的链表。链表中的节点分别编号为：node_1, node_2, node_3, ... 。
每个节点都可能有下一个更大值（next larger value）：对于 node_i，如果其 next_larger(node_i) 是 node_j.val，那么就有 j > i 且  node_j.val > node_i.val，而 j 是可能的选项中最小的那个。如果不存在这样的 j，那么下一个更大值为 0 。
返回整数答案数组 answer，其中 answer[i] = next_larger(node_{i+1}) 。
注意：在下面的示例中，诸如 [2,1,5] 这样的输入（不是输出）是链表的序列化表示，其头节点的值为 2，第二个节点值为 1，第三个节点值为 5 。

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> nextLargerNodes(ListNode* head) {
        std::vector<int> v;
        std::stack<int> s; // 存下标

        while (head)
        {
            v.push_back(head->val);
            head = head->next;
        }

        std::vector<int> res(v.size(), 0);

        for (int index = 0; index <= (int)v.size() - 1; index++)
        {
            while (false == s.empty() && v[index] > v[s.top()])
            {
                res[s.top()] = v[index];
                s.pop();
            }
            s.push(index);
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1022. 从根到叶的二进制数之和
// 前序遍历 自顶向下递归 深度优先 二叉树

给出一棵二叉树，其上每个结点的值都是 0 或 1 。每一条从根到叶的路径都代表一个从最高有效位开始的二进制数。例如，如果路径为 0 -> 1 -> 1 -> 0 -> 1，那么它表示二进制数 01101，也就是 13 。
对树上的每一片叶子，我们都要找出从根到该叶子的路径所表示的数字。
以 10^9 + 7 为模，返回这些数字之和。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int sumRootToLeaf(TreeNode* root) {
        res = 0;
        dfs(root, 0);
        return res;
    }

private:
    int res;

    void dfs(TreeNode* root, int state)
    {
        if (nullptr == root)
        {
            return;
        }

        state = (state << 1) + root->val;

        if (nullptr == root->left && nullptr == root->right)
        {
            res += state;
            return;
        }

        dfs(root->left, state);
        dfs(root->right, state);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1026. 节点与其祖先之间的最大差值
// 前序遍历 深度优先 自顶向下递归 

给定二叉树的根节点 root，找出存在于不同节点 A 和 B 之间的最大值 V，其中 V = |A.val - B.val|，且 A 是 B 的祖先。
（如果 A 的任何子节点之一为 B，或者 A 的任何子节点是 B 的祖先，那么我们认为 A 是 B 的祖先）

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int maxAncestorDiff(TreeNode* root) {
        res = 0;
        dfs(root, root->val, root->val);
        return res;
    }

private:
    int res;
    // 栈空间的设置成中间变量，结果设置成全局变量
    void dfs(TreeNode* root, int max_value, int min_value)
    {   
        if (nullptr == root)
        {
            return;
        }

        max_value = std::max(max_value, root->val);
        min_value = std::min(min_value, root->val);
        res = std::max(std::abs(max_value - min_value), res);

        dfs(root->left, max_value, min_value);
        dfs(root->right, max_value, min_value);
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="1035"></div>

```c++

// 1035. 不相交的线
// 动态规划 字符串匹配

class Solution {
public:
    int maxUncrossedLines(vector<int>& A, vector<int>& B) {
        std::vector<std::vector<int>> vvDp(A.size(), std::vector<int>(B.size(), 0));

        for (int row = 0; row <= A.size() - 1; row++)
        {
            for (int col = 0; col <= B.size() - 1; col++)
            {
                if (0 == row && 0 == col) // 初始条件
                {
                    vvDp[0][0] = (A[0] == B[0]) ? 1 : 0;
                }
                else if (0 == row) // 边界条件
                {
                    vvDp[row][col] = (A[row] == B[col]) ? 
                                     1 : vvDp[0][col - 1];
                }
                else if (0 == col) // 边界条件
                {
                    vvDp[row][col] = (A[row] == B[col]) ? 
                                     1 : vvDp[row - 1][0];
                }
                else if (0 < row && 0 < col) // 状态转移
                {
                    vvDp[row][col] = (A[row] == B[col]) ?          \
                                     (1 + vvDp[row - 1][col - 1]) :\ 
                                     std::max(vvDp[row][col - 1],  \
                                              vvDp[row - 1][col]);
                }
            }
        }

        return vvDp[A.size() - 1][B.size() - 1];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1081. 不同字符的最小子序列
// 字符串 单调栈

class Solution {
public:
    string smallestSubsequence(string text) {
        if (0 == text.size())
        {
            return text;
        }
        // 题设是不重复的序列，肯定没有aab和abb这种比较
        std::unordered_map<char, int> m;
        for (char c : text)
        {
            m[c]++;
        }

        std::string res; // 单调栈

        // 单调栈
        for (char c : text)
        {
            if (res.find(c) == std::string::npos) // 去重
            {
                while (res.size() && res.back() > c && m[res.back()] > 0) 
                {
                    // 每次取尽可能小的
                    // 当栈顶元素大于当前元素、有重复就能删
                    res.pop_back();
                }
                
                res += c;
            }

            m[c]--; // 后面c个数少一个
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1091. 二进制矩阵中的最短路径
// 广度优先 队 映射 方位数组 图

class Solution {
public:
    // 方向（方位）数组,八连通
    int dx[8] = {-1, -1, -1, 0, 0, 1, 1, 1};
    int dy[8] = {-1, 0, 1, -1, 1, -1, 0, 1};

    int shortestPathBinaryMatrix(vector<vector<int>>& grid) {
        int n = grid.size(); // 正方形
        if (1 == grid[0][0] || 1 == grid[n - 1][n - 1])
        {
            return -1;
        } 

        if (1 == n)
        {
            return 1;
        }

        // 二维映射到一维,把x,y信息保存到一个值中
        // i = x * n + y; x = i / n; y = i % n
        std::queue<int> q; // 存放当前节点
        std::vector<std::vector<int>> distance(n, std::vector<int>(n, 0));

        q.push(0); // [0, 0]
        distance[0][0] = 1;

        while (false == q.empty())
        {
            // 当前节点的横坐标和纵坐标
            int row = q.front() / n;
            int col = q.front() % n;
            // 遍历八个方向（当前节点的下一层）
            for (int index = 0; index <= 7; index++)
            {
                int x = row + dx[index];
                int y = col + dy[index];
                // 出口
                // 最短路径模板，找出口
                if (n - 1 == x && n - 1 == y)
                {
                    return distance[row][col] + 1;
                }

                if (x < 0 || x >= n || y < 0 || y >= n ||
                    1 == grid[x][y] || 0 != distance[x][y]) // 去重     
                {
                    continue;
                }

                distance[x][y] = distance[row][col] + 1;
                q.push(x * n + y);
            }
            q.pop();
        }
        return -1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1109. 航班预订统计
// 数学（变化量 增量）

class Solution {
public:
    vector<int> corpFlightBookings(vector<vector<int>>& bookings, int n) {
        if (0 == bookings.size())
        {
            return {};
        }

        std::vector<int> v(n, 0);
        // 算出相对于前一位的变化量delta
        for (int row = 0; row <= bookings.size() - 1; row++)
        {
            // 当前位置加上座位
            v[bookings[row][0] - 1] += bookings[row][2];
            // 之后航班减去u作为数
            if (n > bookings[row][1])
            {
                v[bookings[row][1]] -= bookings[row][2];
            }
        }

        // 加上前一位
        for (int index = 1; index <= n - 1; index++)
        {
            v[index] += v[index - 1];
        }

        return v;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1110. 删点成林
// 后序遍历 自底向上递归 深度优先

给出二叉树的根节点 root，树上每个节点都有一个不同的值。
如果节点值在 to_delete 中出现，我们就把该节点从树上删去，最后得到一个森林（一些不相交的树构成的集合）。
返回森林中的每棵树。你可以按任意顺序组织答案。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<TreeNode*> delNodes(TreeNode* root, vector<int>& to_delete) {
        for (auto d : to_delete)
        {
            m.insert(d);
        }

        if (m.find(root->val) == m.end())
        {
            res.push_back(root);
        }

        dfs(nullptr, root, is_root);
        return res;
    }

private:
    std::unordered_set<int> m;
    std::vector<TreeNode*> res;
    enum state{is_root, is_left, is_right};

    void dfs(TreeNode* parent, TreeNode* child, int state)
    {
        if (nullptr == child)
        {
            return;
        }

        dfs(child, child->left, is_left);
        dfs(child, child->right, is_right);

        if (m.find(child->val) != m.end())
        {
            if (child->left)
            {
                res.push_back(child->left);
            }

            if (child->right)
            {
                res.push_back(child->right);
            }

            if (is_left == state)
            {
                parent->left = nullptr;
            }

            if (is_right == state)
            {
                parent->right = nullptr;
            }
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1111. 有效括号的嵌套深度
// 栈

class Solution {
public:
    vector<int> maxDepthAfterSplit(string seq) {
        int depth = 0; // 维护一个深度,类似C语言栈的top下标
        std::vector<int> vRes; // 奇数深度放1，偶数深度放0

        for (auto c : seq)
        {
            if ('(' == c)
            {
                vRes.push_back(++depth % 2);
            }
            else if (')' == c)
            {
                vRes.push_back(depth-- % 2);
            }
        }

        return vRes;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1114. 按序打印
// 多线程 类

class Foo {
public:
    Foo() {
        m2.lock();
        m3.lock();
    }

    void first(function<void()> printFirst) {
        
        // printFirst() outputs "first". Do not change or remove this line.
        printFirst();
        m2.unlock();
    }

    void second(function<void()> printSecond) {
        m2.lock();
        // printSecond() outputs "second". Do not change or remove this line.
        printSecond();
        m2.unlock();
        m3.unlock();
    }

    void third(function<void()> printThird) {
        m3.lock();
        // printThird() outputs "third". Do not change or remove this line.
        printThird();
        m3.unlock();
    }

    void printFirst() { std::cout << "one" << std::endl; }
    void printSecond() { std::cout << "two" << std::endl; }
    void printThird() { std::cout << "three" << std::endl; }

private:
    std::mutex m2, m3;
};

int main()
{
    Foo foo;
    std::thread t1(&Foo::first, &foo);
    std::thread t2(&Foo::second, &foo);
    std::thread t3(&Foo::third, &foo);
    t1.join();
    t2.join();
    t3.join();
    return 0;
}

```
<div STYLE="page-break-after: always;"></div>

```c++

class Foo {
public:
    Foo() {
        flag_first = true;
        flag_second = false;
        flag_third = false;
    }

    void first(function<void()> printFirst) {
        std::unique_lock<std::mutex> l(m);
        v.wait(l, [this](){return this->flag_first;});
        // printFirst() outputs "first". Do not change or remove this line.
        printFirst();
        flag_first = false;
        flag_second = true;
        v.notify_all();
    }

    void second(function<void()> printSecond) {
        std::unique_lock<std::mutex> l(m);
        v.wait(l, [this](){return this->flag_second;});
        // printSecond() outputs "second". Do not change or remove this line.
        printSecond();
        flag_second = false;
        flag_third = true;
        v.notify_all();
    }

    void third(function<void()> printThird) {
        std::unique_lock<std::mutex> l(m);
        v.wait(l, [this](){return this->flag_third;});
        // printThird() outputs "third". Do not change or remove this line.
        printThird();
        flag_third = false;
        flag_first = true;
        v.notify_all();
    }

private:
    std::mutex m;
    std::condition_variable v;
    bool flag_first;
    bool flag_second;
    bool flag_third;
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1115. 交替打印FooBar
// 多线程 类

class FooBar {
private:
    int n;
    std::mutex m_foo;
    std::mutex m_bar;

public:
    FooBar(int n) {
        this->n = n;
        m_bar.lock();
    }

    void foo(function<void()> printFoo) {    
        for (int i = 0; i < n; i++) {
            m_foo.lock();
        	// printFoo() outputs "foo". Do not change or remove this line.
        	printFoo();
            m_bar.unlock();
        }
    }

    void bar(function<void()> printBar) {    
        for (int i = 0; i < n; i++) {
            m_bar.lock();
        	// printBar() outputs "bar". Do not change or remove this line.
        	printBar();
            m_foo.unlock();
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class FooBar {
private:
    int n;
    std::mutex m;
    std::condition_variable v;
    int flag;

public:
    FooBar(int n) {
        this->n = n;
        flag = 0;
    }

    void foo(function<void()> printFoo) {
        
        for (int i = 0; i < n; i++) {
            std::unique_lock<std::mutex> l(m);
            v.wait(l, [this](){return 0 == flag;});
        	// printFoo() outputs "foo". Do not change or remove this line.
        	printFoo();
            flag = 1;
            v.notify_all();
        }
    }

    void bar(function<void()> printBar) {
        
        for (int i = 0; i < n; i++) {
            std::unique_lock<std::mutex> l(m);
            v.wait(l, [this](){return 1 == flag;});
        	// printBar() outputs "bar". Do not change or remove this line.
        	printBar();
            flag = 0;
            v.notify_all();
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1116. 打印零与奇偶数
// 多线程 类

class ZeroEvenOdd {
private:
    int n;
    std::mutex m;
    std::condition_variable v;
    bool flag_zero;
    bool flag_even;
    bool flag_odd;

public:
    ZeroEvenOdd(int n) {
        this->n = n;
        flag_zero = true;
        flag_even = false;
        flag_odd = false;
    }

    // printNumber(x) outputs "x", where x is an integer.
    void zero(function<void(int)> printNumber) {
        for (int index = 0; index <= n - 1; index++)
        {
            std::unique_lock<std::mutex> l(m);
            v.wait(l, [this](){return flag_zero;});
            printNumber(0);
            flag_zero = false;
            if (0 == index % 2)
            {
                flag_odd = true;
            }
            else if (1 == index % 2)
            {
                flag_even = true;
            }

            v.notify_all();
        }
    }

    void even(function<void(int)> printNumber) {
        for (int index = 2; index <= n; index += 2)
        {
            std::unique_lock<std::mutex> l(m);
            v.wait(l, [this](){return !flag_zero && flag_even;});
            printNumber(index);
            flag_even = false;
            flag_zero = true;
            v.notify_all();
        }
    }

    void odd(function<void(int)> printNumber) {
        for (int index = 1; index <= n; index += 2)
        {
            std::unique_lock<std::mutex> l(m);
            v.wait(l, [this](){return !flag_zero && flag_odd;});
            printNumber(index);
            flag_odd = false;
            flag_zero = true;
            v.notify_all();
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1117. H2O 生成
// 多线程 类

class H2O {
public:
    H2O() {
        flag_o = 0;
        flag_h = 0;
    }

    void hydrogen(function<void()> releaseHydrogen) {
        std::unique_lock<std::mutex> l(m);
        v.wait(l, [this](){return 0 == flag_h || 1 == flag_h;});
        // releaseHydrogen() outputs "H". Do not change or remove this line.
        releaseHydrogen();
        flag_h++;
        if (3 == flag_h + flag_o)
        {
            flag_h = 0;
            flag_o = 0;
        }
        v.notify_all();
    }

    void oxygen(function<void()> releaseOxygen) {
        std::unique_lock<std::mutex> l(m);
        v.wait(l, [this](){return 0 == flag_o;});
        // releaseOxygen() outputs "O". Do not change or remove this line.
        releaseOxygen();
        flag_o++;
        if (3 == flag_h + flag_o)
        {
            flag_h = 0;
            flag_o = 0;
        }
        v.notify_all();
    }
private:
    std::mutex m;
    std::condition_variable v;
    int flag_h;
    int flag_o;
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1120. 子树的最大平均值
// 深度优先 后序遍历 树状DP 递归 二叉树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    double maximumAverageSubtree(TreeNode* root) {
        return dfs(root).max_ave;
    }

    class CRes
    {
    public:
        double max_ave;
        int count;
        int sum;
        double ave;

        CRes(double max_ave, int count, int sum, double ave)
        : max_ave(max_ave), count(count), sum(sum), ave(ave)
        {}
    };

    CRes dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return CRes(0, 0, 0, 0);
        }

        CRes left_res = dfs(root->left);
        CRes right_res = dfs(root->right);

        int cur_sum = left_res.sum + right_res.sum + root->val;
        int cur_count = left_res.count + right_res.count + 1;
        double cur_ave = (double)cur_sum / cur_count;
        double cur_max_ave = std::max(cur_ave, 
                                      std::max(left_res.max_ave, right_res.max_ave));

        return CRes(cur_max_ave, cur_count, cur_sum, cur_ave);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1122. 数组的相对排序
// 排序 数组

class Solution {
public:
    vector<int> relativeSortArray(vector<int>& arr1, vector<int>& arr2) {
        // 题目给的范围是arr1.length, arr2.length <= 1000
        // 且0 <= arr1[i], arr2[i] <= 1000
        // rank数组表示该值应当放置的位置
        // e.g. rank[2] = 0 表示2应该放在0号位
        std::vector<int> rank(1001,1001);

        for (int index = 0; index <= arr2.size() - 1; index++)
        {
            rank[arr2[index]] = index; // 反函数
        }

        std::sort(arr1.begin(), arr1.end(),
                  [&] (int a, int b)
                  {
                       return rank[a] != rank[b] ?
                             rank[a] < rank[b] :
                             a < b; // rank相等ab也实际上相等
                  });               // 或者是没有出现过的值，按升序

        return arr1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    vector<int> relativeSortArray(vector<int>& arr1, vector<int>& arr2) {
        // 计数排序
        std::vector<int> cnt(1001, 0);

        for (int a : arr2)
        {
            cnt[a]++; // 统计arr2个数
        }

        for (int num = 0; num < 1001; num++)
        {
            if (cnt[num])
            {
                cnt[num] = 0; // 清空
            }
            else // 把arr1中剩余部分存到arr2中
            {
                arr2.push_back(num);
            }
        }

        for (int a : arr1)
        {
            cnt[a]++; // 统计arr1元素个数
        }

        for (int num = 0, index = 0; num < 1001; num++)
        {
            // 把arr2数组中有的值，找到它的个数
            while (cnt[arr2[num]]--)
            {
                // 把arr2那个值放cnt[arr2[num]]次
                // 覆盖arr1
                arr1[index++] = arr2[num];
            }
        }
        return arr1;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1123. 最深叶节点的最近公共祖先
// 后序遍历 自顶向上递归 自底向下递归 二叉树 深度优先

给你一个有根节点的二叉树，找到它最深的叶节点的最近公共祖先。
回想一下：
叶节点 是二叉树中没有子节点的节点
树的根节点的 深度 为 0，如果某一节点的深度为 d，那它的子节点的深度就是 d+1
如果我们假定 A 是一组节点 S 的 最近公共祖先，S 中的每个节点都在以 A 为根节点的子树中，且 A 的深度达到此条件下可能的最大值。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* lcaDeepestLeaves(TreeNode* root) {
        dfs(root, 0);
        return res;
    }

private:
    int max_depth;
    TreeNode* res;

    int dfs(TreeNode* root, int depth)
    {
        if (nullptr == root) // 多算一层
        {
            return depth - 1; // 当前路径最大深度，自上而下递归
        }

        int res_left = dfs(root->left, depth + 1); // 左边最大深度
        int res_right = dfs(root->right, depth + 1); // 右边最大深度

        if (res_left == res_right && res_left >= max_depth)
        {
            max_depth = res_left;
            res = root;
        }

        return std::max(res_left, res_right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1130. 叶值的最小代价生成树
// 单调栈 二叉树 

给你一个正整数数组 arr，考虑所有满足以下条件的二叉树：
每个节点都有 0 个或是 2 个子节点。
数组 arr 中的值与树的中序遍历中每个叶节点的值一一对应。（知识回顾：如果一个节点有 0 个子节点，那么该节点为叶节点。）
每个非叶节点的值等于其左子树和右子树中叶节点的最大值的乘积。
在所有这样的二叉树中，返回每个非叶节点的值的最小可能总和。这个和的值是一个 32 位整数。

class Solution {
public:
    int mctFromLeafValues(vector<int>& arr) {
        int res = 0;
        std::stack<int> s;
        s.push(INT_MAX);

        // 大的值尽可能少乘几次，也就是先乘小值
        for (int& cur : arr)
        {
            while (s.top() <= cur) // 当前元素更大
            {
                int drop = s.top();
                s.pop();
                res += drop * std::min(s.top(), cur); // drop 在 [s.top(), cur] 中间，选小的乘
            }
            s.push(cur);
        }

        while (s.size() > 2)
        {
            int drop = s.top();
            s.pop();
            res += drop * s.top();
        }

        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

<div id="1143"></div>

```c++

// 1143. 最长公共子序列
// 动态规划 滚动数组

class Solution {
public:
    int longestCommonSubsequence(string text1, string text2) {
        std::vector<std::vector<int>> 
        dp(text1.length(), std::vector<int>(text2.length(), 0));

        for (int row = 0; row <= text1.length() - 1; row++)
        {
            for (int col = 0; col <= text2.length() - 1; col++)
            {
                if (0 == row && 0 == col)
                {
                    dp[0][0] = (text1[0] == text2[0]) ? 1 : 0;
                }
                else if (0 == row)
                {
                    dp[0][col] = (text1[0] == text2[col]) ? 1 : dp[0][col - 1];
                } 
                else if (0 == col)
                {
                    dp[row][0] = (text1[row] == text2[0]) ? 1 : dp[row - 1][0];
                }
                else
                {
                    dp[row][col] = (text1[row] == text2[col]) ? 
                                   dp[row - 1][col - 1] + 1 :
                                   std::max(dp[row - 1][col], dp[row][col - 1]);
                }
            }
        }
        return dp[text1.length() - 1][text2.length() - 1];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

class Solution {
public:
    int longestCommonSubsequence(string text1, string text2) {
        std::vector<std::vector<int>> 
        dp(2, std::vector<int>(text2.length(), 0));

        for (int row = 0; row <= text1.length() - 1; row++)
        {
            for (int col = 0; col <= text2.length() - 1; col++)
            {
                if (0 == row && 0 == col)
                {
                    dp[0][0] = (text1[0] == text2[0]) ? 1 : 0;
                }
                else if (0 == row)
                {
                    dp[0][col] = (text1[0] == text2[col]) ? 
                                 1 : dp[0][col - 1];
                } 
                else if (0 == col)
                {
                    dp[row % 2][0] = (text1[row] == text2[0]) ? 
                                     1 : dp[(row + 1) % 2][0];
                }
                else
                {
                    dp[row % 2][col] = (text1[row] == text2[col]) ? 
                                   dp[(row + 1) % 2][col - 1] + 1 :
                                   std::max(dp[(row + 1) % 2][col], 
                                            dp[row % 2][col - 1]);
                }
            }
        }
        return dp[(text1.length() - 1) % 2][text2.length() - 1];
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1145. 二叉树着色游戏
// 深度优先 递归 树 公共祖先模型

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */

// 树之所以为树，区别于图是因为树没有环，
// 也就是说两个节点间只有唯一通路，
// 那么这条通路只有三种情况，A是B的祖先，B是A的祖先，AB有最近公共祖先，
// 相当于把整棵树分成三段，一是A割据的部分，二是B割据的部分，三是AB中间争夺的部分，
// 争夺的最后结果只能导致三种情况：A变成B的祖宗，A变成B的孙子，AB有最近公共祖先，
// 那么题目基本就是求双方割据的势力范围哪个来的大，
// 设置的全局变量，实际就是场外裁判，在统计势力范围
class Solution {
public:
    bool btreeGameWinningMove(TreeNode* root, int n, int x) {
        // 本质上当前节点要抢红色x的父节点或者子节点
        // 问题就演变成求其最大子树是否大于红色总数
        // 即以红色为分界点，把树分成三部分：
        // 1.红色以上的祖先节点和他们的堂兄弟节点
        // 2.红色左边以下的子孙节点
        // 3.红色右边以下的子孙节点
        // 求他们哪个大
        // 那么分成三种情况：
        // 1.有拐点的（即红蓝有公共祖先，即蓝色取其父节点）
        // 2.左子树（即红是蓝的祖先，即红色是蓝色的父节点）
        // 3.右子树（即红是蓝的祖先，即红色是蓝色的父节点）
        dfs(root, n, x);
        return (blue_max > n - blue_max);
    }

private:
    // 求节点数目
    int blue_max = 0;

    int dfs(TreeNode* root, const int n, const int x)
    {
        if (nullptr == root)
        {
            return 0;
        }
        // 树深模型
        int left_sum = dfs(root->left, n, x);
        int right_sum = dfs(root->right, n, x);
        // 当遇到红色节点，开始计算
        // 上面计算的左右子树即为当前节点的左右子树数量
        if (x == root->val)
        {
            // 蓝色取红色父节点，那么左右子树都为红色，(n-左右-当前)就是蓝色
            blue_max = std::max(blue_max, n - left_sum - right_sum - 1);
            // 蓝色取红色子节点，那么取左右子树最大的，都涂成红色
            blue_max = std::max(blue_max, left_sum);
            blue_max = std::max(blue_max, right_sum);
        }

        return left_sum + right_sum + 1; // 加上当前节点
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1195. 交替打印字符串
// 多线程 类

class FizzBuzz {
private:
    int n;
    std::mutex m;
    std::condition_variable v;
    int flag;

public:
    FizzBuzz(int n) {
        this->n = n;
        flag = 1;
    }

    // printFizz() outputs "fizz".
    void fizz(function<void()> printFizz) {
        std::unique_lock<std::mutex> l(m);
        while (flag <= n) 
        {
            v.wait(l, [this](){ return flag > n || (!(flag % 3) && (flag % 5));}); 
            if (flag <= n) 
            {
                printFizz();
            }
            flag++;
            v.notify_all();
        }
    }

    // printBuzz() outputs "buzz".
    void buzz(function<void()> printBuzz) {
        std::unique_lock<std::mutex> l(m);
        while (flag <= n) 
        {
            v.wait(l, [this](){ return flag > n || ((flag % 3) && !(flag % 5));}); 
            if (flag <= n) 
            {
                printBuzz();
            }
            flag++;
            v.notify_all();
        }
    }

    // printFizzBuzz() outputs "fizzbuzz".
	void fizzbuzz(function<void()> printFizzBuzz) {
        std::unique_lock<std::mutex> l(m);
        while (flag <= n) 
        {
            v.wait(l, [this](){ return flag > n || (!(flag % 3) && !(flag % 5));}); 
            if (flag <= n) 
            {
                printFizzBuzz();
            }
            flag++;
            v.notify_all();
        }
    }

    // printNumber(x) outputs "x", where x is an integer.
    void number(function<void(int)> printNumber) {
        std::unique_lock<std::mutex> l(m);
        while (flag <= n) 
        {
            v.wait(l, [this](){ return flag > n || ((flag % 3) && (flag % 5));}); 
            if (flag <= n) 
            {
                printNumber(flag);
            }
            flag++;
            v.notify_all();
        }        
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1226. 哲学家进餐
// 互斥量 锁

class DiningPhilosophers {
private:
    std::mutex mutexs[5];

public:
    DiningPhilosophers() {
        
    }

    void wantsToEat(int philosopher,
                    function<void()> pickLeftFork,
                    function<void()> pickRightFork,
                    function<void()> eat,
                    function<void()> putLeftFork,
                    function<void()> putRightFork) {
		int left = philosopher;
        int right = (philosopher + 1) % 5;

        // lock()，调用线程将锁住该互斥量。线程调用该函数会发生下面 3 种情况：
        // (1). 如果该互斥量当前没有被锁住，则调用线程将该互斥量锁住，直到调用 unlock之前，该线程一直拥有该锁。
        // (2). 如果当前互斥量被其他线程锁住，则当前的调用线程被阻塞住。
        // (3). 如果当前互斥量被当前调用线程锁住，则会产生死锁(deadlock)。
        // lock_guard对象管理Mutex对象，Mutex对象已被当前线程锁住。
        std::lock(mutexs[left], mutexs[right]);
        std::lock_guard<std::mutex> lock_left(mutexs[left], std::adopt_lock);
        std::lock_guard<std::mutex> lock_right(mutexs[right], std::adopt_lock);

        pickLeftFork();
        pickRightFork();
        eat();
        putLeftFork();
        putRightFork();
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1245. 树的直径
// 图 深度优先 自顶向下递归 

给你这棵「无向树」，请你测算并返回它的「直径」：这棵树上最长简单路径的 边数。
我们用一个由所有「边」组成的数组 edges 来表示一棵无向树，其中 edges[i] = [u, v] 表示节点 u 和 v 之间的双向边。
树上的节点都已经用 {0, 1, ..., edges.length} 中的数做了标记，每个节点上的标记都是独一无二的。

class Solution {
public:
    int treeDiameter(vector<vector<int>>& edges) {
        std::vector<std::vector<int>> g(edges.size() + 1);
        for (auto e : edges)
        {
            g[e[0]].push_back(e[1]);
            g[e[1]].push_back(e[0]);
        }
        std::vector<bool> visited(edges.size() + 1, false);

        res = 0;
        start = 0;
        // 从随意一个顶点开始，找到最长边，从那个边的端点再找一次最长边
        dfs(g, visited, 0, 0);
        visited.assign(edges.size() + 1, false);
        dfs(g, visited, start, 0);
        return res;
    }

private:
    int res;
    int start;

    void dfs(std::vector<std::vector<int>>& g, std::vector<bool>& visited,
             int cur, int state)
    {
        visited[cur] = true;

        if (cur != start && 1 == g[cur].size()) // 不是开头那个
        {
            if (state >= res)
            {
                res = state;
                start = cur;
            }
            return;
        }

        for (auto child : g[cur])
        {
            if (false == visited[child])
            {
                dfs(g, visited, child, state + 1);
            }
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1249. 移除无效的括号
// 栈

class Solution {
public:
    string minRemoveToMakeValid(string s) {
        if (0 == s.size())
        {
            return s;
        }

        std::stack<int> s_index;

        for (int index = 0; index <= s.size() - 1; index++)
        {
            if ('(' == s[index])
            {
                s_index.push(index);
            }
            else if (')' == s[index])
            {
                if (false == s_index.empty()) // 如果栈里有元素就出栈
                {
                    s_index.pop();
                }
                else if (true == s_index.empty())
                {
                    s[index] = '#';
                }
            }
        }

        while (!s_index.empty())
        {
            int temp_index = s_index.top();
            s[temp_index] = '#';
            s_index.pop();
        }

        s.erase(std::remove(s.begin(), s.end(), '#'), s.end());

        return s;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1254. 统计封闭岛屿的数目
// 深度优先 递归 回溯 连通分量

class Solution {
public:
    int closedIsland(vector<vector<int>>& grid) {
        if (0 == grid.size())
        {
            return 0;
        }

        int res = 0;
        int valid = 1;

        for (int row = 0; row <= grid.size() - 1; row++)
        {
            for (int col = 0; col <= grid[0].size() - 1; col++)
            {
                if (0 == grid[row][col])
                {
                    valid = 1;
                    dfs(grid, row, col, valid); // 岛的其余部分清零
                    res += valid;
                }
            }
        }
        return res;
    }
    
private:
    void dfs(vector<vector<int>>& grid, int row, int col, int& valid)
    {
        if (row < 0 || row >= grid.size() || 
            col < 0 || col >= grid[0].size())
        {
            valid = 0;
            return;
        }

        if (1 == grid[row][col])
        {
            return;
        }

        grid[row][col] = 1; // 对岛清零, 沉岛

        dfs(grid, row + 1, col, valid);
        dfs(grid, row - 1, col, valid);
        dfs(grid, row, col + 1, valid);
        dfs(grid, row, col - 1, valid);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1302. 层数最深叶子节点的和
// 广度优先 二叉树 队

给你一棵二叉树，请你返回层数最深的叶子节点的和。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int deepestLeavesSum(TreeNode* root) {
        std::queue<TreeNode*> q;
        q.push(root);
        int depth = 1;

        while (false == q.empty())
        {
            int len = q.size();
            int sum = 0;
            int is_bottom = true;

            while (len--)
            {
                auto cur = q.front();
                sum += cur->val;
                q.pop();

                if (cur->left)
                {
                    is_bottom = false;
                    q.push(cur->left);
                }

                if (cur->right)
                {
                    is_bottom = false;
                    q.push(cur->right);
                }
            }

            if (is_bottom)
            {
                return sum;
            }

            depth++;
        }
        return 0;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1305. 两棵二叉搜索树中的所有元素
// 深度优先 中序遍历 递归 二叉树

给你 root1 和 root2 这两棵二叉搜索树。
请你返回一个列表，其中包含 两棵树 中的所有整数并按 升序 排序。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<int> getAllElements(TreeNode* root1, TreeNode* root2) {
        std::vector<int> res;
        dfs(root1);
        dfs(root2);
        for (auto& val : s)
        {
            res.push_back(std::move(val));
        }
        return res;
    }

private:
    std::multiset<int> s;

    void dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return;
        }

        dfs(root->left);
        s.insert(root->val);
        dfs(root->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1315. 祖父节点值为偶数的节点和
// 深度优先 二叉树 自顶向下递归

给你一棵二叉树，请你返回满足以下条件的所有节点的值之和：
该节点的祖父节点的值为偶数。（一个节点的祖父节点是指该节点的父节点的父节点。）
如果不存在祖父节点值为偶数的节点，那么返回 0 。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int sumEvenGrandparent(TreeNode* root) {
        sum = 0;
        dfs(root);
        return sum;
    }

private:
    int sum;

    void dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return;
        }

        if (0 == root->val % 2)
        {
            if (root->left && root->left->left)
            {
                sum += root->left->left->val;
            }

            if (root->left && root->left->right)
            {
                sum += root->left->right->val;
            }

            if (root->right && root->right->left)
            {
                sum += root->right->left->val;
            }

            if (root->right && root->right->right)
            {
                sum += root->right->right->val;
            }
        }
        
        dfs(root->left);
        dfs(root->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1325. 删除给定值的叶子节点
// 树 深度优先 后序遍历

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    TreeNode* removeLeafNodes(TreeNode* root, int target) {
        if (nullptr == root)
        {
            return nullptr;
        }

        root->left = removeLeafNodes(root->left, target);
        root->right = removeLeafNodes(root->right, target);

        // 叶子节点
        if (target == root->val && !root->left && !root->right)
        {
            return nullptr;
        }

        return root;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1339. 分裂二叉树的最大乘积
// 二叉树 后序遍历 前缀和 自底向上递归 深度优先

给你一棵二叉树，它的根为 root 。请你删除 1 条边，使二叉树分裂成两棵子树，且它们子树和的乘积尽可能大。
由于答案可能会很大，请你将结果对 10^9 + 7 取模后再返回。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int maxProduct(TreeNode* root) {
        res = 0;
        int sum = dfs(root);
        for (auto s : prefix_sum)
        {
            res = std::max(res, (long long)(sum - s) * s);
        }
        return (res % (long long)(1e9 + 7));
    }

private:
    long long res;
    std::vector<int> prefix_sum;

    int dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return 0;
        }

        int res_left = dfs(root->left);
        int res_right = dfs(root->right);
        root->val += res_left + res_right;
        prefix_sum.push_back(root->val);
        return root->val;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1367. 二叉树中的列表
// 二叉树 链表 深度优先 双递归

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSubPath(ListNode* head, TreeNode* root) {
        if (nullptr == head)
        {
            return true;
        }

        if (nullptr == root)
        {
            return false;
        }

        return dfs(head, root) || 
               isSubPath(head, root->left) || 
               isSubPath(head, root->right);
    }

private:
    bool dfs(ListNode* list, TreeNode* root)
    {
        if (nullptr == list)
        {
            return true;
        }

        if (nullptr == root)
        {
            return false;
        }

        if (list->val != root->val)
        {
            return false;
        }

        return dfs(list->next, root->left) || 
               dfs(list->next, root->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1372. 二叉树中的最长交错路径
// 深度优先 后序遍历 自底向上递归 二叉树

给你一棵以 root 为根的二叉树，二叉树中的交错路径定义如下：
选择二叉树中 任意 节点和一个方向（左或者右）。
如果前进方向为右，那么移动到当前节点的的右子节点，否则移动到它的左子节点。
改变前进方向：左变右或者右变左。
重复第二步和第三步，直到你在树中无法继续移动。
交错路径的长度定义为：访问过的节点数目 - 1（单个节点的路径长度为 0 ）。
请你返回给定树中最长 交错路径 的长度。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int longestZigZag(TreeNode* root) {
        res = 0;
        dfs(root, is_left);
        return res;
    }

private:
    enum state{is_left, is_right};
    int res;

    int dfs(TreeNode* root, int state)
    {
        if (nullptr == root)
        {
            return 0;
        }

        int res_left = dfs(root->left, is_left);
        int res_right = dfs(root->right, is_right);

        res = std::max(res, res_left);
        res = std::max(res, res_right);

        if (state == is_left)
        {
            return res_right + 1;
        }
        else // if (state == is_right)
        {
            return res_left + 1;
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1373. 二叉搜索子树的最大键值和
// 深度优先 后序遍历 树状DP 递归 二叉树

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int maxSumBST(TreeNode* root) {
        return dfs(root).max_sum;
    }

    class CRes
    {
    public:
        bool isBst;
        int sum;
        int max_sum;
        int min_val;
        int max_val;

        CRes(bool isBst, int sum, int max_sum, int min_val, int max_val)
        : isBst(isBst), sum(sum), max_sum(max_sum), min_val(min_val), max_val(max_val)
        {}
    };

    CRes dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return CRes(true, 0, 0, INT_MAX, INT_MIN);
        }

        CRes left_res = dfs(root->left);
        CRes right_res = dfs(root->right);

        bool cur_is_bst = left_res.isBst && right_res.isBst &&
                          left_res.max_val < root->val &&
                          root->val < right_res.min_val;
        
        int cur_min = std::min(root->val, left_res.min_val);
        int cur_max = std::max(root->val, right_res.max_val);
        int cur_sum = left_res.sum + right_res.sum + root->val;
        int pre_max_sum = std::max(left_res.max_sum, right_res.max_sum);
        int cur_max_sum =std::max(cur_sum, pre_max_sum);

        if (false == cur_is_bst)
        {
            return CRes(false, 0, pre_max_sum, INT_MAX, INT_MIN);
        }
        
        return CRes(true, cur_sum, cur_max_sum, cur_min, cur_max);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1379. 找出克隆二叉树中的相同节点
// 二叉树 深度优先 自顶向下递归 自底向上递归

给你两棵二叉树，原始树 original 和克隆树 cloned，以及一个位于原始树 original 中的目标节点 target。
其中，克隆树 cloned 是原始树 original 的一个 副本 。
请找出在树 cloned 中，与 target 相同 的节点，并返回对该节点的引用（在 C/C++ 等有指针的语言中返回 节点指针，其他语言返回节点本身）。
注意：
你 不能 对两棵二叉树，以及 target 节点进行更改。
只能 返回对克隆树 cloned 中已有的节点的引用。
进阶：如果树中允许出现值相同的节点，你将如何解答？

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */

class Solution {
public:
    TreeNode* getTargetCopy(TreeNode* original, TreeNode* cloned, TreeNode* target) {
        res = nullptr;
        dfs(original, cloned, target);
        return res;
    }

private:
    TreeNode* res;

    void dfs(TreeNode* original, TreeNode* cloned, TreeNode* target)
    {
        if (nullptr == original)
        {
            return ;
        }

        if (original == target)
        {
            res = cloned;
        }

        dfs(original->left, cloned->left, target);
        dfs(original->right, cloned->right, target);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */

class Solution {
public:
    TreeNode* getTargetCopy(TreeNode* original, TreeNode* cloned, TreeNode* target) {
        res = nullptr;
        dfs(original, cloned, target);
        return res;
    }

private:
    TreeNode* res;

    void dfs(TreeNode* original, TreeNode* cloned, TreeNode* target)
    {
        if (nullptr == original)
        {
            return ;
        }

        dfs(original->left, cloned->left, target);
        dfs(original->right, cloned->right, target);
        
        if (original == target) // 自底向上
        {
            res = cloned;
        }
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1430. 判断给定的序列是否是二叉树从根到叶的路径
// 二叉树 前序遍历 自顶向下递归 深度优先 数组

给定一个二叉树，我们称从根节点到任意叶节点的任意路径中的节点值所构成的序列为该二叉树的一个 “有效序列” 。检查一个给定的序列是否是给定二叉树的一个 “有效序列” 。
我们以整数数组 arr 的形式给出这个序列。从根节点到任意叶节点的任意路径中的节点值所构成的序列都是这个二叉树的 “有效序列” 。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    bool isValidSequence(TreeNode* root, vector<int>& arr) {
        is_valid = false;
        dfs(root, arr, 0);
        return is_valid;
    }

private:
    int is_valid;

    void dfs(TreeNode* root, vector<int>& arr, int index)
    {
        if (nullptr == root && index == arr.size())
        {
            return;
        }

        if (nullptr == root || index == arr.size())
        {
            return;
        }

        if (nullptr == root->left && nullptr == root->right 
            && index == arr.size() - 1 && root->val == arr[index])
        {
            is_valid = true;
            return;
        }

        if (root->val != arr[index])
        {
            return;
        }

        dfs(root->left, arr, index + 1);
        dfs(root->right, arr, index + 1);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1448. 统计二叉树中好节点的数目
// 深度优先 递归 二叉树 栈

给你一棵根为 root 的二叉树，请你返回二叉树中好节点的数目。
「好节点」X 定义为：从根到该节点 X 所经过的节点中，没有任何节点的值大于 X 的值。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int goodNodes(TreeNode* root) {
        res = 0;
        dfs(root, INT_MIN);
        return res;
    }

private:
    int res;

    void dfs(TreeNode* root, int state_max)
    {
        if (nullptr == root)
        {
            return;
        }

        if (root->val >= state_max)
        {
            res++;
            state_max = root->val; // 利用栈的特性
        }

        dfs(root->left, state_max);
        dfs(root->right, state_max);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1443. 收集树上所有苹果的最少时间
// 深度优先 图 二叉树 自底向上递归 后序遍历

给你一棵有 n 个节点的无向树，节点编号为 0 到 n-1 ，它们中有一些节点有苹果。通过树上的一条边，需要花费 1 秒钟。你从 节点 0 出发，请你返回最少需要多少秒，可以收集到所有苹果，并回到节点 0 。
无向树的边由 edges 给出，其中 edges[i] = [fromi, toi] ，表示有一条边连接 from 和 toi 。除此以外，还有一个布尔数组 hasApple ，其中 hasApple[i] = true 代表节点 i 有一个苹果，否则，节点 i 没有苹果。

class Solution {
public:
    int minTime(int n, vector<vector<int>>& edges, vector<bool>& hasApple) {
        std::vector<std::vector<int>> g(n);
        for (auto e : edges)
        {
            g[e[0]].push_back(e[1]);
            g[e[1]].push_back(e[0]);
        }
        std::vector<bool> visited(n, false);
        return dfs(g, hasApple, visited, 0);
    }

private:
    int dfs(std::vector<std::vector<int>>& g, std::vector<bool>& hasApple, 
            std::vector<bool>& visited, int cur)
    {
        visited[cur] = true;
        int count = 0;

        for (auto child : g[cur])
        {
            if (false == visited[child])
            {
                int count_res = dfs(g, hasApple, visited, child);

                if (count_res || hasApple[child])
                {
                    count = count + count_res + 2;
                }
            }
        }
        return count;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1457. 二叉树中的伪回文路径
// 位运算 深度优先 二叉树 自顶向下递归

给你一棵二叉树，每个节点的值为 1 到 9 。我们称二叉树中的一条路径是 「伪回文」的，当它满足：路径经过的所有节点值的排列中，存在一个回文序列。
请你返回从根到叶子节点的所有路径中 伪回文 路径的数目。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int pseudoPalindromicPaths (TreeNode* root) {
        res = 0;
        dfs(root, 0);
        return res;
    }

private:
    int res;

    void dfs(TreeNode* root, int state)
    {
        if (nullptr == root)
        {
            return;
        }

        state ^= (1 << root->val);

        if (nullptr == root->left && nullptr == root->right)
        {   
            if (0 == state || 0 == (state & (state - 1))) // -1表示把最右边1后面的全置1
            {
                res++;
            }
            return;
        }

        dfs(root->left, state);
        dfs(root->right, state);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1466. 重新规划路线
// 有向图 广度优先 二叉树 队

n 座城市，从 0 到 n-1 编号，其间共有 n-1 条路线。因此，要想在两座不同城市之间旅行只有唯一一条路线可供选择（路线网形成一颗树）。去年，交通运输部决定重新规划路线，以改变交通拥堵的状况。
路线用 connections 表示，其中 connections[i] = [a, b] 表示从城市 a 到 b 的一条有向路线。
今年，城市 0 将会举办一场大型比赛，很多游客都想前往城市 0 。
请你帮助重新规划路线方向，使每个城市都可以访问城市 0 。返回需要变更方向的最小路线数。
题目数据 保证 每个城市在重新规划路线方向后都能到达城市 0 。

class Solution {
public:
    int minReorder(int n, vector<vector<int>>& connections) {
        std::vector<std::vector<std::pair<int, int>>> g(n); // graph

        for (auto connection : connections)
        {
            g[connection[0]].push_back({connection[1], 1}); // [0]=>[1],存在这个方向
            g[connection[1]].push_back({connection[0], -1}); // [1]=>[0],不存在这个方向
        }

        std::queue<int> q;
        std::vector<bool> visited(n, false);
        int res = 0;

        q.push(0);

        while (false == q.empty())
        {
            int cur = q.front();
            q.pop();
            visited[cur] = true;

            for (auto child : g[cur])
            {
                if (false == visited[child.first])
                {
                    if (1 == child.second)
                    {
                        res++;
                    }
                    q.push(child.first);
                }
            }
        }
        return res;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1469. 寻找所有的独生节点
// 前序遍历 自顶向下递归 二叉树 深度优先

二叉树中，如果一个节点是其父节点的唯一子节点，则称这样的节点为 “独生节点” 。二叉树的根节点不会是独生节点，因为它没有父节点。
给定一棵二叉树的根节点 root ，返回树中 所有的独生节点的值所构成的数组 。数组的顺序 不限 。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<int> getLonelyNodes(TreeNode* root) {
        dfs(root);
        return res;
    }

private:
    std::vector<int> res;

    void dfs(TreeNode* root)
    {
        if (nullptr == root)
        {
            return;
        }

        if (nullptr == root->left && nullptr != root->right)
        {
            res.push_back(root->right->val);
        }

        if (nullptr != root->left && nullptr == root->right)
        {
            res.push_back(root->left->val);
        }

        dfs(root->left);
        dfs(root->right);
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 1530. 好叶子节点对的数量
// 深度优先 递归 后序遍历 分治 二叉树

给你二叉树的根节点 root 和一个整数 distance 。
如果二叉树中两个 叶 节点之间的 最短路径长度 小于或者等于 distance ，那它们就可以构成一组 好叶子节点对 。
返回树中 好叶子节点对的数量 。

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int countPairs(TreeNode* root, int distance) {
        res = 0;
        dfs(root, distance);
        return res;
    }

private:
    int res;

    std::vector<int> dfs(TreeNode* root, int distance)
    {
        if (nullptr == root)
        {
            return {};
        }

        if (nullptr == root->left && nullptr == root->right)
        {
            return {0};
        }

        auto left_res = dfs(root->left, distance);
        auto right_res = dfs(root->right, distance);

        std::vector<int> v;

        for (auto left_len : left_res)
        {
            if (left_len + 1 > distance)
            {
                continue;
            }

            v.push_back(left_len + 1);
        }

        for (auto right_len : right_res)
        {
            if (right_len + 1 > distance)
            {
                continue;
            }
            v.push_back(right_len + 1);
        }

        for (auto left_len : left_res)
        {
            for (auto right_len : right_res)
            {
                res += (left_len + right_len + 2 <= distance);
            }
        }

        return v;
    }
};

```
<div STYLE="page-break-after: always;"></div>

```c++

// 面试题 03.05. 栈排序
// 最小栈 栈 类

class SortedStack {
public:
    SortedStack() {

    }
    
    void push(int val) {
        while (!s_ascend.empty() && s_ascend.top() > val)
        {
            s_descend.push(s_ascend.top());
            s_ascend.pop();
        }

        while (!s_descend.empty() && s_descend.top() < val)
        {
            s_ascend.push(s_descend.top());
            s_descend.pop();
        }

        s_descend.push(val);
    }
    
    void pop() {
        while (!s_ascend.empty())
        {
            s_descend.push(s_ascend.top());
            s_ascend.pop();
        }

        if (s_descend.empty())
        {
            return;
        }

        s_descend.pop();
    }
    
    int peek() {
        while (!s_ascend.empty())
        {
            s_descend.push(s_ascend.top());
            s_ascend.pop();
        }

        if (s_descend.empty())
        {
            return -1;
        }

        return s_descend.top();
    }
    
    bool isEmpty() {
        return s_descend.empty() && s_ascend.empty();
    }
private:
    // 输入值作为划分点
    // 比它大的就放在原栈中
    // 比它小的就放在辅助栈中
    std::stack<int> s_descend; // 原栈降序
    std::stack<int> s_ascend; // 辅助栈升序,栈底存放最小值
};

/**
 * Your SortedStack object will be instantiated and called as such:
 * SortedStack* obj = new SortedStack();
 * obj->push(val);
 * obj->pop();
 * int param_3 = obj->peek();
 * bool param_4 = obj->isEmpty();
 */

```
<div STYLE="page-break-after: always;"></div>

```c++
 
```
