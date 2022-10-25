# Regex Tutorial: Matching URLs with Regular Expressions

In JavaScript, a Regular Expression (RegEx) is an object that describes a sequence of characters used for defining a search pattern. For example, /^a...s$/. This code defines a RegEx pattern. The pattern refers to any five lietter string starting with 'a' and ending with 's'.

Below is a tutorial on RegEx and how to use this object with the help of examples.

## Summary

As a junior developer, I've learned that RegEx can be a powerful tool when writing code, paticularly Javascript. The pre-defined and ready-to-use RegEx make them user friendly and make my life a lot easier! Some common examples of regular expressions include match(), matchAll(), replace(), replaceAll(), search(), and split(). RegEx can be used for forms of validation, such as when someone is filling out an online form and has to input their email address.

Below are some more examples of RegEx in action and how to use it. 

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

## RegEx Components

### Anchors

Anchors are used at the beginning and end of searches to check if a string fully matches a pattern, although they themselves do not match the characters. They strictly affirm a string matches a location. Anchors will create parameters.

Common types of RegEx anchors are ^ (caret)	and $ (dollar). 

#### Caret

The ^ anchor signifies a string that begins with the characters that follow. This could be used in one of two ways:

- An exact string match, such as when ^The, where the strings "The" or "The dog" match, but "the" and "the dog" don't. This is because a RegEx is case sensitive, so coders have to be specific. 
- You can also use ^ in a range of possible matches displayed by using bracket expressions.

#### Dollar 

The $ anchor signifies a string that ends with the characters before it. Just as with the ^ character, the $ character can be preceded by an exact string or a range of possible matches. 

So if we were to match the username /^[b-l0-9_-]{3,15}$/, the string must start and end with something that mathces the pattern [b-l0-9_-]. However, {3,16} is not included in our match because it's a different component called a quantifier, which is up next on our tutorial.

### Quantifiers

Quantifiers set the limits of a string that your RegEx matches (or an individual section of the string). They often include the minimum and maximum number of characters that your RegEx is looking for. 

Qunatifiers match as many occurrences of certain patterns as possible, such as: 

- *—Matches the pattern zero or more times

- +—Matches the pattern one or more times

- ?—Matches the pattern zero or one time

- {}—Curly brackets can provide three different ways to set limits for a match:

- { n }—Matches the pattern exactly n number of times

- { n, }—Matches the pattern at least n number of times

- { n, x }—Matches the pattern from a minimum of n number of times to a maximum of x number of times

The ? symbol can also be added to quantifiers so they match as few occurrences as possible. 

Now, let's use quantifiers in our example. When it comes to the username /^[b-l0-9_-]{3,15}$/, we have the quantifier {3,15}. This means that we want to find the preceding string pattern a minimum of 3 times and a maximum of 15 times. Because our bracket expression ([b-l0-9_-]) will match any string that includes any combination of lowercase letters between b and l, any number between 0 and 9, and the special characters of underscore and hyphen, this quantifier means that the string has to be between 3 and 15 characters. 

### Bracket Expressions

Anything inside a set of square brackets [] is a range of characters known as bracket expressions, or they may also be called positive character group because they outline the characters we want to include when we're matching. We can write these expressions to include all of the characters we'd like to match. 

For instance, [abc] will look for a string that includes a or b or c, regardless of how long the string is. So any examples of a match would include: "aaa", "bbb", "ccc", "bat", "bin", "court", and "bca". It's also common to see a hyphen (-) used between letters and numbers to represent a range of possible characters. This means that [a-c] equates to [abc].

In the username example we've previously mentioned (/^[b-l0-9_-]{3,15}$/), we can break down the bracket expressions as follows: 

- [b-l] - This means the string can only contain any lowercase letter between b and l. If we also wanted to include uppercase letters, then the expression would have to be changed to [b-lB-L].
- [0-9] - This means the string can only contain any number between 0 and 9.
- [_-] - This means that the string can contain any underscore or hyphen. Both of these are known as special characters. You might have had to use them when creating a strong password. In this case, we only want a string that includes _ or -. 

### OR Operator



### Character Classes

### Flags

### Grouping and Capturing

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
