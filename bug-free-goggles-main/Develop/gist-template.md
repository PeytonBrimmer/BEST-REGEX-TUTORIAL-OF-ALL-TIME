# Peyton Brimmer REGEX Tutorial:

This is an application for teaching people how to use REGEX!!!!!! Yay!!!!!

## Summary

Regular Expression, AkA REGEX are sequences for characters that ar used to define a search pattern. These patterns have many applications commonly used in various string operations such as matching, replacing and searching for text within strings. we can use REGEX's to find text that conforms to specific patterns in order to effectively complete advanced text processing. Regular expressions are a powerful tool for processing and manipulation. REGEX's are commonly used in processing text files and can significantly cut down on the amount of code that is needed. REGEX is supported by all of the scripting languages. 

Regular Expressions use patterns describing a certain amount of text that is being matched against another subject string most often from left to right. Characters stand for themsleves and match with the coresponding character in the subject text. REGEX operations can include powerful alternatives, character classes and repititions in their pattern. We also can use meta characters that are differently interpreted than literal text for other ways of sorting subject strings. 


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

## Regex Components

### Anchors
anchors are used to match position before after or between characters. Anchors provice a way of limiting the regex matches by telling particular strings in the engine where they are allowed to begin and end. 

Carets ^ match the position before the first character in the string. This can only be used on the first character in the string.

Example: /^abc/A matches "abc" only at the start of the string.
Example: /a.*b/U matches the shortest string starting with "a" and ending with "b".
_____________________________________________________________________
### Quantifiers
Quantifiers indicate numbers of characters or expressions to match and are also used to define quantities

x*?
x+?
x??
x{n}?
x{n,}?
x{n,m}?

By default quantifiers like * and + are "greedy", meaning that they try to match as much of the string as possible. The ? character after the quantifier makes the quantifier "non-greedy": meaning that it will stop as soon as it finds a match. For

"*" = 0 or more
"+" = 1 or more
"?" = 0 or 1
"{2}" = exactly 2
"{2,}" = 2 or more 
"{2,4}" = 2, 3 or 4 
Adding ? to a quantifier makes it "lazy"

"Greedy" (default) Means: Meatch as many occurences of an expression as possible.

"Lazy" Means: Match as few occurences of an expression as possible.

### OR Operator
OR operators use | to return a value from a boolean to figure out if either or both operands are true, it will return true and otherwise it will return false. the operands are converted to bool type and the logical OR has a left to right associativity. example: ^(part1|part2)$
### Character Classes
character classes are used to match any of the enclosed characters. Characters can be specified into a range by using hyphens, but in the occurence of a hyphen appearing as the first or last character enclosed inside square brackets, it is taken as a literal hyphen which is then included in the character class as a nromal character.

Examples: 

[abcd-] and [-abcd] both match the same values of whatever b and c string you are working with as well as the - .
___________________________________________________________________

[abcd] is the same as [a-d]

________________________________________________________
Character classes also have unicoseSets (v) flag enabled whicg=h allow for additional features such as: 

The \p escape sequence can be additionally used to match properties of strings, instead of just characters.

The character class syntax is upgraded to allow intersection, union, and subtraction syntaxes, as well as matching multiple Unicode characters.

The character class complement syntax [^...] constructs a complement class instead of negating the match result, avoiding some confusing behaviors with case-insensitive matching.
### Flags
Flags are an accessor property of regex instances that return the flags of a regular expression. They are optional modifiers that you can use to change how regex patternsare interpreted.

'i' (ignore case) Example: /aBc/i matches "abc", "Abc", "aBc", etc.

'm' (multiline) Example: /^abc/m matches "abc" at the beginning of any line in a multi-line string.

's' (dotall) Example: /a.b/s matches "a\nb".

'g' (global) Example: /a/g finds all occurrences of "a" in the string.

'u' (Unicode) Example: /\u{61}/u matches "a" (where \u{61} is the Unicode code point for "a").

'y' (sticky) Example: 
const str = 'abc';
const regex = /a/y;
regex.test(str); // true
regex.lastIndex = 1;
regex.test(str); // false, because it does not match "bc" starting from index 1
______________________________________________________________________________________________________________________________________________
### Grouping and Capturing
Grouping allows you to treat part of a regular expression as a single unit. This is done using parenthesis'()'

Uses: Grouping is used through nesting, alternation and repitition. 

Repitition allows the use of quantifiers to a group to repeat the entire grouped pattern.
Example: (abc)+ matches "abcabc" in "abcabc".

Alternation uses the Or Operator in a group to match several patterns. 
Example: (abc|def) matches "abc" or "def".

