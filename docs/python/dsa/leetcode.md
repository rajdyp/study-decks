### [1. Contains duplicate](https://leetcode.com/problems/contains-duplicate/)

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


### [2. Valid anagram](https://leetcode.com/problems/valid-anagram/)

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


### [3. Two sum](https://leetcode.com/problems/two-sum/)

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


### [4. Valid palindrome](https://leetcode.com/problems/valid-palindrome/)

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


### [5. Best time to buy and sell stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

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


### [6. Valid parentheses](https://leetcode.com/problems/valid-parentheses/)

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


### [7. Binary search](https://leetcode.com/problems/binary-search/)

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

