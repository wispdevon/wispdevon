![[./Tools#^c5510f|Tools > ^c5510f]]

Zoxide is a fast alternative to 'cd', which tracks the directories you use most frequently. It was inspired by z and zz programs, and is completely written in Rust. It helps you to navigate quickly between directories you have previously accessed.

To use Zoxide, follow these steps:

1. Install it: You can install Zoxide using a package manager like Homebrew for macOS (brew install zoxide) or Scoop or Chocolately for Windows. Linux users can use the cargo package manager to install Zoxide (cargo install zoxide).

2. Integrate it: Zoxide needs to be integrated into your shell before you can use it. You may use the 'eval' method (eval "$(zoxide init bash)").

    Replace 'bash' with whatever shell you're using e.g. fish, zsh, etc.

3. Use the 'z' command: Once you've installed and integrated Zoxide, you can start using the 'z' command to navigate around directories smartly.

    Just type 'z' followed by a portion of the directory path and Zoxide will send you to the most frequently visited directory that matches the input.

4. Update database: Zoxide updates its internal database every time you visit a directory which makes it smarter over time as you traverse your file structure.

For example, if you frequently navigate to a directory at /Users/username/Documents/Projects/zoxide, you can just type 'z zoxid' (or even just a part of the directory name) in the terminal and press Enter, Zoxide will automatically take you to that directory.

In summary, Zoxide helps you navigate your file system in an efficient manner by keeping track of your most used directories and allowing you to jump to them with just a piece of the directory’s name. Thus, it saves your time by reducing the number of keystrokes you need to enter.