Nesting is used in groups to be nested inside other groups.
Example: (abc|def) matches "abc" or "def".

Grouping: Use parentheses () to group parts of your regex.
_____________________________________________________________________
Capturing groups are used to gorup part of the regex but also to capture the matches from text. This captured text can be retrieved for further use. Captured grops are used to be refrenced later in the regex, this is called Backrefrences. Substitution is also used in the replacement string in substitution operations. Finally we have xtracting which is used to extract smaller parts of our capturing groups.

Capturing: Use parentheses to also capture the matched text for backreferences, substitutions, or extracting matches.

Capturing Example:
Regex: (abc)
Text: abc
Capture: abc

Non-Capturing groups also exist in order to group parts of the regex that do not need capturing. 

Non-Capturing Groups: Use (?: ... ) for grouping without capturing.

Named Capturing Groups: Use or (?P<name> ... ) (?<name> ... ) for more readable and manageable capturing.
### Bracket Expressions
Bracket Expressions in REGEX are used to specify character sets that you are trying to match. Bracket expressions are defined by using square brackets []. Bracket Expressions are used to find individual or ranges of chatacters in a set. Escape sequnces are also used in greedy or lazy in order to escape special characters within bracket expressions.


single character example: /[abc]/ matches "a" in "apple", "b" in "banana", and "c" in "cherry".

character ranges example: [a-z] matches any lowercase letter from "a" to "z".

or 

/[a-z]/ matches any lowercase letter in "hello".

________________________________________________________________________
### Greedy and Lazy Match
Greedy matches try to match as much of the text given as possible, vs lazy matching tries to match as little as possible. This works by the greedy quantifier matching a given element as many times as possible and vice-versa. This algorithm uses the diminishing returns property of submodular functions in order to avoid re-evaluating elements that provide little gain. Greedy quantifiers can be turned into a lazy quantifier by adding ? . 
Greedy = longest possible string.
Lazy = shortest possible string.

example: 
greedy h.+l matches 'hell' in 'hello' but the lazy h.+?l matches 'hel'
__________________________________________________
### Boundaries
boundaries are used ot match position where word charecters are not proceeded or followed by other word characters.

Example:
Regex: ^abc
Text: abc def
Match: abc (matches "abc" at the start of the string)
Regex: def$
Text: abc def
Match: def (matches "def" at the end of the string)

Example:
Regex: \bword\b
Text: wordy word
Match: word (matches "word" as a whole word)
Start (^) and End ($) Boundaries
"^" matches the beginning of a string.
"$" matches the end of a string.
_________________________________________________________
### Back-references
Back-refrences allow us to reuse part of the matched text in the REGEX.
By putting the opening tag into a backrefrence, we can reuse the name of the tag for the closing tag. Parenthesis in the regex allow us to capture strings we have matched. When we want to figure out the number value in a particular backreference, we can scan the regex from left to right, counting the opening parentheses of all the numbered capturing groups in the regex. We can have multiple backrefrences in a regular expressions, they are ordered starting with 1 being the farthest left and so on from there. The REGEX engine does not substitute backreferences permenantly in the expression. It will always use the last saved match into the backrefrence.

example: <([A-Z][A-Z0-9]*)\b[^>]*>.*?</\1>.

example: ([a-c])x\1x\1 matches axaxa, bxbxb and cxcxc.

### Look-ahead and Look-behind
Regular Expressions match from left to right, lookahead and lookbehind assertions are used to look ahead (to the right) and look behind(to the left). Negative Lookaheads also exist and can also constain capturing groups. 

(?=pattern) assertion works when the text matches after the current position.
(?!pattern) assertion works wehn the pattern does not match at the current position.

Look Ahead

Look-Ahead asssertions check for a match that follows a certain pattern without including the pattern in the match. It works by looking ahead and attempting to match the subsequent input with the pattern we are working with. if the match is successful the current position from the inpurt stays the same. Look-Ahead assertions do not consume any of the input. 

Lookahead can be used to match strings multiple times with different patterns, which allows for complex relationships to be expressed like subtraction and intersection.

example: 
(?=pattern)
(?!pattern)

_______________________________________________________________
Look Behind

Look-Behind assertions check for a match that precedes a certain pattern without including the pattern in the match.

example: /(?=(a+))a*b\1/.exec("baabac"); // ['aba', 'a']
// Not ['aaba', 'a']
____________________________________________________
## Author

This REGEX tutorial was created by Peyton Brimmer as aas a challenge during the MSU fullstack bootcamp of 2024.


