# Regex Tutorial: Email Validation

Welcome to this comprehensive tutorial on email regular expressions (regex) using JavaScript. In this tutorial, we will focus on understanding and using regex components specifically for email validation.


## **Summary**

Throughout the tutorial, we will break down the regex pattern designed to validate email addresses. Each part of the pattern will be explained in detail, highlighting its contribution to accurate and reliable email validation. You will learn about character classes, quantifiers, anchors, and other essential regex concepts. We will provide examples and analyze their application, allowing you to gain a solid understanding of how each component works in email validation.

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

# Regex Components
Here is a quick reference for regex components.

<mark>Literal Characters</mark>: These are ordinary characters that match themselves. For example, the letter "a" in a regex pattern will match the letter "a" in the text being searched.

<mark>Meta-characters</mark>: These are special characters with predefined meanings in regex. They include:
- (.) (dot): Matches any single character except a newline.
- (^) (caret): Matches the beginning of a line or string.
- ($) (dollar sign): Matches the end of a line or string.
- (*) (asterisk): Matches zero or more occurrences of the preceding element.
- (+) (plus): Matches one or more occurrences of the preceding element.
- (?) (question mark): Matches zero or one occurrence of the preceding element.
- ([ ]) (square brackets): Defines a character class, matching any character within the brackets.
- (|) (pipe): Represents the logical OR operation, matching either the expression before or after the pipe.
- (\) (backslash): Escapes meta-characters, allowing you to match them literally.

<mark>Character Classes</mark>: These specify a set of characters to match. For example, [a-z] matches any lowercase letter.

<mark>Quantifiers</mark>: These specify how many times an element should occur. Examples include * (zero or more), + (one or more), ? (zero or one), and {n} (exactly n occurrences).

<mark>Grouping and Capturing</mark>: Parentheses ( ) are used to group elements together and capture matched text for later use. This allows you to apply quantifiers or other operations to multiple characters or sub-patterns.

<mark>Anchors</mark>: ^ and $ are used as anchors to match the beginning and end of a line or string, respectively.

We will dive into more detail about Regex components and their syntax.



## **Anchors**

Anchors play an essential role in defining the position of the pattern within the input string. In the context of email validation, like in the regex featured in this tutorial /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/, it is crucial to ensure that the entire input string matches the specified pattern, rather than just a part of it. like it the summary above Anchors are made up of 2 main components.

1. Start Anchor ^: This asserts that the pattern must match the start of the string.
2. End Anchor $: This asserts that the pattern must match the end of the string.

