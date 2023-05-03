# Regular Expression Tutorial: How to match an Email

Today, we will be reviewing how to march an email using Regular Express, otherwise known as 'regex'. Now, this can be quite tricky but once understood, regex can do some amazing things and can be used not only within coding, but also within documents such as text files or text and replace. Let's take a look at a particular example of how regex can help when needing to match an email and break down the compenents of regex for easy understanding.

## Summary

In this gist guide, we'll be outlining a regular expression (regex) that may be used to validate if a particular text field contains an appropriatly typed email address. Below is an email vaidation regex we'll be using throughout this tutorial.

Email Validation Regex: /^([a-z0-9_\.-]+)@([\da-z\.]+)\.([a-z]{2,8})$/

To begin, let's break the above down into 3 segments: the username and @ symbol, the second level domain, and top level domain.
Example: hello@outlook.com (username@)(secondlevel domain)(toplevel domain)

Segment 1: /^([a-z0-9_\.-]+)@
this segement validates the username and @ symbol within the email address. The backslash (/) identifies the start of the regex and the initial carrot (^) anchor that declares taht the string must start with the following match. After each of these, each single character in the string will be validated against the character group outlined within the bracket expression: [a-z0-9_\.-]. We'll learn more about Bracket Expressions below. Breaking this down even futher, we'll be validating if the string includes characters a-z, digits between 0-9, if it's a period, underscore or hyphen. If the characters match these parameters, you have a match. The following + character is a Quantifier that tells the regex to try and match each character in the string with everything within the parenthesis anywhere between ONE to UNLIMITED times. We'll also learn more about Quantifiers below. Because of this Quantifier, it will match as large of a group of characters as possible and is referred to as a GREEDY Match. Finally, the last part of this segement is the @ symbol which simply is always expected following the string of previously matched characters. This is where you've probably run into errors as a user and the error reads ' must be a valid email ' before you put the @ sign within your email address.

Segment 2: ([\da-z\.]+)\.
this segement validates the email address second level domain (ex: outlook or gmail) and is followed by a period (.) We do not have an anchor section here to identify how this text must begin or end. Instead it will validate the middle of the entire email address string. The character validation here follows suit of segement 1 in that is identifies a-z. The /d is used to validate if the character being validated marches a digit between 0-9, it serves as a similar function to how the range of 0-9 is validated in segment 1. The period is used to validate if the character is a period or not. Becuase there is a + Quatifier here as well, it will match as large of a group as possible and can range between one to unlimited number of times. The outside period outside of the parenthesis and after the backslash, indicates is is looking the match a single period after the character group in a literal sense, ie. verifying the second level domain segment. If you have an outlook email, this will validate the outlook. segment of the email's domain or if you have gmail it will validate the gmail. segement of the email's domain.

Segment 3: ([a-z]{2,8})$/
    this segment validates the top level domain. the .com, .net, .edu, etc. Much like the previous two segements, a-z will be validated within the character body. This means however, the character in question must be lower case between letters a-z. If the regex identified A-Z in capital letters, the top level domain would need to be in all caps to match but it's extremly rare to have a top level domain with captial letters so we stick to validating a-z in most regexs. The {2,8} within the curly brackets however, is different than the previous two segements. This is our Quantifier defining how many characters the top level domain must be between. 2 is the minimum, while 8 is the maximum. This quantifier  tells the regex to attempt to match a group between 2 and 8 characters long as many times as possible. Finally, the dollar sign ($) symbol identifies an anchor and indicates this match must occur at the end of the string.

In summary, the above email validataion regular expression (regex) parses and tries to match the username to our initial achor and first character group. If that segment matches, it will check for the @ symbol, then parse through and attempt to match the second segment of the second level domain. If that segement validates, it will work to find the period and move through to parse and match the final top level domain with the final character group. Once all validated, it will check to ensure the string ends with the match as directed by the $ anchor.

Click the following link to see a test of the regex validation with an example email: https://regex101.com/r/Rd1bUg/1

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

In regex, we often need to define a specific amount of characters that should be included within the string. These specifics are referred to as Quantifiers which set a limit to the string that your regex, or an individual section of the string, can match. Typically Quantifiers include a minimum and maximum and are inherently greedy, meaning they match as many occurences of the pattern as possible. Quantifiers can include:

- - which matches the pattern ZERO or MORE times
- - which matches the pattern ONE or MORE times
- ? which matches the pattern either ZERO or ONE time.
- {} curly braces can provide three different ways to set limits for a match. One being { n } where matches the pattern EXACTLY n number of times. Two being { n, } where it matches the pattern AT LEAST n number of times. And lastly, { n,x } where n = the minimum number of times it matches and x = the maximum number of times.
  The caviot to this though, is that each quantifier can be made LAZY by adding the question mark (?) symbol AFTER. This means it will match as few occurrences as possible.

