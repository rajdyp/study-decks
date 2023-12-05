Perform below multi line assignment in a single line.

``` md
n = 0.125
m = "abc"
z = False
```

??? example annotate "Solution"

    ``` py
    n, m, z = 0.125, "abc", False
    print(n)
    print(m)
    print(z)
    ```

<!-- end of question -->


String exercises

``` md
- Create a string `Hello, World!`
- Just print `,` from the string
- Get the characters from position 2 to position 5 (not included)
- Print only the characters at even position
- Replace `"H"` with `"Y"`
- Split 'My name is Rajdeep' to a list of substrings
- Remove any whitespace from beginning or end of `" Hello, World! "`
- Combine a list of strings `["ab", "cd", "ef"]` with an empty string delimitor
```

??? example annotate "Solution"

    ``` py
    print('\nCreate a string `Hello, World!`')
    my_str = "Hello, World!"
    print(my_str)

    print('\nJust print `,` from the string')
    print(my_str[5])

    print('\nGet the characters from position 2 to position 5 (not included)')
    print(my_str[1:5])

    print('\nPrint only the characters at even position')
    print(my_str[::2])

    print('\nReplace `"H"` with `"Y"`')
    print(my_str.replace("H", "Y"))

    print('\nSplit "My name is Rajdeep" to a list of substrings')
    my_str = "My name is Rajdeep"
    print(my_str.split())

    print('\nRemove any whitespace from beginning or end of `" Hello, World! "`')
    my_str = " Hello, World! "
    print(my_str.strip())

    print('\nCombine a list of strings `["ab", "cd", "ef"]` with an empty string delimitor')
    str_list = ["ab", "cd", "ef"]
    print(" ".join(str_list))
    ```

<!-- end of question -->


List exercises

``` md
- Create a list of names containing `"John", "Alice", "Sarah", "Rajna", "George"` using list() constructor.
- Print number of items in the list
- Print `"Alice", "Sarah", Rajna` from the list
- Print `"George"` from the list
- Print `"Sarah"` from the list
- Replace `"John"` with `"Jenny"`
- Replace `"Jenny", "Alice"` with `"John", "Maya"`
- Add `"Simon"`
- Add `"Betty"` before `"Sarah"`
- Remove `"John"`
- Remove element at index 2
- Remove the last element
- Add list `fruits = ["apple", "banana", "cherry", "kiwi"]` to names
- From `fruits = ["apple", "banana", "cherry", "kiwi"]`, print all fruits that has `a` in its name using list comprehension
- Reverse the order of list `fruits = ["apple", "banana", "cherry", "kiwi"]`
- Sort list numerically `num = [100, 50, 65, 82, 23]`
- Sort above list in descending order
- Join fruits and num list to a new list
- Clear fruits list
- Delete num list
```

??? example annotate "Solution"

    ``` py
    print('\n1. Create a list of names containing `"John", "Alice", "Sarah", "Rajna", "George"` using list() constructor\n')
    names = list(("John", "Alice", "Sarah", "Rajna", "George"))
    print(names)

    names = list()
    names.append("John")
    names.append("Alice")
    names.append("Sarah")
    names.append("Rajna")
    names.append("George")
    print(names)

    print('\n2. Print number of items in the list\n')
    print(f"No of items: {len(names)}")

    print('\n3. Print `"Alice", "Sarah", Rajna` from the list\n')
    print(names[1:4])

    print('\n4. Print `"George"` from the list\n')
    print(names[-1])

    print('\n5. Print `"Sarah"` from the list\n')
    print(names[2])

    print('\n6. Replace `"John"` with `"Jenny"`\n')
    names[0] = "Jenny"
    print(names)

    print('\n7. Replace `"Jenny", "Alice"` with `"John", "Maya"`\n')
    names[0:2] = ["John", "Maya"]
    print(names)

    print('\n8. Add `"Simon"`\n')
    names.append("Simon")
    print(names)

    print('\n9. Add `"Betty"` before `"Sarah"`\n')
    names.insert(2, "Betty")
    print(names)

    print('\n10. Remove `"John"`\n')
    names.remove("John")
    print(names)

    print('\n11. Remove element at index 2\n')
    names = ['Maya', 'Betty', 'Sarah', 'Rajna', 'George', 'Simon']
    names.remove(names[2])
    print(names)

    names = ['Maya', 'Betty', 'Sarah', 'Rajna', 'George', 'Simon']
    names.pop(2)
    print(names)

    print('\n12. Remove the last element\n')
    names.pop()
    print(names)

    print('\n13. Add list `fruits = ["apple", "banana", "cherry", "kiwi"]` to names\n')
    fruits = ["apple", "banana", "cherry", "kiwi"]
    names.extend(fruits)
    print(names)

    print('\n14. From `fruits = ["apple", "banana", "cherry", "kiwi"]`, print all fruits that has `a` in its name using list comprehension\n')
    fruits = ["apple", "banana", "cherry", "kiwi"]
    print([fruit for fruit in fruits if "a" in fruit])

    print('\n15. Reverse the order of list `fruits = ["apple", "banana", "cherry", "kiwi"]`\n')
    fruits.reverse()
    print(fruits)

    fruits.sort(reverse=True)
    print(fruits)

    print('\n16. Sort list numerically `num = [100, 50, 65, 82, 23]`\n')
    num = [100, 50, 65, 82, 23]
    num.sort()
    print(num)

    print('\n17. Sort above list in descending order\n')
    num = [100, 50, 65, 82, 23]
    num.sort(reverse=True)
    print(num)

    print('\n18. Join fruits and num list to a new list\n')
    new_list = fruits + num
    print(new_list)

    fruits.extend(num)
    print(fruits)

    print('\n19. Clear fruits list\n')
    print(fruits)
    fruits.clear()
    print(fruits)

    print('\n20. Delete num list\n')
    print(num)
    del num
    print(num)
    ```

<!-- end of question -->