**For Example** ("hello world): if you wanted to locate the hello in the string "hello world" the regex ^hello would locate it however if the string was "world hello" it would not similarly if you were looking for the word "world" the regex world$ would work but if it was written "world hello" it would not.

as for the example in this tutorial /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ both the starting and ending anchor tags tells us where the regex starts and ends.

## **Quantifiers**
Quantifiers are used to specify how many times a pattern should match. Quantifiers are placed after a character, character class, or group, in order to determine the minimum and maximum number of times preceding patterns should occur. In the context of email validation, like in the regex featured in this tutorial /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ it allows us to look for multiple patterns so we would able to look for multiple email addresses. but before we dive in lets break it down even more.

**For Example** (a+) looks for 1 or more, (a*) looks for 0 or more, (a?) looks for 0 or 1  of the preceding value, effectively making it optional. a{5}a{2,} -Looks for exactly five, two or more. {2,6} -forces the input of characters between two & six characters long. 

As for our example the + before [a-z0-9_\.-] and [\da-z\.-] tells us that the pattern should occur at least once, but it can also occur multiple times consecutively. while the {2,6} indicates that [a-z\.] the email address must end with a two to six letter top-level domain, such as .com, .edu, or .co.uk.

## **OR Operator**

 ( | )Acts like a boolean OR. Matches the expression before or after the |. It can operate within a group, or on a whole expression. The patterns will be tested in order. It will look for this OR that.

 **For Example** the regex (g|m) will highlight both the m and g in a statement like "the main thing we should focus on is what we will gain."


## **Character Classes**
Character classes match a character from a specific set. There are a number of predefined character classes and you can also define your own sets. this shortens your regex making it easier to read and understand. here are a few examples of character classes:
- [A-Z] Add a dash between two characters will select a Range.
- [ABC] Characters inside brackets will match any character in the set.
- [^ABC] Adding a caret will match any character that is not in the set.
- \w Matches any word character (alphanumeric & underscore).
- \d Matches any digit character (0-9)

Lets take a look at our feature Regex expression.  /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ contains multiple character classes lets deconstruct it.
- [a-z0-9_\.-]: this character class matches a single character that is either a lowercase letter (a-z), a digit (0-9), an underscore (_), a dot (.), or a hyphen (-).
- [\da-z\.-]: This character class matches a single character that is either a digit (\d is a shorthand for digits), a lowercase letter (a-z), a dot (.), or a hyphen (-).
- [a-z\.]: This character class matches a single character that is either a lowercase letter (a-z) or a dot (.).


## **Flags**

Expression flags change how the expression is interpreted. Flags follow the closing forward slash of the expression. here are some examples of flags:

- i Ignores case
- g Global search retain the index of the last match, allowing subsequent searches to start from the end of the previous match. Without the global flag, subsequent searches will return the same match.
- m Multiline flag When the multiline flag is enabled, beginning and end anchors (^ and $) will match the start and end of a line, instead of the start and end of the whole string.
- u Unicode
- y The expression will only match from its last Index position and ignores the global (g) flag if set. Because each search in Regex is discrete, this flag has no further impact on the displayed results.
- s Dot (.) will match any character, including newline.

 **For Example** /hello/i would highlight both "hello" and "Hello" and /ab/g would find all occurrences of "ab" in the input text, not just the first one.

 Essentially they are modifiers for your classes.

## **Grouping and Capturing**

In regular expressions (Regex), grouping and capturing refers to the mechanism of closing a portion of a pattern in parentheses ( ) to create a logical group. This grouping allows you to apply modifiers to multiple characters as a single group. then you will be able to capture that data and store it for future use.

 **For Example** (\d{2})-(\d{2})-(\d{4}) there are three groups. Each group captures two numbers, separated by hyphens, representing a date in the format "dd-mm-yyyy". By capturing the individual components, you can later extract and work with the day, month, and year separately.

 for our featured Regex example /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ we have three groups 
 
 - ^([a-z0-9_\.-]+): This is the first capturing group. It captures the username portion of the email address. It matches one or more lowercase letters, numbers, underscores, dots, or hyphens.

 - @([\da-z\.-]+): This is the second capturing group. It captures the domain portion of the email address(gmail, live, aol) after the "@" symbol. It matches one or more numbers, lowercase letters, dots, or hyphens.

 - \.([a-z\.]{2,6})$: This is the third capturing group. It captures the top-level domain portion of the email address after the last dot. It matches two to six lowercase letters or dots.


## **Bracket Expressions**

Bracket expressions are used to define a set of characters that can be matched within a single position in a text string. They are denoted by square brackets [ ~ ]. any character enclosed within these brackets will become a part of the set.

 **For Example** [A-Z0-9] both character classes A-Z and 0-9 are part of a single set denoted by one bracket expression.

 for our featured Regex example /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ we have again three sets each with their own character classes inclosed into three groups

## **Greedy and Lazy Match**
In regular expressions (Regex) greedy and lazy are terms used to describe the behavior of quantifiers when matching patterns. if you recall quantifiers specify how many times a certain element or group should be repeated. click [here](#quantifiers) for more details on quantifiers.

- Greedy Match: quantifiers are naturally greedy trying to get as many match as they possibly can. Greedy quantifiers are denoted by * (zero or more), + (one or more), ? (zero or one).
**For Eample**  In the pattern fre*, if the input text is "Freeeee", the greedy match will capture the entire string "Freeeee"

- Lazy Match: lazy matches are the complete opposite of greedy. they take the first match they can and are denoted by the use of ? quantifier.
**For Example** In the pattern fre?, if the input text is "Freeeee", the lazy match will capture the "fre" from the  string "Freeeee"
as soon as it found the first "e" it stopped.

 for our featured Regex example /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ we have multiple greedy matches denoted by the two + and the {2,6} and we have 0 lazy matches. lets break it down even furthur.
 - email name: multiple; numbers, lowercase letters, underscores, dots, and hyphens.
 - domain name:  multiple numbers, lowercase letters, dots, and hyphens.
 - top level domain name: 2-6 lower case letters and dots.

## **Boundaries**
when both the starting and closing [anchors](#anchors) are used they form a boundary inside the boundary is the code that makes up your regex. Boundaries can also be created in different ways. boundaries can use to define specific conditions for pattern matching. Some common boundary types include:
- **Start of String** (\A): Matches the position at the start of the entire string.
- **End of String** (\z or \Z): Matches the position at the end of the entire string.
- **Word Boundary** (\b): Matches the position between a word character and a non-word character.
- **Not Word Boundary** (\B): Matches any position that is not a word boundary.

there are many other types of boundaries and al help to simplify your Regex. here is a quick example to illustrate the point.

**For Example** \btest\b matches the word "test" as a whole. It will match "test" in the sentence "This is a test." but will not match "contest" or "testing".

for our featured Regex example /^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/ we have one boundary made up of the starting and closing anchors but no special boundary.

## **Back-references**
A back-reference is a feature that allows you to refer back to a previously matched group within the same regular expression pattern. It is denoted by the backslash \ followed by a modifiers like a number for example (\1 or \2). Back-references are useful when you want to match repeated patterns or ensure that the same content appears multiple times within a string.

**For Example** the Regex (\b\w+\b)\s+\1 captures a word using (\b\w+\b) and then matches the same word followed by whitespace using \s+. The \1 refers back to the first captured group, ensuring that the same word is repeated. if we have a string that says "hello hello world"
the pattern will match "hello hello" because the word "hello" is repeated.

## **Look-ahead and Look-behind**
Look-ahead and Look-behind are modifiers that allow you to add extra conditions to your pattern matching without including them in the final result. this make useful for when you searching for something but you want to be more specific in you with the pattern you are looking for.
here are examples of look-ahead and look-behind.

**For Example** (hello(?=world)) will look for hello but only if it is followed by "world" so the "hello" in "hello everyone" would not be selected unless one would use a negative look-ahead written like this (hello(?!world)).
look-behind works the same using this type of syntax  ((?<=pattern1)pattern2). so ((?<=hello)world) will look for all the instances of world that have the string hello before it. 


## **Author**
Thank you for reading if you have any questions, comments, or concerns  feel free to contact me or follow me on [github](https://github.com/sam-dejesus)