Similar to how we explain the above summary, when it comes to our purposes of matching our email regex above, we have two different quantifiers. The + character and a range of {2,8}. The + matches as many times as possible and the {2,8} indicates the top level domain must be between 2-8 a-z characters.

In essense, Quantifiers tell you what to look for to match an OR Operator. See [OR Operator](#the-or-operator) to learn more.

### Bracket Expressions

Bracket Expressions are unique in the fact that they represent range of characters we want to match. You may hear them referred to as positive character groups as well as they outline the characters that are qualified to be included. There are a few different ways we can construct characters within Bracket Expressions that give the ability to look for a range or specific characters. For example, we can write [xyz] which will look for x.y,z regardless of how long the string is. We could also write [x-z] which will look for for x,y,z just like before, regardless of the how long the string is. It just identifies a range so you can shorten your writen expression and don't have to type each character within the range. You can do this with numerical or special characters as well. Example: [0-9], or [#!&]. Keep in mind, if you want to allow for Meta Characters ie. capital letters, you must identify as such like shown [a-zA-Z]. For our purposes of matching an email, you can put these together similar to: [a-zA-Z0-9#!&].

### Character Classes

A character class defines a set of characters any of which can occur in an string to fulfill a string and is a set of characters enclosed within bracket expressions. Common Character classes can include:

- period (.) that matches any character expect a newline character
- \d - matches any numberal digit. If you refer back to segment 2 in the summary, this is equivilent to the bracket expression [0-9].
- \w - matches any alphanumeric character including the underscore symbol. It can be equivilenent to [A-Za-z0-9] used often to verify usernames.
- \s - matches a single whitespace character which can include those such as tabs and line breaks.

### Character Escapes

the backslash (\) used within a regex will escape a character that otherwise would be interpreted as its literal expression. Before we get into an example, it's important to note, all special characters including the backslash lose their otherwise specific significance inside bracket expressions. An example of a character escape would be if you have an open curly brace such as what we have in our email validation regex defining a quantifier but instead you put a backslash infront of the curly brace. It would then look like this (\{) and would signify to the regex it should look for the open curly brace character within the string instead of identifying the quantifier. Character escapes are commonly used when looking for strings that have special characters that are the same as a specific component within the regex, such as our quantifer above. You'd want to distinguish between the types of curly braces used and their responsibilities within the regex.

### Grouping Constructs

An email validation regex can be fairly open ended with what it accepts in regards to number of character matches per segment as outlined within the summary above however, as you grow with regular expressions and they become more complex, you may run into having to check multiple parts of a string to setermine if the different sections fulfill their differentiating requirements. This is where grouping constructs come in. The main way we group a section is by using parentheses (), within gropuing constructs these sections will become your subexpressions. An example of this is (hij):(tuv):(xyz). The first section looks for a string matching 'hij', the second looks for 'tuv', and the third looks for 'xyz'. The colon between these helps when matching each section string and seperating the subexpressions. The aforementioned string would look for 'hij:tuv:xyz' which would match, however the string 'ijh:uvt:xzy' would not. Order matters and an exact match is necessary unless the regex is told otherwise by an OR operator. We'll learn more about OR operators within the next section.

### The OR Operator

Although we do not have an OR Operator within our email validation regex, you could use them if looking to identify a specific top level domain. They pair very well with Grouping Constructs when things get more complex. In essense, the OR Operator (|) can seperate a string such as [xyz] to [x|y|z]. Often you want to add the same login outside of the bracket expression.

### Flags

Our current email validation regex does not use any flags however they are still beneficial to know. Typically regex must be wrapped in slash characters however, the one expection is when flags are placed at THE END of the regex, after the second slash. Flags identify additional functionality or limitations for the regex. THere are six optional flags total and they can be used seperatly, together, and in any order. The main three you may encounter are:

- g - global search where the regex can be tested against all possible matches in a string.
- i - case INSENSITIVE search where the case should be ignored while attempting the match the string.
- m - multiline search where a mltiline input string should be treated as multple lines.

The other three include:

- s - called a Dot All and makes the character a while character
- y - called a Sticky which makes the expression start is search from the index indiviated in the lastIndex property
- u - called a Unicode that makes the expression assume individual characters as code points not as code unites.

### Resources

Regex 101: https://www.regex101.com/ - where developers can test regular expressions

## Author

Chelsey Valerio
Github: https://github.com/chelseyvalerio/regular-expression-tutorial
Contact me at cvalerio@cosg.net
