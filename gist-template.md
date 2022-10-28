# Regex Tutorial: Matching URLs with Regular Expressions

In JavaScript, a Regular Expression (RegEx) is an object that describes a sequence of characters used for defining a search pattern. For example, /^a...s$/. This code defines a RegEx pattern. The pattern refers to any five lietter string starting with 'a' and ending with 's'.

Below is a tutorial on how to use the match emails RegEx using this expression: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/. This can be useful for validating emails using applications/technologies like Node or MongoDB.

## Summary

As a junior developer, I've learned that RegEx can be a powerful tool when writing code, paticularly Javascript. The pre-defined and ready-to-use RegEx make them user friendly and make my life a lot easier! Some common examples of regular expressions include match(), matchAll(), replace(), replaceAll(), search(), and split(). RegEx can be used for forms of validation, such as when someone is filling out an online form and has to input their email address.

Below are some more examples of Match an Email RegEx in action and how to use it. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## RegEx Components

### Anchors

Anchors are used at the beginning and end of searches to check if a string fully matches a pattern, although they themselves do not match the characters. They strictly affirm a string matches a location. Anchors will create parameters.

The anchors used in match email RegEx are ^ (caret), which indicates the beginning of the string, and $ (dollar), which indicates the end of the string.

#### Caret

The ^ anchor signifies a string that begins with the characters that follow. This could be used in one of two ways:

- An exact string match, such as when ^The, where the strings "The" or "The dog" match, but "the" and "the dog" don't. This is because a RegEx is case sensitive, so coders have to be specific. 
- You can also use ^ in a range of possible matches displayed by using bracket expressions.

#### Dollar 

The $ anchor signifies a string that ends with the characters before it. Just as with the ^ character, the $ character can be preceded by an exact string or a range of possible matches. 

### Quantifiers

Quantifiers set the limits of a string that your RegEx matches (or an individual section of the string). They often include the minimum and maximum number of characters that your RegEx is looking for. 

Quantifiers in the matching email RegEx includes the + operator, which connects the user's email name+ email service+ .com. Another quantifier used in this regular expression is {2,6}. In our expression [a-z0-9_.-]+, any character matching the characters inside the bracket is expected to appear at least once with no maximum. 

If we were to have an expression such as [a-z.]{2,6}, then 2 to 6 characters matching those inside the brackets are expected. The numbers inside the curly brackets refers to the minimum and maximum number of characters expected.

### Character Classes 

A character class in a RegEx defines a set of characters, any of which can occur in an input string to accomplish a match. In addition to the positive and ngative character groups, other common character classes include: 

In our expression, \d in [\da-z\.-]+ is used to match any digital character. The backslash is needed to differentiate between the digital class from the letter d. While we only have one character class in our match email expression, the function of a backslash helps us understand the "." part of the expression.

Additionally, unlike other character classes, \d, \w (matches a word character), and \s (matches a whitespace characters), the character class "." - which matches any character - doesn't require a backslash. As a result, the backslash has to be used to negate its use as a character class and interpret it as the character ".".

### Grouping and Capturing

Grouping constructs allow you to break up regular expressions into multiple parts to make them more easy to understand. The primary way you break up or group a section of a RegEx is by using parentheses (). Each section with parentheses is know as a subexpression. 

Capturing groups are a way to treat multiple characters in a single unit. They're created by grouping characters inside of parentheses. For instance, the RegEx (dog) creates a single group containing the letters "d" "o" and "g". 

Both capturing and grouping can be done with () in regex.

For example, when we look at our expression /^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/, between the /^ and $/, there are three character groups, ([a-z0-9_.-]+), ([\da-z.-]+), ([a-z.]{2,6}). If we were to label these groups, then we'd see it this way: (1)@(2).(3). Easier to read, right? This is the format email addresses follow, which is the (string)@(website)(.com/edu/etc).

### Greedy and Lazy Match

This RegEx uses a greedy match, which is marked by the quantifiers "+", "*", and "{#}", all of which tell the RegEx to parse the input string attempt to match the largest group within the parameters. For instance, {#} (which is {2,6} in our expression) tells the RegEx to try and match between 2 and 6 times, or as many as possible for our given string. Lazy matches are marked by the question mark "?", but this can do different things. For instance, in this part of our expression ([a-z0-9_.-]+?), the lazy match would attempt to match as few times as possible.

## Bracket Expressions

Bracket expressions can be used to match a single character or collection of characters. In reference to our match email RegEx, [a-z0-9_\.-] matches any letter a-z and is case sensitive, matches any character from 0 to 9, and matches special characters "_", "-", and ".".

## Author

My name is Lauren Pineiro and I'm a future front-end web developer in training. You can reach me via email at lamor1800@gmail.com or through GitHub: https://github.com/laurenp305 where you can also check out some of my other work.
