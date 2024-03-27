---
quickshare-date: 2024-03-24T01:35:47.000Z
quickshare-url: https://noteshare.space/note/clu4fkugh991801mwvt4emafc#LVM3wwKMkVx+OUoS+RIp8zQ8/8FoyCLCBB9kmkLey+Y
slug: coding
datetime: 2024-03-23 01:23
summary: Python, JavaScript, and C# code snippets are provided along with a short explanation. A random password generator and a palindrome checker are showcased in the code examples.
tags:
  - Python
  - JavaScript
  - C#
cover_image_url: 
gists:
  - id: 9fd40b6f3e75ad6679486909b9b1edab
    url: https://gist.github.com/wispdevon/9fd40b6f3e75ad6679486909b9b1edab
    createdAt: 2024-03-23T18:39:15Z
    updatedAt: 2024-03-23T18:39:15Z
    filename: Coding.md
    isPublic: true
---

```python
print("Hello World!")
```

```javascript
console.log("hi");
```

```ts
const data: void = console.log("hi")
```

```cs
using System;

class HelloWorld
{
    static void Main()
    {
        Console.WriteLine("Hello, World!");
    }
}
```

```cpp
#include <iostream>

int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```

Here is a simple Python code that generates a random password with a specified length:

```python

import random

import string


def generate_password(length):

    characters = string.ascii_letters + string.digits + string.punctuation

    password = ''.join(random.choice(characters) for i in range(length))

    return password


password_length = 12

random_password = generate_password(password_length)

print("Random password:", random_password)

```

```chat
< ChatGPT | This code will create a random password of length 12 that contains a mix of uppercase and lowercase letters, digits, and special characters. Feel free to modify the `password_length` variable to change the length of the generated password.
```

Write a short javascript snippet that will do something cool

Sure, here's a cool JavaScript snippet – A basic palindrome checker function.

```javascript
function isPalindrome(str) {
	str = str.replace(/[^a-z0-9+]+/gi, "").toLowerCase();

	let reverseStr = str.split("").reverse().join("");

	return str === reverseStr;
}

console.log(isPalindrome("Is this a palindrome? Racecar."));
```

This is a simple palindrome checker. A palindrome is a word, phrase, number, or other sequences of characters that reads the same forward and backward, ignoring spaces, punctuation, and capitalization.

When you pass the phrase "Is this a palindrome? Racecar." to this function, it will ignore all non-alphanumeric characters, turn all alphabets to lower case, and then check if it's the same as the reverse of the string, printing out `true` or `false`.

However, if you need more complex or specific JavaScript snippets, several resources comprise various JavaScript snippets, such as

Image of a cartoony wisp like in Terraria wisp in a bottle



