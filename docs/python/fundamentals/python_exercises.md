Perform below multi line assignment in a single line.

``` yaml
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

``` yaml
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
