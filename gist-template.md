# RegexHTMLTag-Documentation

HTML uses tags to structure and style website content, with each tag having an opening and closing tag. Correctly matching HTML tags is crucial to ensure proper display of website content on various devices and browsers. This will assist in avoiding disorganization or broken appearance. This documentation emphasizes the importance of using matching HTML tags and offers tips to avoid common mistakes.

## Summary

Matching HTML tags is important for parsing and processing HTML documents. HTML tags are used to structure web pages and most other online content. HTML tags provide a way to mark up content with metadata that describes its meaning and structure, allowing web browsers and other software to interpret and display the content correctly. By matching HTML tags using regular expressions, programmers and web developers can extract specific data from HTML documents, manipulate the structure of the documents, and automate certain tasks related to web content processing.

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
- [Author](#Author)

## Regex Components

### Anchors

Matching HTML tag regex Anchors will utilize regular expression patterns to identify and match HTML tags in a text string. Typically, you will use a carrot "^" and a dollar sign "$" anchor to indicate the start and end of the string as well as bracket ("<" and ">") characters to match the brackets around the tags. The pattern `^<\w+>$` matches any HTML element opening tag that consists of a wword character within the bracket at the start and end of the string.

When considering a regular expression pattern for matching HTML tags that contain attributes and values you can make modifications to the pattern. If you had an HTML string such as `<div id="myDiv">Hello, world!</div>` which is a common testing string in HTML, you could use the regex pattern `^<\w+(\s+\w+="[^"]*")*>$`. This expression matches the opening tag which consists of a word character followed by zero or more paired attribute values including white space between them.

`^` - Start of the string <br>
`<` - Matches the opening angle bracket <br>
`\w+` - Matches one or more word characters (i.e., letters, numbers, or underscores), which represents the tag name <br>
`(` - Starts a capture group for the attributes <br>
`\s+` - Matches one or more whitespace characters, which separate the attribute-value pairs <br>
`\w+` - Matches one or more word characters, which represents the attribute name <br>
`=` - Matches the equals sign between the attribute name and value <br>
`"` - Matches the opening double quote of the attribute value <br>
`[^"]*` - Matches zero or more characters that are not a double quote, which represents the attribute value <br>
`"` - Matches the closing double quote of the attribute value <br>
`)*` - Closes the capture group for the attributes and allows for zero or more attribute-value pairs <br>
`$` - End of the string <br>

### Quantifiers

Matching HTML tag regex Quantifiers involves using regular expresssions to match specific patterns of text within HTML tags. Quantifiers are used to specify the number of times a pattern should occur.

Quantifiers:
`"?"` - Match zero or more occurrences <br>
`"+"` - Match one or more occurences <br>

When used in HTML, these quantifiers can be utilized to match frequently occuring attributes or nested tags. 

The pattern `^\s*<\w+\s+(\w+="[^"]*"\s*)*>` matches any opening HTML tag beginning with white space and followed by a letter character identifying the tag name as well as one or more pairs of attributed values with white space.

`^` - Matches the start of the string <br>
`\s*` - Matches zero or more whitespace characters (spaces, tabs, line breaks, etc.) at the beginning of the tag <br>
`<` - Matches the opening angle bracket of the tag <br>
`\w+` - Matches one or more word characters (letters, digits, or underscores), which represents the tag name <br>
`\s+` - Matches one or more whitespace characters between the tag name and the attributes <br>
`(` - Starts a capturing group for the attributes <br>
`\w+` - Matches one or more word characters, which represents the attribute name <br>
`=` - Matches the equals sign between the attribute name and value <br>
`"` - Matches the opening double quote of the attribute value <br>
`[^"]*` - Matches zero or more characters that are not a double quote, which represents the attribute value <br>
`"` - Matches the closing double quote of the attribute value <br>
`\s*` - Matches zero or more whitespace characters between attributes <br>
`)*` - Closes the capturing group for the attributes and allows for zero or more attribute-value pairs <br>
`>` - Matches the closing angle bracket of the tag <br>

### OR Operator

Matching HTML tag regex OR Operators provides developers the ability to use regular expressions to match multiple variations of a certain pattern within HTML tags using the `"|"` symbol to specify particular options.

The patter `<(p|div)>` is matching either the `<p>` or the `<div>` tag in a text string. In a similar case, the pattern `<(p|div)\s+(id|class)="[^"]*">` would also match either a `<p>` or `<div>` inlcuding attributes with values such as an `id` or `class`.

`<` - Matches the opening angle bracket of the tag <br>
`(p|div)` - Matches either the tag name p or div using the OR operator | <br>
`\s+` - Matches one or more whitespace characters between the tag name and the attributes <br>
`(id|class)` - Matches either the attribute name id or class using the OR operator | <br>
`=` - Matches the equals sign between the attribute name and value <br>
`"` - Matches the opening double quote of the attribute value <br>
`[^"]*` - Matches zero or more characters that are not a double quote, which represents the attribute value <br>
`"` - Matches the closing double quote of the attribute value <br>
`>` - Matches the closing angle bracket of the tag <br>

### Character Classes

Matching HTML tag regex Character Classes uses regular expressions to match a set of characters. Character classes can be utilized to match specific characters or a range of characters. 

`\d:` This matches any digit character (i.e., 0-9). <br>
`\w:` This matches any word character (i.e., alphabets, digits, and underscores). <br>
`\s:` This matches any whitespace character (i.e., spaces, tabs, and line breaks). <br>
`.:` This matches any character (except line breaks). <br>

You can use square brackets `[]` to define custom character classes such as `[aeiou]` - Matches any vowel character.

Lets break down a regular expression for better understanding, `/<(\w+)\s*.*?>.*?<\/\1>/`

`<:` This matches the opening angle bracket of an HTML tag. <br>
`(\w+):` This matches one or more word characters (i.e., alphabets, digits, and underscores) and captures them in a group. This group represents the tag name. <br>
`\s*:` This matches zero or more whitespace characters (i.e., spaces, tabs, and line breaks) after the tag name. <br>
`.*?:` This matches zero or more characters (except line breaks) in a non-greedy way. This is used to match any attributes present in the tag. <br>
`>:` This matches the closing angle bracket of an opening tag. <br>
`.*?:` This matches zero or more characters (except line breaks) in a non-greedy way. This is used to match the contents of the HTML tag. <br>
`<\/\1>:` This matches the closing tag of the HTML tag. The \/ matches the forward slash character, and \1 refers to the tag name captured in the first group. <br>

### Flags

Matching HTML tag regex Flags uses regular expressions to modify how they match against the input string.

Commonly used flags: <br>
`g` - Flag to match all occurences of a tag <br>
`i` - Flag to match tag names regardless of case <br>
`m` - Flag to match tags across multiple lines <br>
`s` - Flag to match tags with line breaks <br>
`u` - Flag to enable Unicode support <br>
`y` - Flag to match repeatedly in a loop <br>

Lets break down this expression pattern: `/\<(\w+)\s+.*class="example".*?>.*?<\/\1>/g`

`/:` The opening delimiter for the regular expression pattern. <br>
`\<:` This matches the opening angle bracket of an HTML tag. The backslash is used to escape the angle bracket so that it is not interpreted as a metacharacter.<br>
`(\w+):` This matches one or more word characters (i.e., alphabets, digits, and underscores) and captures them in a group. This group represents the tag name.<br>
`\s+:` This matches one or more whitespace characters (i.e., spaces, tabs, and line breaks) after the tag name.<br>
`.*:` This matches zero or more characters (except line breaks) after the whitespace characters. This is used to match any attributes present in the tag.<br>
class="example": This matches the string "class="example"" exactly. This is used to match the class attribute with the value "example".
`.*?:` This matches zero or more characters (except line breaks) in a non-greedy way. This is used to match any additional attributes that may be present before the closing angle bracket of the opening tag.<br>
`>:` This matches the closing angle bracket of an opening tag.<br>
`.*?:` This matches zero or more characters (except line breaks) in a non-greedy way. This is used to match the contents of the HTML tag.<br>
`<\/:` This matches the opening angle bracket and forward slash of a closing tag.<br>
`\1:` This is a backreference that matches the same tag name as the one captured in the first group. This ensures that the closing tag matches the opening tag.<br>
`>:` This matches the closing angle bracket of a closing tag.<br>
`/:` The closing delimiter for the regular expression pattern.<br>
`g:` The global flag, which matches all occurrences of the pattern in the input string.<br>


### Grouping and Capturing

Matching HTML tag regex Grouping and Capturing involves regular expressions to match and extract specific portions of the input string. 

Grouping can be achieved by enclosing part of the regular expression pattern in parantheses `"()"` which is a group that can be referred to later.

Capturing is the process of extracting the contents of a group from the input string. 

Grouping and Capturing together in the context of matching HTML tags, can be used to extract information about the tag, such as the tag name, attributes, and contents.

This regular expression pattern `/\<(\w+)\s+.*class="example".*?>.*?<\/\1>/g` includes a group that captures the tag name, which can be extracted from the result of the match using the `match()` function in JavaScript.

`/:` The opening delimiter for the regular expression pattern. <br>
`\<`: This matches the opening angle bracket of an HTML tag. The backslash is used to escape the angle bracket so that it is not interpreted as a metacharacter. <br>
`(\w+):` This matches one or more word characters (i.e., alphabets, digits, and underscores) and captures them in a group. This group represents the tag name. <br>
`\s+:` This matches one or more whitespace characters (i.e., spaces, tabs, and line breaks) after the tag name. <br>
`.*:` This matches zero or more characters (except line breaks) after the whitespace characters. This is used to match any attributes present in the tag. <br>
class="example": This matches the string "class="example"" exactly. This is used to match the class attribute with the value "example".
`.*?:` This matches zero or more characters (except line breaks) in a non-greedy way. This is used to match any additional attributes that may be present before the closing angle bracket of the opening tag. <br>
`>:` This matches the closing angle bracket of an opening tag. <br>
`.*?:` This matches zero or more characters (except line breaks) in a non-greedy way. This is used to match the contents of the HTML tag. <br>
`<\/:` This matches the opening angle bracket and forward slash of a closing tag.  <br>
`\1:` This is a backreference that matches the same tag name as the one captured in the first group. This ensures that the closing tag matches the opening tag. <br>
`>:` This matches the closing angle bracket of a closing tag. <br>
`/:` The closing delimiter for the regular expression pattern. <br>
`g:` The global flag, which matches all occurrences of the pattern in the input string. <br>

### Bracket Expressions

Matching HTML tag regex Bracket Expressions are also know as character classes which have touched on a few topics above. These expressions are used to match any single character that is contained within a set of brackets. In context with HTML tags, bracket expressions can be used to match any character that is valid within the tag name or attribute name.

Take this regular expression pattern as an example `/\<([a-z]+)[^>]*>/i`. The bracket expression has a `[a-z]+` matching one or more lowercase alphabet characters. This is followed by `[^>]*` matching any number of characters that are not a closing angle bracket.

`/:` This is the start of the regular expression pattern. The forward slashes are used to delimit the pattern.
`<:` This matches the opening angle bracket that starts an HTML tag.
`([a-z]+):` This is a capture group that matches one or more lowercase letters. The parentheses indicate that the contents of this group should be captured and returned as a separate result.
`[^>]*:` This matches zero or more characters that are not a closing angle bracket. The ^ character inside the brackets means "not", and the * means "zero or more times".
`>:` This matches the closing angle bracket that ends an HTML tag.
`/:` This is the end of the regular expression pattern. The forward slashes are used to delimit the pattern.
`i:` This is a flag that indicates the regular expression should be evaluated case-insensitively.


### Greedy and Lazy Match

Matching HTML tag regex can use either a Greedy or Lazy match. Greedy matches attempt to match as much of the string as possible while lazy matching attempts to match as little as possible. Consider the string `<p>Hello, world!</p><p>Goodbye, world!</p>` a greedy match for the opening tag `<p>` would match the entire string, while lazy would match only the first opening tag. 

Greedy match: `/<.*>/` will match the entire string because the `.*` matches everything between the first opening tag `<p>` and the last closing tag `</p>`. The resulting match will be `<p>Hello, world!</p><p>Goodbye, world!</p>`.

Lazy match: `/<.*?>` will match only the first opening tag because the `.*?` matches as little as possible. The resulting match will be `<p>`.

### Boundaries

Matching HTML tag regex Boundaries refers to the process of indentifying the beginning and ending tags of an HTML element using regular expressions. Web pages are made up of HTML tags that define the structure and content, and each HTML element has an opening tag and a closing tag.

Lets breakdown this regular expression `<(\w+)\b[^>]*>(.*?)</\1>`

`<:` matches the opening angle bracket of the tag. <br>
`(\w+):` matches one or more word characters (letters, digits, or underscores) and captures them in a group. <br>
`\b:` matches a word boundary, which ensures that the tag name is not part of a longer word. <br>
`[^>]*:` matches any characters that are not the closing angle bracket of the tag, allowing for any attributes or whitespace between the tag name and the closing bracket. <br>
`>:` matches the closing angle bracket of the opening tag. <br>
`(.*?):` matches any content between the opening and closing tags, capturing it in a group. <br>
`</\1>:` matches the closing tag, where \1 refers back to the tag name captured in the first group. <br>


### Back-references

Matching HTML tag regex Back-References is a technique using regular expressions that match opening and closing tags by referencing the tag name captured in the opening tag. Utilizing the syntax `"\1"` you can refer to a previously captured group within the same regular expression. 

Lets breakdown the regular expression `<(\w+)\b[^>]*>(.*?)</\1>`

`<:` Matches the opening angle bracket of the HTML tag. <br>
`(\w+):` Matches one or more word characters (letters, digits, or underscores) and captures them in a group. This represents the tag name. <br>
`\b:` Matches a word boundary to ensure that the tag name is not part of a longer word. <br>
`[^>]*:` Matches any characters that are not the closing angle bracket of the opening tag, allowing for any attributes or whitespace between the tag name and the closing bracket. <br>
`>:` Matches the closing angle bracket of the opening tag. <br>
`(.*?):` Matches any content between the opening and closing tags and captures it in a group. The ? makes the matching lazy, meaning it will match as few characters as possible to satisfy the expression. <br> 
`</\1>:` Matches the closing tag, where \1 is a back-reference that matches the same text as the first capturing group, which is the tag name from the opening tag. <br>

### Look-ahead and Look-behind

Matching HTML tag regex Look-ahead and Look-behind are advanced regular expression features. They can be used to match HTML tags in complex patterns. 

Look-ahead patterns match certain patterns that are followed by another pattern. While, look-behind patterns match patterns that is preceded by another pattern. 

The expression `/<p>(?=.*world).*<\/p>/` is using a look-ahead pattern to match any `<p>` tag containing the string "world" within its opening and closing brackets.

## Author

If you have questions, comments, or concerns please reach me at https://github.com/fabien1313 or
fabienmoreno1331@yahoo.com
