# Regular Expressions: Exploring URL Matching

As a student, professional, or enthusiast in the realm of web development, you might already be familiar with the term 'Regular Expression', often shortened to 'regex'. These are incredibly useful tools that help us find, replace, and validate strings in text, with applications ranging from form validation to data extraction and more. Today, we are going to break down a specific regex used for matching URLs in JavaScript.

## Summary

In this tutorial, we'll be exploring a JavaScript regex used for matching URLs. The regular expression we'll be examining is as follows:

```
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/

```

We'll discuss each part of the expression in depth, breaking down their individual functionalities and how they all come together to validate a URL.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

Anchors are used in a regex to match at the beginning or the end of a string. They don't match any characters themselves but assert the position in the string where a match must start/end.

In our URL regex, we have two anchors:

```javascript
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/;
```

- `^` is the start-of-string anchor. It asserts that the following pattern must start at the beginning of the string. So our regex must match right from the start of the string.
- `$` is the end-of-string anchor. It asserts that the preceding pattern must be at the end of the string. So our regex must match all the way to the end of the string.

Anchors are key to ensuring that the entire string, and not just a part of it, matches our regex.

### Quantifiers

Quantifiers in regex specify how many instances of a character, group, or character class must be present in the input for a match to be found.

In our URL regex, we have several quantifiers:

```javascript
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/;
```

- `?` makes the preceding element optional. It matches zero or one instance of that element. For example, in `(https?:\/\/)?`, the `?` makes the 'http://' or 'https://' optional.
- `+` matches one or more of the preceding element. For example, `([\da-z\.-]+)` matches one or more alphanumeric characters, dots, or dashes.
- `{2,6}` is a specific quantifier. It matches between 2 and 6 instances of the preceding element. In `([a-z\.]{2,6})`, it's matching between 2 and 6 lowercase letters or dots.
- `*` matches zero or more of the preceding element. For example, in `([\/\w \.-]*)`, the `*` is saying that zero or more of these characters are acceptable.

Quantifiers can greatly increase the flexibility and power of your regex patterns.

### Grouping Constructs

Grouping constructs are a way to treat multiple characters as a single unit. They are created by placing the characters to be grouped inside a set of parentheses `()`.

In our regex, we can see several groups:

```javascript
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/;
```

- `(https?:\/\/)?` - This group matches either 'http://' or 'https://'. The question mark after the parenthesis means this entire group is optional.
- `([\da-z\.-]+)` - This group matches one or more alphanumeric characters, dots, or dashes.
- `([a-z\.]{2,6})` - This group matches between 2 and 6 lowercase letters or dots. It is used for matching the domain extension (like .com, .org, etc.).
- `([\/\w \.-]*)` - This group matches zero or more slashes, word characters, spaces, dots, or dashes. It is used for matching the optional path after the domain.

Using groups can greatly increase the power and flexibility of your regex, allowing you to apply quantifiers to entire sequences of characters and to capture the characters matched for use in a replacement or later in the pattern.

### Bracket Expressions

A bracket expression (also known as character set) is a type of character class that matches any character enclosed in the square brackets `[]`.

In our URL-matching regex, we use several bracket expressions:

```javascript
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/;
```

- `[https?:\/\/]` - This character set matches any character in 'http', 's', ':', '\/', '\/'. As a result, it can match 'http://', 'https://', and so on.
- `[\da-z\.-]` - This character set matches any digit (0-9), any lowercase letter (a-z), a dot (.), or a dash (-).
- `[a-z\.]` - This character set matches any lowercase letter (a-z) or a dot (.).
- `[\/\w \.-]` - This character set matches a slash (\/), any word character (a-z, A-Z, 0-9, \_), a space, a dot (.), or a dash (-).

These bracket expressions allow the regex to match URLs with a variety of characters.

### Character Classes

Character classes allow us to define specific sets of characters we want to match. In a character class, only one character needs to be matched for the overall match to succeed.

In our URL-matching regex, there are a few character classes:

- `\d`: Matches any digit from 0-9.
- `a-z`: Matches any lowercase letter.
- `A-Z`: Matches any uppercase letter (not present in our regex but mentioned for completeness).

Let's break it down:

```javascript
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/;
```

- `\d` and `a-z` are contained in the character class `[\da-z\.-]`, which matches a digit, a lowercase letter, or a period (.), or a hyphen (-). This is used to match the domain name (e.g., 'example' in 'www.example.com').

- `a-z` is also used in the character class `([a-z\.]{2,6})`, which matches a sequence of 2 to 6 lowercase letters or periods. This is used to match the domain extension (e.g., 'com' in 'www.example.com').

- `\w` in `([\/\w \.-]*)` matches any word character (equivalent to `[a-zA-Z0-9_]`), and is used to match the pathname of the URL (e.g., 'path/to/myfile' in 'www.example.com/path/to/myfile').

### The OR Operator

The OR operator in a regular expression is represented by the pipe symbol (|). It allows the regex to match one expression or another.

In our URL-matching regex, we don't have an OR operator:

```javascript
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/;
```

If we had one, it could look something like this: `(https?|ftp):\/\/`. This expression matches either 'http' or 'ftp' followed by '://'.

The OR operator provides flexibility in our pattern matching and is particularly useful when multiple patterns can satisfy the search requirement.

### Flags

In reular expressions, flags are optional parameters that modify the search. They can be used to make the search case-insensitive, search globally in a string, or search across multiple lines, among other things.

In our URL-matching regex, there are no flags present:

```javascript
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]_)_\/?$/;
```

The flags would normally be found at the end of the regular expression, after the closing `/`. For example, a `g` flag would look like this: `/some regex/g`. However, as we can see, our regex does not include any flags.

Just for your information, here are some commonly used flags in JavaScript regex:

- `g`: Global search, meaning the pattern will be searched for in the entire string.
- `i`: Case-insensitive search, meaning the pattern will match regardless of the case.
- `m`: Multiline search, meaning the pattern can match over multiple lines.

Even though our URL-matching regex doesn't use flags, they're still important to know as they can greatly enhance the power and flexibility of your regular expressions!

### Character Escapes

In regular expressions, certain characters hold special meanings, such as `.` (dot), `*` (asterisk), and `\` (backslash), to name a few. What if we want to match these characters as literal symbols in our search pattern? That's when character escapes come into play!

In our URL-matching regex, we use character escapes in a few places:

```javascript
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/;
```

Now, you might have noticed the `\.`, `\/`, and `\?` patterns. The backslash (`\`) here is the escape character that tells our regex engine to treat the following character (`.` or `/` or `?`) as a literal character, not a special symbol.

- `\\.`: Matches a literal dot (`.`).
- `\\\/`: Matches a literal forward slash (`/`).
- `\\?`: Matches a literal question mark (`?`).

For example, when we want to match the URL `https://www.example.com`, the `.` and `/` are matched by the `\.`, `\/` escape sequences in our regex.

## Author

Ilir Hajdari is an IT professional learning how to code!

-[Ilir's Github](https://github.com/IlirHajdari)
