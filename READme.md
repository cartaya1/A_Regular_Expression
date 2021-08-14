<h1 align="center">A Regular expression?</h1>
  
<p align="center">
    <img src="https://img.shields.io/github/repo-size/cartaya1/A_Regular_Expression" />
    <img src="https://img.shields.io/github/languages/top/cartaya1/A_Regular_Expression"  />
    <img src="https://img.shields.io/github/issues/cartaya1/A_Regular_Expression" />
    <img src="https://img.shields.io/github/last-commit/cartaya1/A_Regular_Expression" >
    <a href="https://github.com/cartaya1"><img src="https://img.shields.io/github/followers/cartaya1?style=social" target="_blank" /></a>
    <a href="https://twitter.com/cartayas_USA">
        <img alt="Twitter: cartayas_USA" src="https://img.shields.io/twitter/follow/cartayas_USA.svg?style=social" target="_blank" />
    </a>
</p>

# Regex Tutorial
<p>
    <a href="https://cartaya1.github.io/A_Regular_Expression/Regular expressions quick reference.pdf">
        <img src="https://img.shields.io/badge/-Download%20PDF%20-0a0a0a.svg?style=flat&colorA=0a0a0a" alt="Download PDF">
    </a>
</p>

A regular expression (shortened as regex or regexp;[1] also referred to as rational expression[2][3]) is a sequence of characters that specifies a search pattern. Usually such patterns are used by string-searching algorithms for "find" or "find and replace" operations on strings, or for input validation. It is a technique developed in theoretical computer science and formal language theory.

The concept of regular expressions began in the 1950s, when the American mathematician Stephen Cole Kleene formalized the description of a regular language. They came into common use with Unix text-processing utilities. Different syntaxes for writing regular expressions have existed since the 1980s, one being the POSIX standard and another, widely used, being the Perl syntax.

Regular expressions are used in search engines, search and replace dialogs of word processors and text editors, in text processing utilities such as sed and AWK and in lexical analysis. Many programming languages provide regex capabilities either built-in or via libraries, as it has uses in many situations.

From Wikipedia, the free encyclopedia

## Summary

Regular expressions are patterns used to match character combinations in strings. In JavaScript, regular expressions are also objects. These patterns are used with the exec() and test() methods of RegExp, and with the match(), matchAll(), replace(), replaceAll(), search(), and split() methods of String. This chapter describes JavaScript regular expressions.

## Using simple patterns
Simple patterns are constructed of characters for which you want to find a direct match. For example, the pattern /abc/ matches character combinations in strings only when the exact sequence "abc" occurs (all characters together and in that order). Such a match would succeed in the strings "Hi, do you know your abc's?" and "The latest airplane designs evolved from slabcraft." In both cases the match is with the substring "abc". There is no match in the string "Grab crab" because while it contains the substring "ab c", it does not contain the exact substring "abc".

## Using special characters
When the search for a match requires something more than a direct match, such as finding one or more b's, or finding white space, you can include special characters in the pattern. For example, to match a single "a" followed by zero or more "b"s followed by "c", you'd use the pattern /ab*c/: the * after "b" means "0 or more occurrences of the preceding item." In the string "cbbabbbbcdebc", this pattern will match the substring "abbbbc".

# Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Autor Informations](#author-informations)


# Regex Components

