# Regex Tutorial: Matching URLs with Regular Expressions

In JavaScript, a Regular Expression (RegEx) is an object that describes a sequence of characters used for defining a search pattern. For example, /^a...s$/. This code defines a RegEx pattern. The pattern refers to any five lietter string starting with 'a' and ending with 's'.

Below is a tutorial on how to use the match emails RegEx using this expression: /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/. This can be useful for validating emails using applications/technologies like Node or MongoDB.

## Summary

As a junior developer, I've learned that RegEx can be a powerful tool when writing code, paticularly Javascript. The pre-defined and ready-to-use RegEx make them user friendly and make my life a lot easier! Some common examples of regular expressions include match(), matchAll(), replace(), replaceAll(), search(), and split(). RegEx can be used for forms of validation, such as when someone is filling out an online form and has to input their email address.

Below are some more examples of Match an Email RegEx in action and how to use it. 

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

The anchors used in match email RegEx are ^ (caret), which indicates the beginning of the string, and $ (dollar), which indicates the end of the string.

#### Caret

The ^ anchor signifies a string that begins with the characters that follow. This could be used in one of two ways:

- An exact string match, such as when ^The, where the strings "The" or "The dog" match, but "the" and "the dog" don't. This is because a RegEx is case sensitive, so coders have to be specific. 
- You can also use ^ in a range of possible matches displayed by using bracket expressions.

#### Dollar 

The $ anchor signifies a string that ends with the characters before it. Just as with the ^ character, the $ character can be preceded by an exact string or a range of possible matches. 

So if we were to match the username /^[b-l0-9_-]{3,15}$/, the string must start and end with something that mathces the pattern [b-l0-9_-]. However, {3,16} is not included in our match because it's a different component called a quantifier, which is up next on our tutorial.

### Quantifiers

Quantifiers set the limits of a string that your RegEx matches (or an individual section of the string). They often include the minimum and maximum number of characters that your RegEx is looking for. 

Quantifiers in the matching email RegEx includes the + operator, which connects the user's email name+ email service+ .com. Another quantifier used in this regular expression is {2,6}. In the expression /^[b-l0-9_.-]+, any character matching the characters inside the bracket is expected to appear at least once with no maximum. 

If we were to have an expression such as [b-z.]{2,6}, then 2 to 6 characters matching those inside the brackets are expected. The numbers inside the curly brackets refers to the minimum and maximum number of characters expected.

### Character Classes & Escapes 

#### Classes

A character class in a RegEx defines a set of characters, any of which can occur in an input string to accomplish a match. In addition to the positive and ngative character groups, other common character classes include: 

- .—Matches any character except the newline character (\n)

- \d—Matches any Arabic numeral digit. This class is equivalent to the bracket expression [0-9].

- \w—Matches any alphanumeric (letters and numbers) character from the basic Latin alphabet, including the underscore (_). This class equates to this bracket expression [A-Za-z0-9_].

- \s—Matches a single whitespace character, including tabs and line breaks

The last three character classes listed can be changed to perform an inverse match by capitalizing letters. 

#### Escapes 

