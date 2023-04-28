# Regular Expression Tutorial: How to match an Email

Today, we will be reviewing how to march an email using Regular Express, otherwise known as 'regex'. Now, this can be quite tricky but once understood, regex can do some amazing things and can be used not only within coding, but also within documents such as text files or text and replace. Let's take a look at a particular example of how regex can help when needing to match an email and break down the compenents of regex for easy understanding.

## Summary

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Resources](#resources)
- [Author](#author)

## Regex Components

### Anchors

Anchors in essense tell you whether a string begins with the characters that follow or ends with the characters that follow. The carrot anchor (^) signifies a string BEGINS with the characters that follow. the dollar sign anchor ($) signifies a string ENDS with the characters that follow. One thing to note, is regex is CASE SENSITIVE.

- The carrot anchor (^): BEGINS with preceeding characters. Can occur in one of two formats: 1. an exact string match such as ^Hello where the stings "Hello" or "Hello friend" match but "hello" and "friend" do not. Notice the capitalization within ^Hello. Again, regex is case sensitive. 2. A range of possible matches, displayed using bracket [] expressions. See [Bracket Expressions](#bracket-expressions) below.

- The dollar sign anchor ($): ENDS with the preceeding characters. In the same fasion as the carrot anchor, the dollar sign anchor can be preceded with an exact string OR a range of possible matches.

### Quantifiers

### Grouping Constructs

### Bracket Expressions

Bracket Expressions are unique in the fact that they represent range of characters we want to match. You may hear them referred to as positive character groups as well as they outline the characters that are qualified to be included. There are a few different ways we can construct characters within Bracket Expressions that give the ability to look for a range or specific characters. For example, we can write [xyz] which will look for x.y,z regardless of how long the string is. We could also write [x-z] which will look for for x,y,z just like before, regardless of the how long the string is. It just identifies a range so you can shorten your writen expression and don't have to type each character within the range. You can do this with numerical or special characters as well. Example: [0-9], or [#!&]. Keep in mind, if you want to allow for Meta Characters ie. capital letters, you must identify as such like shown [a-zA-Z]. For our purposes of matching an email, you can put these together similar to: [a-zA-Z0-9#!&].

### Character Classes

### The OR Operator

### Flags

### Character Escapes

### Resources

Regex Pal: https://www.regexpal.com/ - where developers can test regular expressions

## Author

Chelsey Valerio
Github: https://github.com/chelseyvalerio/regular-expression-tutorial
Contact me at cvalerio@cosg.net