# Anchors
[Table of Contents](#table-of-contents)

## Anchors in Regular Expressions

Anchors, or atomic zero-width assertions, specify a position in the string where a match must occur. When you use an anchor in your search expression, the regular expression engine does not advance through the string or consume characters; it looks for a match in the specified position only. For example, ^ specifies that the match must start at the beginning of a line or string. Therefore, the regular expression ^http: matches "http:" only when it occurs at the beginning of a line. The following table lists the anchors supported by the regular expressions in .NET.

### Anchors in Regular Expressions 

|Anchor|Description|
|:----:|----|
|^|By default, the match must occur at the beginning of the string; in multiline mode, it must occur at the beginning of the line. For more information, see Start of String or Line.|
|$|By default, the match must occur at the end of the string or before \n at the end of the string; in multiline mode, it must occur at the end of the line or before \n at the end of the line. For more information, see End of String or Line.|
|\A|The match must occur at the beginning of the string only (no multiline support). For more information, see Start of String Only.|
|\Z|The match must occur at the end of the string, or before \n at the end of the string. For more information, see End of String or Before Ending Newline.|
|\z|The match must occur at the end of the string only. For more information, see End of String Only.|
|\G|The match must start at the position where the previous match ended. For more information, see Contiguous Matches.|
|\b|The match must occur on a word boundary. For more information, see Word Boundary.|
|\B|The match must not occur on a word boundary. For more information, see Non-Word Boundary.|
|

### Start of String or Line: ^

By default, the ^ anchor specifies that the following pattern must begin at the first character position of the string. 
If you use ^ with the RegexOptions.Multiline option (see Regular Expression Options), the match must occur at the beginning of each line.

The following example uses the ^ anchor in a regular expression that extracts information about the years during which some professional baseball teams existed. The example calls two overloads of the Regex.Matches method:

The call to the Matches(String, String) overload finds only the first substring in the input string that matches the regular expression pattern.

The call to the Matches(String, String, RegexOptions) overload with the options parameter set to RegexOptions.Multiline finds all five substrings.

The regular expression pattern ^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+ is defined as shown in the following table.

### End of String or Line: $

The $ anchor specifies that the preceding pattern must occur at the end of the input string, or before \n at the end of the input string.

If you use $ with the RegexOptions.Multiline option, the match can also occur at the end of a line. Note that $ matches \n but does not match \r\n (the combination of carriage return and newline characters, or CR/LF). To match the CR/LF character combination, include \r?$ in the regular expression pattern.

The following example adds the $ anchor to the regular expression pattern used in the example in the Start of String or Line section. When used with the original input string, which includes five lines of text, the Regex.Matches(String, String) method is unable to find a match, because the end of the first line does not match the $ pattern. When the original input string is split into a string array, the Regex.Matches(String, String) method succeeds in matching each of the five lines. When the Regex.Matches(String, String, RegexOptions) method is called with the options parameter set to RegexOptions.Multiline, no matches are found because the regular expression pattern does not account for the carriage return element (\u+000D). However, when the regular expression pattern is modified by replacing $ with \r?$, calling the Regex.Matches(String, String, RegexOptions) method with the options parameter set to RegexOptions.Multiline again finds five matches.

### Start of String Only: \A

The \A anchor specifies that a match must occur at the beginning of the input string. It is identical to the ^ anchor, except that \A ignores the RegexOptions.Multiline option. Therefore, it can only match the start of the first line in a multiline input string.

The following example is similar to the examples for the ^ and $ anchors. It uses the \A anchor in a regular expression that extracts information about the years during which some professional baseball teams existed. The input string includes five lines. The call to the Regex.Matches(String, String, RegexOptions) method finds only the first substring in the input string that matches the regular expression pattern. As the example shows, the Multiline option has no effect.

### End of String or Before Ending Newline: \Z

The \Z anchor specifies that a match must occur at the end of the input string, or before \n at the end of the input string. It is identical to the $ anchor, except that \Z ignores the RegexOptions.Multiline option. Therefore, in a multiline string, it can only match the end of the last line, or the last line before \n.

Note that \Z matches \n but does not match \r\n (the CR/LF character combination). To match CR/LF, include \r?\Z in the regular expression pattern.

The following example uses the \Z anchor in a regular expression that is similar to the example in the Start of String or Line section, which extracts information about the years during which some professional baseball teams existed. The subexpression \r?\Z in the regular expression ^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\Z matches the end of a string, and also matches a string that ends with \n or \r\n. As a result, each element in the array matches the regular expression pattern.

### End of String Only: \z

The \z anchor specifies that a match must occur at the end of the input string. Like the $ language element, \z ignores the RegexOptions.Multiline option. Unlike the \Z language element, \z does not match a \n character at the end of a string. Therefore, it can only match the last line of the input string.

The following example uses the \z anchor in a regular expression that is otherwise identical to the example in the previous section, which extracts information about the years during which some professional baseball teams existed. The example tries to match each of five elements in a string array with the regular expression pattern ^((\w+(\s?)){2,}),\s(\w+\s\w+),(\s\d{4}(-(\d{4}|present))?,?)+\r?\z. 

Two of the strings end with carriage return and line feed characters, one ends with a line feed character, and two end with neither a carriage return nor a line feed character. As the output shows, only the strings without a carriage return or line feed character match the pattern.

### Contiguous Matches: \G

The \G anchor specifies that a match must occur at the point where the previous match ended. When you use this anchor with the Regex.Matches or Match.NextMatch method, it ensures that all matches are contiguous.

The following example uses a regular expression to extract the names of rodent species from a comma-delimited string.

### Word Boundary: \b

The \b anchor specifies that the match must occur on a boundary between a word character (the \w language element) and a non-word character (the \W language element). Word characters consist of alphanumeric characters and underscores; a non-word character is any character that is not alphanumeric or an underscore. (For more information, see Character Classes.) The match may also occur on a word boundary at the beginning or end of the string.

The \b anchor is frequently used to ensure that a subexpression matches an entire word instead of just the beginning or end of a word. The regular expression \bare\w*\b in the following example illustrates this usage. It matches any word that begins with the substring "are". The output from the example also illustrates that \b matches both the beginning and the end of the input string.

### Non-Word Boundary: \B
The \B anchor specifies that the match must not occur on a word boundary. It is the opposite of the \b anchor.

The following example uses the \B anchor to locate occurrences of the substring "qu" in a word. The regular expression pattern \Bqu\w+ matches a substring that begins with a "qu" that does not start a word and that continues to the end of the word.

.

# Quantifiers
[Table of Contents](#table-of-contents)

Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. The following table lists the quantifiers supported by .NET.

## QUANTIFIERS IN REGULAR EXPRESSIONS

|Greedy quantifier|Lazy quantifier|Description|
|:---------------:|---------------|-----------|
|*|*?|Match zero or more times.|
|+|+?|Match one or more times.|
|?|??|Match zero or one time.|
|{ n }|{ n }?|	Match exactly n times.|
|{ n ,}|{ n ,}?|	Match at least n times.|
|{ n , m }|{ n , m }?|	Match from n to m times.|
|

The quantities n and m are integer constants. Ordinarily, quantifiers are greedy; they cause the regular expression engine to match as many occurrences of particular patterns as possible. Appending the ? character to a quantifier makes it lazy; it causes the regular expression engine to match as few occurrences as possible. For a complete description of the difference between greedy and lazy quantifiers, see the section Greedy and Lazy Quantifiers later in this topic.

## Regular Expression Quantifiers

The following sections list the quantifiers supported by .NET regular expressions.

 Note: If the *, +, ?, {, and } characters are encountered in a regular expression pattern, the regular expression engine interprets them as quantifiers or part of quantifier constructs unless they are included in a character class. To interpret these as literal characters outside a character class, you must escape them by preceding them with a backslash. For example, the string \* in a regular expression pattern is interpreted as a literal asterisk ("*") character.

### Match Zero or More Times: *

The * quantifier matches the preceding element zero or more times. It is equivalent to the {0,} quantifier. * is a greedy quantifier whose lazy equivalent is *?.

The following example illustrates this regular expression. Of the nine digit groups in the input string, five match the pattern and four (95, 929, 9219, and 9919) do not.

### Match One or More Times: +

The + quantifier matches the preceding element one or more times. It is equivalent to {1,}. + is a greedy quantifier whose lazy equivalent is +?.

For example, the regular expression \ban+\w*?\b tries to match entire words that begin with the letter a followed by one or more instances of the letter n. The following example illustrates this regular expression. The regular expression matches the words an, annual, announcement, and antique, and correctly fails to match autumn and all.

### Match Zero or One Time: ?

The ? quantifier matches the preceding element zero or one time. It is equivalent to {0,1}. ? is a greedy quantifier whose lazy equivalent is ??.

For example, the regular expression \ban?\b tries to match entire words that begin with the letter a followed by zero or one instances of the letter n. In other words, it tries to match the words a and an. The following example illustrates this regular expression.

### Match Exactly n Times: {n}

The {n} quantifier matches the preceding element exactly n times, where n is any integer. {n} is a greedy quantifier whose lazy equivalent is {n}?.

For example, the regular expression \b\d+\,\d{3}\b tries to match a word boundary followed by one or more decimal digits followed by three decimal digits followed by a word boundary. The following example illustrates this regular expression.

### Match at Least n Times: {n,}

The {n,} quantifier matches the preceding element at least n times, where n is any integer. {n,} is a greedy quantifier whose lazy equivalent is {n,}?.

For example, the regular expression \b\d{2,}\b\D+ tries to match a word boundary followed by at least two digits followed by a word boundary and a non-digit character. The following example illustrates this regular expression. The regular expression fails to match the phrase "7 days" because it contains just one decimal digit, but it successfully matches the phrases "10 weeks and 300 years".

### Match Between n and m Times: {n,m}
The {n,m} quantifier matches the preceding element at least n times, but no more than m times, where n and m are integers. {n,m} is a greedy quantifier whose lazy equivalent is {n,m}?.

In the following example, the regular expression (00\s){2,4} tries to match between two and four occurrences of two zero digits followed by a space. Note that the final portion of the input string includes this pattern five times rather than the maximum of four. However, only the initial portion of this substring (up to the space and the fifth pair of zeros) matches the regular expression pattern.

### Greedy and Lazy Quantifiers

A number of the quantifiers have two versions:

- A greedy version.
    
        A greedy quantifier tries to match an element as many times as possible.

- A non-greedy (or lazy) version.

        A non-greedy quantifier tries to match an element as few times as possible. You can turn a greedy quantifier into a lazy quantifier by simply adding a ?.

Consider a simple regular expression that is intended to extract the last four digits from a string of numbers such as a credit card number. The version of the regular expression that uses the * greedy quantifier is \b.*([0-9]{4})\b. However, if a string contains two numbers, this regular expression matches the last four digits of the second number only.

### Quantifiers and Empty Matches

The quantifiers *, +, and {n,m} and their lazy counterparts never repeat after an empty match when the minimum number of captures has been found. This rule prevents quantifiers from entering infinite loops on empty subexpression matches when the maximum number of possible group captures is infinite or near infinite.

For example, the following code shows the result of a call to the Regex.Match method with the regular expression pattern (a?)*, which matches zero or one "a" character zero or more times. Note that the single capturing group captures each "a" as well as String.Empty, but that there is no second empty match, because the first empty match causes the quantifier to stop repeating.

.

# Grouping Constructs
[Table of Contents](#table-of-contents)

## Grouping Constructs in Regular Expressions

Grouping constructs delineate the subexpressions of a regular expression and capture the substrings of an input string. You can use grouping constructs to do the following:

Match a subexpression that is repeated in the input string.

Apply a quantifier to a subexpression that has multiple regular expression language elements. For more information about quantifiers, see Quantifiers.

Include a subexpression in the string that is returned by the Regex.Replace and Match.Result methods.

Retrieve individual subexpressions from the Match.Groups property and process them separately from the matched text as a whole.

The following table lists the grouping constructs supported by the .NET regular expression engine and indicates whether they are capturing or non-capturing.

|Grouping construct|Capturing or noncapturing|
|:----------------|-------------------------|
|Matched subexpressions|    Capturing|
|Named matched subexpressions|	Capturing|
|Balancing group definitions|	Capturing|
|Noncapturing groups|	Noncapturing|
|Group options|	Noncapturing|
|Zero-width positive lookahead assertions|	Noncapturing|
|Zero-width negative lookahead assertions|	Noncapturing|
|Zero-width positive lookbehind assertions|	Noncapturing|
|Zero-width negative lookbehind assertions|	Noncapturing|
|Atomic groups|	Noncapturing|
|

formation on groups and the regular expression object model, see Grouping constructs and regular expression objects.

## Matched Subexpressions
The following grouping construct captures a matched subexpression:

        ( subexpression )

where subexpression is any valid regular expression pattern. Captures that use parentheses are numbered automatically from left to right based on the order of the opening parentheses in the regular expression, starting from one. The capture that is numbered zero is the text matched by the entire regular expression pattern.

    Note

    By default, the (subexpression) language element captures the matched subexpression. But if the RegexOptions parameter of a regular expression pattern matching method includes the RegexOptions.ExplicitCapture flag, or if the n option is applied to this subexpression (see Group options later in this topic), the matched subexpression is not captured.


You can access captured groups in four ways:

- By using the backreference construct within the regular expression. The matched subexpression is referenced in the same regular expression by using the syntax \number, where number is the ordinal number of the captured subexpression.

- By using the named backreference construct within the regular expression. The matched subexpression is referenced in the same regular expression by using the syntax \k<name>, where name is the name of a capturing group, or \k<number>, where number is the ordinal number of a capturing group. A capturing group has a default name that is identical to its ordinal number. For more information, see Named matched subexpressions later in this topic.

- By using the $number replacement sequence in a Regex.Replace or Match.Result method call, where number is the ordinal number of the captured subexpression.

- Programmatically, by using the GroupCollection object returned by the Match.Groups property. The member at position zero in the collection represents the entire regular expression match. Each subsequent member represents a matched subexpression. For more information, see the Grouping Constructs and Regular Expression Objects section.

- The following example illustrates a regular expression that identifies duplicated words in text. The regular expression pattern's two capturing groups represent the two instances of the duplicated word. The second instance is captured to report its starting position in the input string.


### Named Matched Subexpressions

The following grouping construct captures a matched subexpression and lets you access it by name or by number:

        (?<name>subexpression)

        or:

        (?'name'subexpression)

where name is a valid group name, and subexpression is any valid regular expression pattern. name must not contain any punctuation characters and cannot begin with a number.

    Note

    If the RegexOptions parameter of a regular expression pattern matching method includes the RegexOptions.ExplicitCapture flag, or if the n option is applied to this subexpression (see Group options later in this topic), the only way to capture a subexpression is to explicitly name capturing groups.
 

You can access named captured groups in the following ways:

- By using the named backreference construct within the regular expression. The matched subexpression is referenced in the same regular expression by using the syntax \k<name>, where name is the name of the captured subexpression.

- By using the backreference construct within the regular expression. The matched subexpression is referenced in the same regular expression by using the syntax \number, where number is the ordinal number of the captured subexpression. Named matched subexpressions are numbered consecutively from left to right after matched subexpressions.

- By using the ${name} replacement sequence in a Regex.Replace or Match.Result method call, where name is the name of the captured subexpression.

- By using the $number replacement sequence in a Regex.Replace or Match.Result method call, where number is the ordinal number of the captured subexpression.

- Programmatically, by using the GroupCollection object returned by the Match.Groups property. The member at position zero in the collection represents the entire regular expression match. Each subsequent member represents a matched subexpression. Named captured groups are stored in the collection after numbered captured groups.

- Programmatically, by providing the subexpression name to the GroupCollection object's indexer (in C#) or to its Item[] property (in Visual Basic).


A simple regular expression pattern illustrates how numbered (unnamed) and named groups can be referenced either programmatically or by using regular expression language syntax. The regular expression ((?<One>abc)\d+)?(?<Two>xyz)(.*) produces the following capturing groups by number and by name. The first capturing group (number 0) always refers to the entire pattern.

.

# Bracket Expressions
[Table of Contents](#table-of-contents)

Character Classes and Bracket Expressions
A bracket expression is a list of characters enclosed by ‘[’ and ‘]’. It matches any single character in that list. If the first character of the list is the caret ‘^’, then it matches any character not in the list, and it is unspecified whether it matches an encoding error. For example, the regular expression ‘[0123456789]’ matches any single digit, whereas ‘[^()]’ matches any single character that is not an opening or closing parenthesis, and might or might not match an encoding error.

Within a bracket expression, a range expression consists of two characters separated by a hyphen. It matches any single character that sorts between the two characters, inclusive. In the default C locale, the sorting sequence is the native character order; for example, ‘[a-d]’ is equivalent to ‘[abcd]’. In other locales, the sorting sequence is not specified, and ‘[a-d]’ might be equivalent to ‘[abcd]’ or to ‘[aBbCcDd]’, or it might fail to match any character, or the set of characters that it matches might even be erratic. To obtain the traditional interpretation of bracket expressions, you can use the ‘C’ locale by setting the LC_ALL environment variable to the value ‘C’.

Finally, certain named classes of characters are predefined within bracket expressions, as follows. Their interpretation depends on the LC_CTYPE locale; for example:
 - ‘[[:alnum:]]’ means the character class of numbers and letters in the current locale.

- ‘[:alnum:]’
Alphanumeric characters: ‘[:alpha:]’ and ‘[:digit:]’; in the ‘C’ locale and ASCII character encoding, this is the same as ‘[0-9A-Za-z]’.

- ‘[:alpha:]’
Alphabetic characters: ‘[:lower:]’ and ‘[:upper:]’; in the ‘C’ locale and ASCII character encoding, this is the same as ‘[A-Za-z]’.

- ‘[:blank:]’
Blank characters: space and tab.

- ‘[:cntrl:]’
Control characters. In ASCII, these characters have octal codes 000 through 037, and 177 (DEL). In other character sets, these are the equivalent characters, if any.

- ‘[:digit:]’
Digits: 0 1 2 3 4 5 6 7 8 9.

- ‘[:graph:]’
Graphical characters: ‘[:alnum:]’ and ‘[:punct:]’.

- ‘[:lower:]’
Lower-case letters; in the ‘C’ locale and ASCII character encoding, this is a b c d e f g h i j k l m n o p q r s t u v w x y z.

- ‘[:print:]’
Printable characters: ‘[:alnum:]’, ‘[:punct:]’, and space.

- ‘[:punct:]’
Punctuation characters; in the ‘C’ locale and ASCII character encoding, this is ! " # $ % & ' ( ) * + , - . / : ; < = > ? @ [ \ ] ^ _ ` { | } ~.

- ‘[:space:]’
Space characters: in the ‘C’ locale, this is tab, newline, vertical tab, form feed, carriage return, and space. See Usage, for more discussion of matching newlines.

- ‘[:upper:]’
Upper-case letters: in the ‘C’ locale and ASCII character encoding, this is A B C D E F G H I J K L M N O P Q R S T U V - W X Y Z.

- ‘[:xdigit:]’
Hexadecimal digits: 0 1 2 3 4 5 6 7 8 9 A B C D E F a b c d e f.

Note that the brackets in these class names are part of the symbolic names, and must be included in addition to the brackets delimiting the bracket expression.

If you mistakenly omit the outer brackets, and search for say, ‘[:upper:]’, GNU grep prints a diagnostic and exits with status 2, on the assumption that you did not intend to search for the nominally equivalent regular expression: ‘[:epru]’. Set the POSIXLY_CORRECT environment variable to disable this feature.

    Most meta-characters lose their special meaning inside bracket expressions.

‘]’
ends the bracket expression if it’s not the first list item. So, if you want to make the ‘]’ character a list item, you must put it first.

‘[.’
represents the open collating symbol.

‘.]’
represents the close collating symbol.

‘[=’
represents the open equivalence class.

‘=]’
represents the close equivalence class.

‘[:’
represents the open character class symbol, and should be followed by a valid character class name.

‘:]’
represents the close character class symbol.

‘-’
represents the range if it’s not first or last in a list or the ending point of a range.

‘^’
represents the characters not in the list. If you want to make the ‘^’ character a list item, place it anywhere but first.

### This is a clomplement of next charter 

.

# Character Classes
[Table of Contents](#table-of-contents)

## Character classes in regular expressions

A character class defines a set of characters, any one of which can occur in an input string for a match to succeed. The regular expression language in .NET supports the following character classes:

Positive character groups. A character in the input string must match one of a specified set of characters. For more information, see Positive Character Group.

Negative character groups. A character in the input string must not match one of a specified set of characters. For more information, see Negative Character Group.

Any character. The . (dot or period) character in a regular expression is a wildcard character that matches any character except \n. For more information, see Any Character.

A general Unicode category or named block. A character in the input string must be a member of a particular Unicode category or must fall within a contiguous range of Unicode characters for a match to succeed. For more information, see Unicode Category or Unicode Block.

A negative general Unicode category or named block. A character in the input string must not be a member of a particular Unicode category or must not fall within a contiguous range of Unicode characters for a match to succeed. For more information, see Negative Unicode Category or Unicode Block.

A word character. A character in the input string can belong to any of the Unicode categories that are appropriate for characters in words. For more information, see Word Character.

A non-word character. A character in the input string can belong to any Unicode category that is not a word character. For more information, see Non-Word Character.

A white-space character. A character in the input string can be any Unicode separator character, as well as any one of a number of control characters. For more information, see White-Space Character.

A non-white-space character. A character in the input string can be any character that is not a white-space character. For more information, see Non-White-Space Character.

A decimal digit. A character in the input string can be any of a number of characters classified as Unicode decimal digits. For more information, see Decimal Digit Character.

A non-decimal digit. A character in the input string can be anything other than a Unicode decimal digit. For more information, see Decimal Digit Character.

.NET supports character class subtraction expressions, which enables you to define a set of characters as the result of excluding one character class from another character class. For more information, see Character Class Subtraction.

Positive character group: [ ]
A positive character group specifies a list of characters, any one of which may appear in an input string for a match to occur. This list of characters may be specified individually, as a range, or both.

The syntax for specifying a list of individual characters is as follows:

        [*character_group*]

where character_group is a list of the individual characters that can appear in the input string for a match to succeed. character_group can consist of any combination of one or more literal characters, escape characters, or character classes.

The syntax for specifying a range of characters is as follows:

        [firstCharacter-lastCharacter]

where firstCharacter is the character that begins the range and lastCharacter is the character that ends the range. A character range is a contiguous series of characters defined by specifying the first character in the series, a hyphen (-), and then the last character in the series. Two characters are contiguous if they have adjacent Unicode code points. firstCharacter must be the character with the lower code point, and lastCharacter must be the character with the higher code point.

.

# The OR Operator
[Table of Contents](#table-of-contents)

## Logical OR operator: ||

### Syntax

logical-or-expression || logical-and-expression

### Remarks

The logical OR operator (||) returns the boolean value true if either or both operands is true and returns false otherwise. The operands are implicitly converted to type bool before evaluation, and the result is of type bool. Logical OR has left-to-right associativity.

The operands to the logical OR operator don't have to have the same type, but they must be of boolean, integral, or pointer type. The operands are commonly relational or equality expressions.

The first operand is completely evaluated and all side effects are completed before continuing evaluation of the logical OR expression.

The second operand is evaluated only if the first operand evaluates to false, because evaluation isn't needed when the logical OR expression is true. It's known as short-circuit evaluation.

    printf( "%d" , (x == w || x == y || x == z) );

In the above example, if x is equal to either w, y, or z, the second argument to the printf function evaluates to true, which is then promoted to an integer, and the value 1 is printed. Otherwise, it evaluates to false and the value 0 is printed. As soon as one of the conditions evaluates to true, evaluation stops.

### Operator keyword for ||
C++ specifies or as an alternative spelling for ||. In C, the alternative spelling is provided as a macro in the <iso646.h> header. In C++, the alternative spelling is a keyword; use of <iso646.h> or the C++ equivalent <ciso646> is deprecated. In Microsoft C++, the /permissive- or /Za compiler option is required to enable the alternative spelling.

### Data Types
If the operands consist of one Boolean expression and one numeric expression, Visual Basic converts the Boolean expression to a numeric value (–1 for True and 0 for False) and performs a bitwise operation.

For a Boolean comparison, the data type of the result is Boolean. For a bitwise comparison, the result data type is a numeric type appropriate for the data types of expression1 and expression2. See the "Relational and Bitwise Comparisons" table in Data Types of Operator Results.

### Overloading
The Or operator can be overloaded, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure. If your code uses this operator on such a class or structure, be sure you understand its redefined behavior. For more information, see Operator Procedures.

.

# Flags
[Table of Contents](#table-of-contents)

## FlagsAttribute Class
.

Indicates that an enumeration can be treated as a bit field; that is, a set of flags.

    [System.AttributeUsage(System.AttributeTargets.Enum, Inherited=false)]
    public class FlagsAttribute : Attribute

.

    Inheritance Object -> Attribute -> FlagsAttribute

    Attributes AttributeUsageAttribute

### Remarks

Bit fields are generally used for lists of elements that might occur in combination, whereas enumeration constants are generally used for lists of mutually exclusive elements. Therefore, bit fields are designed to be combined with a bitwise OR operation to generate unnamed values, whereas enumerated constants are not. Languages vary in their use of bit fields compared to enumeration constants.

### Attributes of the FlagsAttribute
AttributeUsageAttribute is applied to this class, and its Inherited property specifies false. This attribute can only be applied to enumerations.

.
#### Guidelines for FlagsAttribute and Enum
.

- Use the FlagsAttribute custom attribute for an enumeration only if a bitwise operation (AND, OR, EXCLUSIVE OR) is to be performed on a numeric value.

- Define enumeration constants in powers of two, that is, 1, 2, 4, 8, and so on. This means the individual flags in combined enumeration constants do not overlap.

- Consider creating an enumerated constant for commonly used flag combinations. For example, if you have an enumeration used for file I/O operations that contains the enumerated constants Read = 1 and Write = 2, consider creating the enumerated constant ReadWrite = Read OR Write, which combines the Read and Write flags. In addition, the bitwise OR operation used to combine the flags might be considered an advanced concept in some circumstances that should not be required for simple tasks.

- Use caution if you define a negative number as a flag enumerated constant because many flag positions might be set to 1, which might make your code confusing and encourage coding errors.

- A convenient way to test whether a flag is set in a numeric value is to perform a bitwise AND operation between the numeric value and the flag enumerated constant, which sets all bits in the numeric value to zero that do not correspond to the flag, then test whether the result of that operation is equal to the flag enumerated constant.

- Use None as the name of the flag enumerated constant whose value is zero. You cannot use the None enumerated constant in a bitwise AND operation to test for a flag because the result is always zero. However, you can perform a logical, not a bitwise, comparison between the numeric value and the None enumerated constant to determine whether any bits in the numeric value are set.
If you create a value enumeration instead of a flags enumeration, it is still worthwhile to create a None enumerated constant. The reason is that by default the memory used for the enumeration is initialized to zero by the common language runtime. Consequently, if you do not define a constant whose value is zero, the enumeration will contain an illegal value when it is created.
If there is an obvious default case your application needs to represent, consider using an enumerated constant whose value is zero to represent the default. If there is no default case, consider using an enumerated constant whose value is zero that means the case that is not represented by any of the other enumerated constants.

- Do not define an enumeration value solely to mirror the state of the enumeration itself. For example, do not define an enumerated constant that merely marks the end of the enumeration. If you need to determine the last value of the enumeration, check for that value explicitly. In addition, you can perform a range check for the first and last enumerated constant if all values within the range are valid.

- Do not specify enumerated constants that are reserved for future use.

- When you define a method or property that takes an enumerated constant as a value, consider validating the value. The reason is that you can cast a numeric value to the enumeration type even if that numeric value is not defined in the enumeration.

.
# Character Escapes
[Table of Contents](#table-of-contents)

## Regex.Escape(String) Method

### Definition

Escapes a minimal set of characters (\, *, +, ?, |, {, [, (,), ^, $, ., #, and white space) by replacing them with their escape codes. This instructs the regular expression engine to interpret these characters literally rather than as metacharacters.

    public static string Escape (string str);

### Parameters
    str String
The input string that contains the text to convert.

### Returns

    String

A string of characters with metacharacters converted to their escaped form.

### Exceptions
    ArgumentNullException

str is null.

### Examples

The following example extracts comments from text. It assumes that the comments are delimited by a begin comment symbol and an end comment symbol that is selected by the user. Because the comment symbols are to be interpreted literally, they are passed to the Escape method to ensure that they cannot be misinterpreted as metacharacters. In addition, the example explicitly checks whether the end comment symbol entered by the user is a closing bracket (]) or brace (}). If it is, a backslash character (\) is prepended to the bracket or brace so that it is interpreted literally. Note that the example also uses the Match.Groups collection to display the comment only, rather than the comment together with its opening and closing comment symbols.

### Remarks
Escape converts a string so that the regular expression engine will interpret any metacharacters that it may contain as character literals. For example, consider a regular expression that is designed to extract comments that are delimited by straight opening and closing brackets ([ and ]) from text. In the following example, the regular expression "[(.*?)]" is interpreted as a character class. Rather than matching comments embedded in the input text, the regular expression matches each opening or closing parenthesis, period, asterisk, or question mark.

.

# Author Informations

## [Luis Cartaya](https://github.com/cartaya1)
[Table of Contents](#table-of-contents)
.
# Questions
✉️ Contact me with any questions: [email](mailto:cartaya1@msn.com) , 
[GitHub](https://github.com/cartaya1/A_Regular_Expression)<br />
