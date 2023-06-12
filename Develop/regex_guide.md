# Regular Expressions Guide - How to use Regex? 

This content shows you what is regex and how to use regex for beginners of regex.

## Summary

Regular expressions, often abbreviated as regex, are a method used to match and manipulate patterns of characters within a string. They are composed of a combination of characters that form a pattern and optional flags. 

Here's an example of a regular expression pattern for validating email addresses:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

 Let's try to break down the components of this pattern:
  
  * `^`: Anchors the pattern to the start of the string.
  * `([a-z0-9_\.-]+)`: Matches one or more lowercase letters, digits, underscores, periods, or hyphens in the username part of the email address.
  * `@`: Matches the "@" symbol.
  * `([\da-z\.-]+)`: Matches one or more digits, lowercase letters, periods, or hyphens in the domain name part of the email address.
  * `\.`: Matches a literal period (dot) character.
  * `([a-z\.]{2,6})`: Matches two to six lowercase letters or periods in the top-level domain part of the email address.
  * `$`: Anchors the pattern to the end of the string.

Here are some examples of strings that would match this pattern:

 * test@example.com
 * user.name1234@subdomain.domain.co.au

Regex can be used to ensure that the entered email address follows a valid format, helping to prevent incorrect or malicious inputs. By using regexs to perform format checks, you can enhance both the usability and security of your web applications.

Many programming languages provide support for regular expressions, allowing developers to implement various functionalities using them.

However, it is not uncommon for individuals to have questions or uncertainties about regular expressions.

This guide help clarify any doubts and explain the mechanisms of regular expressions so that you can effectively utilize them.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
In regular expressions, there are metacharacters used to indicate the beginning or end of a string, as well as word boundaries. These metacharacters that represent the position of characters are called anchors.

The metacharacter `^` (caret) is used in regex to represent the beginning of a string.
 When `^` is placed at the beginning of a regular expression pattern, it specifies that the following pattern should match only if it occurs at the start of the string.  

**Example Regex ( Matching a `Y` ):**
````
let reg = /^Y/;

console.log(reg.test('Yamada Hanako')); // true
console.log(reg.test('Yes or No?')); // true
console.log(reg.test('Woo-hoo, Yeaaah!')); // false
````

The metacharacter `$` (dollar sign) is used in regex to represent the end of a string. 
When `$` is placed at the end of a regular expression pattern, it specifies that the preceding pattern should match only if it occurs at the end of the string.

**Example Regex ( Matching a `.com` ):**
````
let reg = /.com$/;

console.log(reg.test('abc@gmail.com')); // true
console.log(reg.test('https://www.apple.com')); // true
console.log(reg.test('https://www.yahoo.co.jp')); // false
````

### Quantifiers
You can use quantifiers in regex to specify the number of occurrences of a certain pattern, such as consecutive digits or alphabets. Quantifiers allow you to match a specific number of repetitions or specify a range.

* **The asterisk `*`**

    It matches zero or more occurrences of the preceding character or pattern. It means that the preceding character or pattern can appear any number of times, including zero repetitions.

* **The plus `+`**

    It matches one or more occurrences of the preceding character or pattern. It means that the preceding character or pattern must appear at least once, and it can also appear multiple times.

* **The question mark `?`**

    It matches zero or one occurrence of the preceding character or pattern.

* **The `{n}`**

   It matches exactly n occurrences of the preceding character or pattern. It specifies a specific number of repetitions for the preceding element.

* **The `{from,to}`**

   It matches a range of repetitions for the preceding character or pattern. It specifies the minimum and maximum number of occurrences for the preceding element.



**Example Regex ( Matching a postcode )**

Let's perform pattern checks on postal codes based on the following conditions:

 * `^[0-9]{3}`: It matches a sequence of three digits at the beginning of the string.
 * `\-?`: It matches an optional hyphen (-) character.
 * `[0-9]{4}$`: It matches a sequence of four digits at the end of the string.

````
let reg = /^[0-9]{3}\-?[0-9]{4}$/;

let str1 = '123-4567';
let str2 = '1234567';
let str3 = '12-3456';

console.log(reg.test(str1)); // true
console.log(reg.test(str2)); // true
console.log(reg.test(str3)); // false
````

### OR Operator
 * **The vertical bar `|`**

   It allows you to express a choice between two options. It acts as an OR operator, indicating that either of the options can match.

**Example Regex**

In this case, it means that the string ends with abc or xyz.

````
const regexp = /(abc|xyz)$/;
````


