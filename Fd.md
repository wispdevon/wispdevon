![[./Tools#^9d86fe|Tools > ^9d86fe]]

Fd is a command-line utility for Unix-based system like Linux, MacOS, and BSD. It is similar to the `find` command in these systems but offers some conveniences and upgrades to the traditional `find`.

Some of its features Include:

1. Convenient Syntax: Fd utilizes a more intuitive and straightforward syntax compared to 'find'. For example, with 'fd', you can type 'fd pattern' instead of 'find -name pattern'.

2. Colored Output: Fd highlights the search terms in the output which can make navigating the results easier for the user.

3. Ignoring Hidden and Ignored Files: Fd ignores hidden and ignored files by default (though they can be included with a simple flag if needed). This can result in a cleaner search result.

4. Smart Case: The search with fd is case insensitive by default, but becomes sensitive if your pattern includes an uppercase character.

5. Parallel Operations: Fd executes commands in parallel which can make it faster than 'find'.

6. Supports Regex: Fd has built in support for regular expressions, a powerful tool for pattern matching.

7. Unicode Support: Fd supports Unicode, making it possible to search for files and folders with non-ASCII characters.

Even though it's different than `find`, the goal of `fd` is similar: providing a way to find files and directories on your file system. But it does so with a simpler syntax and more user-friendly features.
