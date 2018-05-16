# Android code style(Kotlin)

### Content
1. [Source files](#source_files)
    - [Naming](#source_files_naming)
    - [Special Characters](#source_files_special_characters)
    - [Structure](#source_files_structure)
2. [Formatting](#formatting)
    - [Braces](#formatting_braces)
    - [Indentation](#formatting_indentation)
    - [One statement per line](#formatting_one_statement_per_line)
    - [Line wrapping](#formatting_line_wrapping)
    - [Whitespace](#formatting_whitespace)
    - [Specific constructs](#formatting_specific_constructs)



<a id="source_files"><h2>Source files</h2></a>

  <a id="source_files_naming"><h3>Naming</h3></a>
  If a source file contains only a single top-level class, the file name should reflect the case-sensitive name plus the ```.kt``` extension. Otherwise, if a source file contains multiple top-level declarations, choose a name that describes the contents of the file, apply PascalCase, and append the ```.kt``` extension.<br>
  ```java
  // The file name must be HomeActivity.kt
  class HomeActivity {
    // ...
  }
  ```
  <a id="source_files_special_characters"><h3>Special Characters</h3></a>
    <h4>Whitespace characters</h4>
    Aside from the line terminator sequence, the ASCII horizontal space character (0x20) is the only whitespace character that appears anywhere in a source file.<br>
    This implies that:
      - All other whitespace characters in string and character literals are escaped.
      - Tab characters are not used for indentation.
    <h4>Special escape sequences</h4>
    For any character that has a special escape sequence (```\b```, ```\n```, ```\r```, ```\t```, ```\'```, ```\"```, ```\\```, and ```\$```), that sequence is used rather than the corresponding Unicode (e.g., ```\u000a```) escape.
    <h4>Non-ASCII characters</h4>
    For the remaining non-ASCII characters, either the actual Unicode character (e.g., ```∞```) or the equivalent Unicode escape (e.g., ```\u221e```) is used. The choice depends only on which makes the code easier to read and understand. Unicode escapes are discouraged for printable characters at any location and are strongly discouraged outside of string literals and comments.
    
   | Example                                | Discussion                                                               |
   |:--------------------------------------:|:------------------------------------------------------------------------:|
   | ```val unitAbbrev = "μs"```            | Best: perfectly clear even without a comment.                            |
   | ```val unitAbbrev = "\u03bcs" // μs``` | Poor: there’s no reason to use an escape with a printable character      |
   | ```val unitAbbrev = "\u03bcs" ```      | Poor: the reader has no idea what this is.                               |
   | ```return "\ufeff" + content```        | Good: use escapes for non-printable characters, and comment if necessary.|
    
  <a id="source_files_structure"><h3>Structure</h3></a>

<a id="formatting"><h2>Formatting</h2></a>

  <a id="formatting_braces"><h3>Braces</h3></a>
  
  <a id="formatting_indentation"><h3>Indentation</h3></a>
  
  <a id="formatting_one_statement_per_line"><h3>One statement per line</h3></a>
  
  <a id="formatting_line_wrapping"><h3>Line wrapping</h3></a>
  
  <a id="formatting_whitespace"><h3>Whitespace</h3></a>
  
  <a id="formatting_specific_constructs"><h3>Specific constructs</h3></a>