### Character Classes
 * **The `\d`**

   It is a shorthand character class that matches any digit character. It is equivalent to the character range [0-9].

 * **The `\w`**

    It is a shorthand character class that matches any word character, which includes lowercase and uppercase Latin letters, digits, and the underscore character.

 * **The `\s`**

    It is a shorthand character class that matches any whitespace character. It includes spaces, tabs \t, newlines \n, carriage returns \r, and form feeds \f.

 * **The `\D`,`\W`,`\S`**

    It represents their respective inverse character classes. 

      * `\D`: Matches any character that is not a digit (0-9).
      * `\W`: Matches any character that is not a word character (alphanumeric or underscore).
      * `\S`: Matches any character that is not a whitespace character.


 * **The `/pattern/`**

   **Example Regex**

   If a pattern matches when all the characters "CDE" are present in the same order, it would return true.
  
   ````
    let reg = /CDE/;

    let str1 = 'CDE';
    let str2 = 'ABCDE';
    let str3 = 'CD';
    let str4 = 'CDYZ';

    console.log(reg.test(str1)); // true
    console.log(reg.test(str2)); // true
    console.log(reg.test(str3)); // false
    console.log(reg.test(str4)); // false
   ````
 * **The dot `.` (period)**
  
  It matches any single character except for newline characters (\n).

  * **The backslash `\`**

   If you want to treat a special character as a literal character and match it exactly in a regular expression, you need to escape that character by using the backslash `\`.



### Flags

The 6 flags that are commonly used in regular expressions are:
 
 * `i` (Case-Insensitive): It makes the pattern case-insensitive, allowing it to match both uppercase and lowercase letters interchangeably.

 * `g` (Global): It enables global searching, meaning the pattern will search for all matches in the entire input string, rather than stopping after the first match.

 * `m` (Multiline): It changes the behavior of the ^ and $ anchors. In multiline mode, ^ matches the start of a line, and $ matches the end of a line, in addition to matching the start and end of the entire string.

 * `s` (Dot-All): It alters the behavior of the dot . metacharacter. In dot-all mode, the dot matches any character, including newline characters.

 * `u` (Unicode): It enables full Unicode matching. It allows the pattern to handle Unicode characters and properties correctly.

 * `y` (Sticky): It specifies that the search should start at the current position of the regular expression's lastIndex property and only return matches that start at this exact position.


Using flags in conjunction with patterns allows for more advanced searching capabilities in regular expressions. 


### Grouping and Capturing
 Grouping allows you to combine multiple patterns into a single unit and capture that group as a whole.
 It provides additional submatch information when a string matches the regular expression pattern. 

  *  The capturing group `(x)`:

     * (x) is used to define a group within a regular expression.
     * By placing patterns inside parentheses, you create a subexpression that is treated as a single unit.
     * Groups can be nested, and they establish a hierarchy of subexpressions.
     * Groups are useful for applying quantifiers, alternation, or capturing specific parts of the matched   text.
  
  * The named capturing group `(?<Name>x)`:

     * You use the syntax (?<name>pattern), where name is the desired name for the group, and in this case pattern is x you want to match.
     * The name must be enclosed in angle brackets (< and >), as you mentioned.
      
  * The non-capturing group `(?:x)`:

     * you use the syntax (?:pattern), where pattern represents the pattern you want to match.
     * The non-capturing group will match the specified pattern, but it will not store the matched content in any capture group.
     * Unlike capturing groups, the matched substrings within non-capturing groups cannot be accessed using the result array elements ([1], ..., [n]) or the predefined properties ($1, ..., $9) of the RegExp object.

  * `\n`:

     The backreference allows you to refer to the most recent substring that matched a particular capturing group. The backreference is denoted by \n, where n is a positive integer representing the position of the desired capturing group.

  * `\k<Name>`:

     you can use named capturing groups to capture specific parts of a pattern and refer to them using a backreference. The backreference to a named capturing group is denoted by \k<name>, where name is the name assigned to the capturing group.

### Bracket Expressions

  * square brackets `[]` :

     you can use this to define a character class, which matches any single character from the characters specified within the brackets. It allows you to specify a set of characters and match any one of them.
  
   **Example Regex**

 When you use a character class like [aeo], it represents a set of characters, and any one of those characters can match.
  
   ````
   let reg = /H[aeo]llo/;

   let str1 = 'Hello';
   let str2 = 'Hallo';
   let str3 = 'Hollo';

   console.log(str1.match(reg)); // ["Hello"] 
   console.log(str2.match(reg)); // ["Hallo"]
   console.log(str3.match(reg)); // ["Hollo"]
   ````
 * square brackets `[^...]` :
    
     By placing a caret (^) at the beginning of a character class, denoted by square brackets ([]), you can create a negated character class, which means it matches any character that is not in the specified set.
  
   **Example Regex**

     For example, the character class [^abc] matches any single character that is not 'a', 'b', or 'c'. It's like saying "match any character that is not present in this set".
  
   ````
   let reg = /[^abc]/g;

   let str1 = 'apple';
   let str2 = 'grape';
   let str3 = 'banana';

   console.log(str1.match(reg)); // ["p", "p", "l", "e"]
   console.log(str2.match(reg)); // ["g", "r", "p", "e"]
   console.log(str3.match(reg)); // ["n", "n"]
   ````
 * square brackets `[... - ...]` :

     The hyphen (-) inside square brackets ([]), known as a hyphen range, allows you to specify a range of characters based on their Unicode code points. It matches any character within the specified range.
       
    * `[0-9]`: To match the range of digits from 0 to 9. This pattern will match any single digit from 0 to 9.
    * `[A-Z]`: To match the range of uppercase letters from A to Z. This pattern will match any single uppercase letter from A to Z.
    * `[a-z]`: To match the range of lowercase letters from a to z. This pattern will match any single lowercase letter from a to z.


### Greedy and Lazy Match

* **Greedy Match**

 It will try to match the longest possible string.

 **Example Regex**

 `/<.+>/g`: It looks for < followed by any number of characters (.+) and then a >

 ````
  const string = `<div><h1>Hello</h1></div>`;

  const greedy = /<.+>/g;
  str.match(greedy); // [ '<div>`,'<h1>Hello</h1>','</div>']

 ````
 The above regex matches the whole string (in this case, Hello) because by default regex uses the Greedy algorithm and it finds the longest match.

