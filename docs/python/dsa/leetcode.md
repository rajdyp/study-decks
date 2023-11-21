### 1. Contains duplicate
```yaml
Given an integer array nums, return true if any value appears at least twice in the array, and return false if every
element is distinct.

Example 1:
Input: nums = [1,2,3,1]
Output: true

Example 2:
Input: nums = [1,2,3,4]
Output: false

Example 3:
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true

Constraints:
- 1 <= nums.length <= 105
- -109 <= nums[i] <= 109
```

<details>
<summary> Solution </summary>

```python
# O(n)
def containsDuplicate(nums):
    myset = set()
    for n in nums:
        if n in myset:
            return True
        myset.add(n)
    return False
    
nums1 = [1,2,3,1]
print(containsDuplicate(nums1))

nums2 = [1,2,3,4]
print(containsDuplicate(nums2))

nums3 = [1,1,1,3,3,4,3,2,4,2]
print(containsDuplicate(nums3))
```

</details>


### 2. Valid anagram
```yaml
Given two strings s and t, return true if t is an anagram of s, and false otherwise.
An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all
the original letters exactly once.

Example 1:
Input: s = "anagram", t = "nagaram"
Output: true

Example 2:
Input: s = "rat", t = "car"
Output: false
 
Constraints:
- 1 <= s.length, t.length <= 5 * 104
- s and t consist of lowercase English letters.
```

<details>
<summary> Solution </summary>

```yaml
Conditions for anagram:
- Both string (s and t) length should be equal
- Number of individual characters should be equal
```
```python
# O(n)
def is_anagram(s, t):
    if len(s) != len(t):
        return False
    
    s_count = {}
    t_count = {}

    for char in s:
        s_count[char] = s_count.get(char, 0) + 1

    for char in t:
        t_count[char] = t_count.get(char, 0) + 1

    return s_count == t_count

s = "anagram"
t = "nagaram"
print(is_anagram(s, t))
```

</details>


### 3. Two sum
```yaml
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to
target. You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.

Example 1:
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].

Example 2:
Input: nums = [3,2,4], target = 6
Output: [1,2]

Example 3:
Input: nums = [3,3], target = 6
Output: [0,1]
 
Constraints:
- 2 <= nums.length <= 104
- -109 <= nums[i] <= 109
- -109 <= target <= 109
- Only one valid answer exists.
```

<details>
<summary> Solution </summary>

```yaml
- Hashmap (key "num", value "index")
- Take difference of target and "num"
- Check if the difference value exists in hashmap
```
```python
# O(n)
def two_sum(nums, target):
    mydict = {}
    for i, n in enumerate(nums):
        diff = target - n
        if diff in mydict:
            return [mydict[diff], i]
        mydict[n] = i
    return []
    
nums = [2,15,11,7]
target = 9
print(two_sum(nums, target))
```

</details>


### 4. Valid palindrome
```yaml
A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all
non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and
numbers. Given a string s, return true if it is a palindrome, or false otherwise.

Example 1:
Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.

Example 2:
Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.

Example 3:
Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.

Constraints:
- 1 <= s.length <= 2 * 105
- s consists only of printable ASCII characters.
```

<details>
<summary> Solution </summary>

```yaml
# Extra memory

- Filter alphanumeric characters
- Compare "s" with reverse of "s"
```
```python
# O(n)
def is_palindrome(s):
    temp_s = ""
    for char in s:
        if char.isalnum():
            temp_s += char.lower()

    if temp_s == temp_s[::-1]:
        return True
    return False

s = "A man, a plan, a canal: Panama"
print(is_palindrome(s))

s = "race a car"
print(is_palindrome(s))

s = " "
print(is_palindrome(s))
```

```yaml
# Two pointer solution

- Take two pointers "left" and "right"
- If char is not alphanumeric than just increment the pointer
- Compare "left" character with "right" character
- Increment the pointer till while condition is met
```
```python
# O(n)
def is_palindrome(s):
    left, right = 0, len(s) - 1

    while left < right:
        while left < right and not s[left].isalnum():
            left += 1
        while left < right and not s[right].isalnum():
            right -= 1
        if s[left].lower() != s[right].lower():
            return False
        left += 1
        right -= 1
    return True

s = "A man, a plan, a canal: Panama"
print(is_palindrome(s))

s = "race a car"
print(is_palindrome(s))

s = " "
print(is_palindrome(s))
```
</details>


### 5. Best time to buy and sell stock
```yaml
You are given an array prices where prices[i] is the price of a given stock on the ith day. You want to maximize
your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.
Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

Example 1:
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

Example 2:
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.

Constraints:
- 1 <= prices.length <= 105
- 0 <= prices[i] <= 104
```

<details>
<summary> Solution </summary>

```python
# O(n)
def max_profit(prices):
    if len(prices) == 0:
        return 0
    
    max_profit = 0
    min_price = prices[0]

    for price in prices:
        if price < min_price:
            min_price = price
        else:
            max_profit = max(max_profit, price - min_price)
    return max_profit

prices = [7,1,5,3,6,4]
print(max_profit(prices))

prices = [7,6,4,3,1]
print(max_profit(prices))

prices = []
print(max_profit(prices))
```

</details>


### 6. Valid parentheses
```yaml
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:
- Open brackets must be closed by the same type of brackets.
- Open brackets must be closed in the correct order.
- Every close bracket has a corresponding open bracket of the same type.

Example 1:
Input: s = "()"
Output: true

Example 2:
Input: s = "()[]{}"
Output: true

Example 3:
Input: s = "(]"
Output: false

Constraints:
- 1 <= s.length <= 104
- s consists of parentheses only '()[]{}'.
```

<details>
<summary> Solution </summary>

```python
# O(n)
def is_valid(s):
    stack = []      # store open bracket
    mymap = {")": "(", "]": "[", "}": "{"}

    for char in s:
        if char in mymap:
            if len(stack) > 0:
                top = stack.pop()
            if top != mymap[char]:
                return False
        else:
            stack.append(char)
        
    if len(stack) == 0:
        return True
    return False

# Example usage
s1 = "()"
print(is_valid(s1))

s2 = "()[]{}"
print(is_valid(s2))

s3 = "(]"
print(is_valid(s3))

s4 = "("
print(is_valid(s4))

s5 = "(({[]}))"
print(is_valid(s5))
```

</details>


### 7. Binary search
```yaml
Given an array of integers nums which is sorted in ascending order, and an integer target, write a function to
search target in nums. If target exists, then return its index. Otherwise, return -1. You must write an algorithm
with O(log n) runtime complexity.

Example 1:
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4

Example 2:
Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1

Constraints:
- 1 <= nums.length <= 104
- -10**4 < nums[i], target < 10**4
- All the integers in nums are unique.
- nums is sorted in ascending order.
```

<details>
<summary> Solution </summary>

```python
# linear search
# O(n)
def search(nums, target):
    for i in range(len(nums)):
        if nums[i] == target:
            return i
    return -1

n1 = [-1,0,3,5,9,12]
t1 = 9
print(search(n1, t1))

n2 = [-1,0,3,5,9,12]
t2 = 2
print(search(n2, t2))
```

```python
# O(log n)
def search(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

n1 = [-1,0,3,5,9,12]
t1 = 9
print(search(n1, t1))

n2 = [-1,0,3,5,9,12]
t2 = 2
print(search(n2, t2))
```

</details>

