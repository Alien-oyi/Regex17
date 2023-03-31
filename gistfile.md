# Regex-tutorial

Regular expression is a powerful tool for pattern matching and text manipulation. It's a special sequence of characters that define a search pattern, and can be used in a variety of programming languages and text editors.

## Summary
I would use /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ as my example string.A valid hexadecimal color code must consist of either three or six hexadecimal digits, representing the amount of red, green, and blue in the color, respectively.

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
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
The starting ^ caret and ending $ dollar sign are both anchors in the example string. /^#?([a-f0-9]{6}|[a-f0-9]{3})$/,which means the match have to start with an optional #,"$" means the match have to end with 3 or 6 charcter.

### Quantifiers
Each quanifier denotes how many times the previous token will be matched.
{6} means the match have 6 charcter from range [a-f0-9].
{3} means the match have 3 charcter from range [a-f0-9]. 
 
### OR Operator
The pipe operator | means beside the # the match either have 3 digits or 6 digits.

### Character Classes
Character classes are found betwen [],in our example string,/^#?([a-f0-9]{6}|[a-f0-9]{3})$/,[a-f0-9] means the match only contain charcters from alphabet a to f or numberical 0 to 9.
### Flags
- i flag stands for ignore which means ingore uppercase or lowercase.
- g flag stands for global,find all the duplicate.
let string = "now,now,Now"
/now/g would return "now,now"
/now/ig would return "now,now,Now"
### Grouping and Capturing
Anything found inside of parentheses () creates a capture group.
$sign with number stands for position,we can use replace method to
switch position.
let result="Capturing Grouping".replace(/(\w+)\s(\w+)/, '$2 $1')
output "Grouping Capturing" 

### Bracket Expressions
In our example string, /^#?([a-f0-9]{6}|[a-f0-9]{3})$/
[a-f0-9] denotes the match can be a,b,c,d,e,f,0,1,2,3,4,5,6,7,8,9.
{3} quantifier is used to match exactly three occurrences of the preceding element.
() creates a capture group

### Greedy and Lazy Match
We can use "+" do the greedy match and "?" for lazy match
let string ="AAA"
/A+/ find all the "A"
/A?/ find first "A"

### Boundaries
\b word boundaries ensures that "moon" is matched as a complete word, 
and not as part of a longer word such as "mooncake".
let text = "The moon is round and mooncake is delicious."
let regex = /\bmoon/g;
let result = text.match(regex);
output would be "moon"

### Look-ahead-and-look-behind
In following example,?=pattern look-ahead matches the current position only if the pattern ahead of the current position matches,"?=\sbrown" means we need a space before the word "brown".
let text = "The quick brown fox jumps over the lazy dog.";
let regex = /\w+(?=\sbrown)/g;
let result = text.match(regex);
output "quick"

In following example, the pattern /(?<=quick\s)\w+/ matches any word character preceded by the word "quick" and a space, but the match only includes the word character.
let text = "The quick brown fox jumps over the lazy dog.";
let regex = /(?<=quick\s)\w+/g;
let result = text.match(regex);
output "brown"