* **Lazy Match**

 It will try to match the smallest possible string.

 `/<.+?>/g`: Adding a ? to the end of a regular expression pattern makes it perform a lazy match.

 **Example Regex**
  ````
  const string = `<div><h1>Hello</h1></div>`;

  const lazy = /<.+?>/g;
  str.match(lazy); // [ '<div>`,'<h1>','</h1>','</div>']

  ````

### Boundaries
* **`\b`** 

 They also call it by “word boundary”. This is one of the anchor like the caret (^) and the dollar sign ($). The word boundary match is zero-length.

  The characteristics of word boundaries:

 * Before the first character in a string if the first character is a word character.
 * After the last character in a string if the last character is a word character.
 * Between two characters in a string if one is a word character and the other is not.
  
  **Example Regex**

  ````
  console.log('Hello, JS!'.match(/\bJS\b/)); // true
  ````

### Back-references
 * **`\n`** 
 
 It allows you to refer back to previously matched groups within the pattern. They are represented by the syntax \n, where n is the index or number of the group.

 **Example Regex**

  ````
  const regex = /(H)\1+(E)\2+/g; 
  const str = "HHHEEELLOW";
  
  console.log(str.replace(regex, "$1$2"); // HELLOW

  ````
  The replacement string $1$2 refers to the first captured group "H" followed by the second captured group "E", effectively replacing the repeated occurrences with a single instance.


### Look-ahead and Look-behind
  * **`Look-ahead`** 

    It is a type of assertion in regular expressions that matches a specific position in the string without consuming any characters. It allows you to specify a pattern that must be followed by another pattern without including the latter in the overall match.

    The syntax for lookahead is `(?=pattern)`, where pattern represents the pattern that needs to match the characters ahead. 

    **Example Regex**

    ````
    const regex = /harbour (?= bridge)/;
    const str = "Here is harbour bridge.";

    console.log(regex.test(str)); // Output: true

    ````
    (?= bridge) is used after the pattern harbour. It ensures that the characters "harbour must be followed by the word "bridge" for a match. The test() method returns true because the string "Here is harbour bridge" satisfies this condition.

 * **`Look-behind`**
  
     It matches a specific position in the string based on the presence of a pattern behind it. 

     The syntax for Lookbehind is `(?<=pattern)`.
  
     **Example Regex**

     ````
     const regex = /(?<= harbour) bridge/;
     const str = "Here is harbour bridge.";

     console.log(regex.test(str)); // Output: true

     ````
    (?<=harbour) is used before the pattern bridge. It ensures that the word "bridge" must be preceded by the phrase "harbour" (including the space) for a match. The test() method returns true because the string Here is harbour bridge" satisfies this condition.


## Author
Sawako Goshima
https://github.com/sawaks