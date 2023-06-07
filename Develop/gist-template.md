# Regular Expressions Guide - How to use Regex? 

This content shows you what is regex and how to use regex for bigginers of regex.

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

Regular expressions, often abbreviated as regex, are a method used to match and manipulate patterns of characters within a string. They are composed of a combination of characters that form a pattern and optional flags. 

Here's an example of a regular expression pattern for validating email addresses:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

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

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
