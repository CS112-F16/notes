Style Guidelines
================

Your code is expected to follow the guidelines below. If you do not follow these guidelines you will receive a deduction on your assignment score:

1. Use lower-case letters to begin a variable or method name.
2. Use upper-case letters to begin a class name.
3. Use camelCase not_underscores.
4. Be consistent with spacing. `variable= new Something()` is not good. `variable = new Something()` is much better.
 - Put one space after each comma in a parameter list.
 - Put one space on either side of a binary operator.
 - Do not put spaces immediately after a left parenthesis or before a right parenthesis.
 - Do not put spaces before a semicolon.
 - Put one space before a left parenthesis, except before an empty parameter list.
5. Be consistent with your use of the `this` keyword, especially in constructors.
6. Use try-with-resources.
7. Document all of the methods and classes you create.
 - Every source code file should contain a header block of documentation providing basic information about the contents and the author.
 - Each class and interface, and each method in a class, should have a small header block that describes its role.
 - Use in-line documentation as appropriate to clearly describe complex logic.
 - Don't wait until a program is finished to insert documentation. As pieces of your program are completed, comment them appropriately.
8. Use private data members unless there is a good reason to do otherwise.
9. Make sure use proper indentation in all classes.
 - In Sublime, you can create a key binding that will allow you to select all text and use the binding to indent the selected code properly. 
 - I use ```command-i``` for indentation and created the binding as follows: ```Sublime Text > Preferences > Key Bindings - User```. Add the text below and save:
`
[
    { "keys": ["command+i"], "command": "reindent"} 
]
`
10. Do not catch unchecked exceptions unless there is a very good reason. Instead, try to use conditionals appropriately to avoid unchecked (e.g., NullPointer) exceptions.
11. Do not replicate code unless there is a very good reason.
