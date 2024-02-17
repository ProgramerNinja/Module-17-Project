# Email Verification Regex

In this document, I will present an example regex argument and walk you through each piece of it. Hopefully this will help lead to a greater understanding and appreciation of the power and flexability of regex.

## Summary

The regex argument that we will be taking a look at today will be: `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`. This argument is capable of sifting through a file and returning all strings that match the format of an email. It is also able to group each part of the email so that we can isolate it and have even greater control. This can be used to help with verifing that an email is valid when entering it into a data form or to sift through a documnet so that you can erase sensitive data.

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

- The regex argument of focus can be broken up into a few diffrent portions.
- `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`
- You can see that it is wrapped in "/". This allows for a lot of programs to recognise this as a regex argument rather than a literal string.

### Anchors

- You can also see that at the start we have a '^', This is used to indicated the start of a word or common string isolated by white space or specific special characters
- The '$' at the end is used to do the same thing but at the end of a word or common string rather than the beginning.

### Quantifiers

- Near the end of the argument, you can find this string: `([a-z\.]{2,6})`.
- If you take a close look, you can see that you have `[a-z\.]` followed by `{2,6}`.
- The '{}' indicates that there is a specific quantity of something we are looking for.
- In this case, we are looking for anywhere between 2 and 6 characters.
- Now we are also specifing what characters we are looking for by looking right infront of the quantifier.
- Here, we are looking for between 2 and 6 characters. Those characters must be either a letter or a '.'.
- There are also symbles that represent conditions rather than a specific amount:
- *—Matches the pattern zero or more times

- +—Matches the pattern one or more times

- ?—Matches the pattern zero or one time

### Grouping Constructs

- You can identify grouping constructs by "()".
- Anything inside is considered a group.
- You can almost think of them variables that are children of each match of the whole regex.
- Because of this, we can use groups to reorder the data rather than just replace it. such as switching all entries that "first, last" to "last, first".
- The groups from the example can be broken down into these 3 groups: `([a-z0-9_\.-]+)`, `([\da-z\.-]+)`, and `([a-z\.]{2,6})`.

### Bracket Expressions

- Bracket expressions are identified by "[]".
- Anything inside of these brackets are the accepted possibilities.
- In this case: `[a-z0-9_\.-]`, you can see it will expcept and combination of any letter: `a-z`, any number: `0-9`, an `_`, or a `.`.

### Character Classes

- Character classes are shorthand for common sets of characters.
- \d matches any digit, \w matches any word character (alphanumeric character plus underscore), and \s matches a single whitespace character, including tabs and line breaks
This provides a concise way to specify certain character sets without listing out all possible characters.

### The OR Operator

- While there is not an OR operator in this example it is symbolized with `|`.
- With this, we are able to select literals such as `(123)` where it will only accept `123`. and make it accept it in a diffrent order.
- By using it as such `(1|2|3)`, then we can have it accept the characters `1`, `2`, `3`, in any order.
- By using the OR operator, we can now accept `321`, `312` and so on.

### Flags

- Flags are almost like switches to set preferences or behaviors for the regex.
- By placing them at the end of a regex argument after the last slash we can do as such:
g—Global: this will allow characters to be used more than once to find matches.

i—Case-insensitive: case will be ignored .

m—Multi-line: allows a result to traverse multiple lines.

### Character Escapes

- As you have seen above, some characters have more than a literal meaning in regex.
- So we can use those characters such as `(),{},[],$,^` and such, all we need ro do is put a '\' infront of them.
- We can do so as such `\^` so we get '^' rather than it looking fo the start of a word.

## Author

[Jared M](https://github.com/ProgramerNinja)
