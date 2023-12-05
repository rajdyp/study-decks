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

- Create a string `Hello, World!`
- Just print `,` from the string
- Get the characters from position 2 to position 5 (not included)
- Print only the characters at even position
- Replace `"H"` with `"Y"`
- Split 'My name is Rajdeep' to a list of substrings
- Remove any whitespace from beginning or end of `" Hello, World! "`
- Combine a list of strings `["ab", "cd", "ef"]` with an empty string delimitor

??? example annotate "Solution"

    ``` py
    print('\n1. Create a string `Hello, World!`')
    my_str = "Hello, World!"
    print(my_str)


    print('\n2. Just print `,` from the string')
    print(my_str[5])


    print('\n3. Get the characters from position 2 to position 5 (not included)')
    print(my_str[1:5])


    print('\n4. Print only the characters at even position')
    print(my_str[::2])


    print('\n5. Replace `"H"` with `"Y"`')
    print(my_str.replace("H", "Y"))


    print('\n6. Split "My name is Rajdeep" to a list of substrings')
    my_str = "My name is Rajdeep"
    print(my_str.split())


    print('\n7. Remove any whitespace from beginning or end of `" Hello, World! "`')
    my_str = " Hello, World! "
    print(my_str.strip())


    print('\n8. Combine a list of strings `["ab", "cd", "ef"]` with an empty string delimitor')
    str_list = ["ab", "cd", "ef"]
    print(" ".join(str_list))
    ```

<!-- end of question -->


List exercises

- Create a list of names containing `"John", "Alice", "Sarah", "Rajna", "George"` using list() constructor
- Print number of items in the list
- Print `"Alice", "Sarah", Rajna` from the list
- Retrieve `"George"`
- Retrieve `"Sarah"`
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


    print('\n4. Retrieve `"George"`\n')
    print(names[-1])


    print('\n5. Retrieve `"Sarah"`\n')
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


Tuple exercises

- Create a tuple of names`"John", "Sarah", "Alice"` using tuple() constructor
- Create a tuple of single name `"Maya"`
- Add name to names
- Retrieve `"Sarah"`
- Add `"Simon"`
- Rmove `"John"`
- Is there any workaround for add and remove?
- Unpack tuple `fruits = ("apple", "banana", "kiwi")` as per their color and print their values
- Delete fruits tuple

??? example annotate "Solution"

    ``` py
    print('\n1. Create a tuple of names`"John", "Sarah", "Alice"` using tuple() constructor\n')
    names = tuple(("John", "Sarah", "Alice"))
    print(names)


    print('\n2. Create a tuple of single name `"Maya"`\n')
    name = ("Maya",)
    print(name)


    print('\n3. Add name to names\n')
    names += name
    print(names)


    print('\n4. Retrieve `"Sarah"`\n')
    print(names[1])


    print('\n5. Add `"Simon"``\n')
    print("Cannot add items to a Tuple as it is immutable\n")


    print('\n6. Rmove `"John"`\n')
    print("Cannot remove items from a Tuple as it is immutable\n")


    print('\nIs there any workaround for add and remove?\n')
    print(names)
    names = list(names)
    names.append("Simon")
    print(tuple(names))

    names = list(names)
    names.remove("Simon")
    print(tuple(names))


    print('\n7. Unpack tuple `fruits = ("apple", "banana", "cherry")` as per their color and print their values\n')
    fruits = ("apple", "banana", "cherry")
    green, yellow, red = fruits
    print(f"Green : {green}")
    print(f"Yellow : {yellow}")
    print(f"Red : {red}")


    print('\n8. Delete fruits tuple\n')
    print(fruits)
    del fruits
    print(fruits)
    ```

<!-- end of question -->
