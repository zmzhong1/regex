# Phone number Regex

This gist will take in NANP format, a common format for phone numbers **(NXX-NXX-XXXX)**, the below information allows the user to understand the regex and ultimately utilize the regex to find phone numbers easily.

## Summary

The NANP format is commonly used in the US and various other countries, where N = digits 2 through 9 and X = any digit of 0 through 9.
The digit positions in the NANP format can be identified by alphabetical characters using the following format **(ABC-DEF-GHIJ)**

- where ABC is the NPA (numbering plan areas, also known as area code).
- DEF is the CO Code (Central Office code).
- GHIJ is the Line Number.

Additionally, we add also make sure that the user includes the country code, which most countries would fit into the category of +XXX, where X can be any digit of 0 through 9

In summary, once we combine the NANP format with the country code, the regex would be...

- ^([+]\d{1,3})?\s?[2-9]\d{2}[- ]?[2-9]\d{2}[- ]?\d{4}$

- Above code could work on phone numbers like:
  --- +1 206 200 2000 --- +12 206-200-2000 --- +123 206-200 2000

- BUT it would NOT work on phone numbers like:
  --- 1 206 200 2000 --- +1 106 200 2000 --- +1 206 000-0000

- What appears to be not working in the above line? well, user must input a **(+)** sign to place the country code, and the 1st and 4th digit in NANP format must be digit between 2-9.
- Additionally, this regex would only look at the beginning and end of the string, thus means it can only read one phone number input

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)

### Anchors

Anchors are unique in that they match a position within a string, not a character.

- ^ Matches the beginning of the string
- $ Matches the end of the string

Both above matches the position, thus when both being used only one input can be considered

### Quantifiers

Quantifiers indicate that the preceding token must be matched a certain number of times. By default, quantifiers are greedy, and will match as many characters as possible.

- ? Matches 0 or 1 of the preceding token, effectively making it optional.
- {1,3} Matches between 1 and 3 of the preceding token
- {2} {4} Matches 2 of the preceding token, or 4 of the preceding token

### Grouping Constructs

Groups allow you to combine a sequence of tokens to operate on them together. Capture groups can be referenced by a backreference and accessed separately in the results.

- ([+]\d{1,3}) Groups multiple tokens together and creates a capture group for extracting a substring or using a backreference. This case would be the country code, inclusive of a "+" sign and a digits between 1 to 3.

### Bracket Expressions

### Character Classes

Character classes match a character from a specific set. There are a number of predefined character classes and you can also define your own sets.

- [+] Match any character in the set, in this case would be +
- \d Matches any digit character (0-9). Equivalent to [0-9].
- \s Matches any whitespace character (spaces, tabs, line breaks).
- [2-9] Match any character in the set, in this case would be value 2 to 9
- [- ] Match any character in the set, in this case would be -

## Author

Ming Zhong is a web developer in Seattle, Washington. He is interested primarily in front-end development and data modeling. In his free time he enjoys videogames, hiking, and exploring new restaurants.

You can find him on Github at: https://github.com/zmzhong1