The backlash (\) in a RegEx "escapes" a character that would other be interpreted literally. For instance, the open curly bracket ({) is used to begin a qunatifier, but adding a backslash before it (\{) tells the RegEx to look for the open curly bracket character instead of beginning to define a quantifier. This is common when looks for strings with special characters that are the same as a particular component of a regular expression.

*Don't forget that all special characters, including the backslash, lose their "special" title inside bracket expressions.

### Flags

Flags are the one exception to the rule that a RegEx must be wrapped in slash characters. Flags are placed at the end of a RegEx, after the second slash, and they can define additional functionality or limits of the RegEx. While there are 6 types of flags in total, you're more likely to use these 3: 

- g—Global search: the regex should be tested against all possible matches in a string.

- i—Case-insensitive search: case should be ignored while attempting a match in a string

- m—Multi-line search: a multi-line input string should be treated as multiple lines

### Grouping and Capturing

#### Grouping

Grouping constructs allow you to break up regular expressions into multiple parts to make them more easy to understand. The primary way you break up or group a section of a RegEx is by using parentheses (). Each section with parentheses is know as a subexpression. 

For example: (abc):(xyz) contains two groups or subexpressions. The first is looking for a string that matches the string "abc" and the second is look for a string that matches the string "xyz". Subexpressions look for an exact match, unlike bracket expressions. 

#### Capturing

Capturing groups are a way to treat multiple characters in a single unit. They're created by grouping characters inside of parentheses. For instance, the RegEx (dog) creates a single group containing the letters "d" "o" and "g". 

Capturing groups are numbered by counting their opening parenthese from left to right. For instance, the expression ((A)(B(C))) contains four groups, which are: 

- ((A)(B(C)))
- (A)
- (B(C))
- (C)

To find the number of groups in an expression, you can use the groupCount method on a matcher object. The groupCount method returns an int showing the number of capturing groups in the pattern. 

### Greedy and Lazy Match

#### Greedy Quantifiers

Greedy quantifiers in RegEx match as much as they can, only giving back what's necessary to match the remainder of the expression. For instance, suppse you wnat to match tokens that begin with {START} and end with {END}, you'd try this: {START}.*{END}

However, you'd find that this pattern mathces the entire string from beginning to end: 

{START} Twinkle {END} twinkle {START} little star {END}

whereas we wanted to find two separate matches:

{START} Twinkle {END}
{START} little star {END}

So, what happened? Well, after matching {START}, the engine moves to the next token, which is .*

Because of this greedy quantifier, the dot-star maches all the characters to the end of the string. Then the engine moves to the next taken: the { at the beginning of {END}. But this fails to match because there are no characters left. 

However, the engine sees that it can backtrack into the dot-star. First, the dot-star gives up the last character in the string: {. The engine  tries to match the { token against this character, but fails. The dot-star then gives up the D. Again, the engine fails to match the { token against that character. Repeating this process, the dot-star gives up the N, the E and the {, and and the { token can finally match. Then the rest of the pattern END} matches, making the entire string the match. 

A good way to solve this problem is with lazy quantifiers. 

#### Lazy Quantifiers

A lazy quantifier first repeats the token as few times as required and exapnds the match as the engine backtracks through the regular expression to find an overall match. You can make a greedy quantifier lazy by adding a ? mark. For instance, you'd add a question mark to the previous example like this: {START}.*?{END}

The lazy .*? guarantees that the  dot only matches as many characters as needed for the rest of the pattern to succeed. This means the pattern only matches one {START}…{END} item at a time, which is the goal. 

### Boundaries

There are various types of boundaries, but for now we'll just cover word boundaries and not-a-word-boundary. A word boundary \b matches the positions where one side is a word character (such as a letter, digit, or underscore) while the other side is not a word character (such as the beginning of the string or a space character). For example, the RegEx \bbat\b would match the word bat in baseball bat, but it wouldn't match battery. 

Not-a-word-boundaries (\B), on the other hand matche all positions where \b does not match in our previous example. Not-a-word-boundaries match when:

- When neither side of the RegEx is a word character, for instance at any position in the string $=(@-%++) (including the beginning and end of the string)
- When both sides of the RegEx are a word character, such as the between of H and i in "Hi!"

This could be useful for various reasons. Going back to our previous example, \Bcat\B will find "cat" when it's fully surrounded by characters. cat\B will find cat in "certificate", for instance, but not in "tomcat" or on its own. 

### Back-references

Backreferences (\1) match the same text that's previously matched by a capturing group (remember those?). Let's say you want to match a pair of opening and closing HTML tags and the text between them. By putting the opening tag into a backreference, you can reuse the name of the tag for the closing tag. It would look something like this:

<([A-Z][A-Z0-9]*)\b[^>]*>.*?</\1> 

The opening HTML tag is everything within the first set of parentheses, so: [A-Z][A-Z0-9]*

The backreference (\1) references the first capturing group. \1 then matches the same text from that group. 

You can scan the regular expression from left to right to find the number of a particular backreference. Count the opening parentheses of all the numbered capturing groups. The first parenthesis would be backreference number one, the second number two, and so on. Skip parentheses that are part of other syntax like non-capturing groups. Note that non-capturing parentheses can be inserted into a regular expression without changing the numbers assigned to the backreferences. This can be useful when changing a complex regular expression.

### Look-ahead and Look-behind

Lookahead and lookbehind, together called “lookaround”, are zero-length assertions like start and end of anchors. The difference is that lookaround matches chatacters, but then gives up the match and just returns the result. They only assert whether a match ir possible or not. 

There are positive and negative lookahead and positive and negative lookbehind, so let's break this down. 

#### Positive and Negative Lookahead

Negative lookahead allows you to match something that's not followed by something else. For instance, because you can't use a negated character class to match a q that's not followed by a u, negative lookahead provides the solution: q(?!u). The negative lookahead is the pair of parentheses, with the opening parenthesis followed by a question mark and exclamation point. 

Positive lookahead works similarly, and would lool like this: q(?=u). This matches a q that's followed by a u without making the u part of the match. The positive lookahead is a pair of parentheses, with the opening parenthesis followed by a question mark and an equals sign. 

#### Negative and Negative Lookahead

Lookbehind has the same effect, except backwards. It tells the RegEx engine to temporarily step back in the string to check if the text inside can be matched. For instance, by using negative lookbehind, (?!a)c matches a "c" that's not preceded by an "a". This means that while it wouldn't match lab, it would match the b in bed or debt. Positive lookbehind, on the other hand, matches the b in lab, but not the b in bed or debt.

The negative lookbehin is written as (?<!text) while the positive lookbehind is written as (?<=text). 

## Author

My name is Lauren Pineiro and I'm a future front-end web developer in training. You can reach me via email at lamor1800@gmail.com or through GitHub: https://github.com/laurenp305 where you can also check out some of my other work.
