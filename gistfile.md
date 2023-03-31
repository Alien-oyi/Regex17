# Regex-tutorial

Regular expression is a powerful tool for pattern matching and text manipulation.<br />
It's a special sequence of characters that define a search pattern, and can be used <br />
in a variety of programming languages and text editors.

## Summary
I would use /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ as my example string.A valid hexadecimal <br />
color code must consist of either three or six hexadecimal digits, representing the <br />
amount of red, green, and blue in the color, respectively.

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
The starting ^ caret and ending $ dollar sign are both anchors in the example string.<br />
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/,which means the match have to start with an <br />
optional #,"$" means the match have to end with 3 or 6 charcter.<br />

### Quantifiers
Each quanifier denotes how many times the previous token will be matched.
{6} means the match have 6 charcter from range [a-f0-9].
{3} means the match have 3 charcter from range [a-f0-9]. 
 
### OR Operator
The pipe operator | means beside the # the match either have 3 digits or 6 digits.

### Character Classes
Character classes are found betwen [],in our example string,/^#?([a-f0-9]{6}|[a-f0-9]{3})$/,[a-f0-9] means the <br />match only contain charcters from alphabet a to f or numberical 0 to 9.<br />
### Flags
- i flag stands for ignore which means ingore uppercase or lowercase.<br />
- g flag stands for global,find all the duplicate.<br />
let string = "now,now,Now"<br />
/now/g would return "now,now"<br />
/now/ig would return "now,now,Now"<br />
### Grouping and Capturing
Anything found inside of parentheses () creates a capture group.<br />
$sign with number stands for position,we can use replace method to<br />
switch position.<br />
let result="Capturing Grouping".replace(/(\w+)\s(\w+)/, '$2 $1')<br />
output "Grouping Capturing" <br />

### Bracket Expressions
In our example string, /^#?([a-f0-9]{6}|[a-f0-9]{3})$/<br />
[a-f0-9] denotes the match charcters can be a,b,c,d,e,f,0,1,2,3,4,5,6,7,8,9.<br />
{3} quantifier is used to match exactly three occurrences of the preceding element.<br />
() creates a capture group<br />

### Greedy and Lazy Match
We can use "+" do the greedy match and "?" for lazy match<br />
let string ="AAA"<br />
/A+/ find all the "A"<br />
/A?/ find first "A"<br />

### Boundaries
\b word boundaries ensures that "moon" is matched as a complete word,<br /> 
and not as part of a longer word such as "mooncake".<br />
let text = "The moon is round and mooncake is delicious."<br />
let regex = /\bmoon/g;<br />
let result = text.match(regex);<br />
output would be "moon"<br />

### Look-ahead-and-look-behind
In following example,?=pattern look-ahead matches the current position only if the<br />
pattern ahead of the currentposition matches,"?=\sbrown" means we need a space before <br />
the word "brown".
let text = "The quick brown fox jumps over the lazy dog.";<br />
let regex = /\w+(?=\sbrown)/g;<br />
let result = text.match(regex);<br />
output "quick"<br />

In following example, the pattern /(?<=quick\s)\w+/ matches any word character preceded by <br />
the word "quick" and a space, but the match only includes the word character.<br />
let text = "The quick brown fox jumps over the lazy dog.";<br />
let regex = /(?<=quick\s)\w+/g;<br />
let result = text.match(regex);<br />
output "brown"<br />
