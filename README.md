# 17 Computer Science for JavaScript: Regex Tutorial Matching an Email

## Project Task

Developers write code, but they also _write about code_. Within the enclosed gist document, you will find a full tutorial of how to build a regex and understand many regex components in order to validate and match a user email.

## User Story

```md
AS A web development student
I WANT a tutorial explaining a specific regex
SO THAT I can understand the search pattern the regex defines
```

## Acceptance Criteria

```md
GIVEN a regex tutorial
WHEN I open the tutorial
THEN I see a descriptive title and introductory paragraph explaining the purpose of the tutorial, a summary describing the regex featured in the tutorial, a table of contents linking to different sections that break down each component of the regex and explain what it does, and a section about the author with a link to the author’s GitHub profile
WHEN I click on the links in the table of contents
THEN I am taken to the corresponding sections of the tutorial
WHEN I read through each section of the tutorial
THEN I find a detailed explanation of what a specific component of the regex does
WHEN I reach the end of the tutorial
THEN I find a section about the author and a link to the author’s GitHub profile
```

## What Is a Regex?

A **regex**, which is short for **regular expression**, is a sequence of characters that defines a specific search pattern. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate input.

For example, the following regular expression can be used to verify that user input is a valid email address:

Email Validation Regex: `/^([a-z0-9_\.-]+)@([\da-z\.]+)\.([a-z]{2,8})$/`

See the email-match-gist.md to see a full tutorial of how to match an email

Here is a link to matching demo: https://regex101.com/r/Rd1bUg/1

GitHub Repo Link: https://github.com/chelseyvalerio/regular-expression-tutorial

## Contact

Contact me at cvalerio@csog.net with any questions.
