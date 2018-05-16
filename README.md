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
  If a source file contains only a single top-level class, the file name should reflect the case-sensitive name plus the ```.kt``` extension. Otherwise, if a source file contains multiple top-level declarations, choose a name that describes the contents of the file, apply PascalCase, and append the ```.kt``` extension.
  ```java
  /* The file name must be HomeActivity.kt */
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
  
  A ```.kt``` file comprises of the following, in order:
  - Copyright and/or license header (optional)
  - File-level annotations
  - Package statement
  - Import statements
  - Top-level declarations
    
Exactly one blank line separates each of these sections.
  <h4>Copyright / License</h4>
  If a copyright or license header belongs in the file it should be placed at the immediate top in a multi-line comment.<br>
  For example:
  
  ```java
  /*
   * Copyright 2017 Google, Inc.
   *
   * ...
   */
  ```
  
  Do not use a KDoc-style or single-line-style comment.
  <h4>File-level annotations</h4>
  Annotations with the ‘file’ use-site target are placed between any header comment and the package declaration.
  <h4>Package statement</h4>
  The package statement is not subject to any column limit and is never line-wrapped.
  <h4>Import statements</h4>
  Import statements for classes, functions, and properties are grouped together in a single list and ASCII sorted.<br>
  Wildcard imports (of any type) are not allowed.<br>
  Similar to the package statement, import statements are not subject to a column limit and they are never line-wrapped.
  <h4>Top-level declarations</h4>
  
  A ```.kt``` file can declare one or more types, functions, properties, or type aliases at the top-level.<br>
  The contents of a file should be focused on a single theme. Examples of this would be a single public type or a set of extension functions performing the same operation on multiple receiver types. Unrelated declarations should be separated into their own files and public declarations within a single file should be minimized.<br>
  No explicit restriction is placed on the number nor order of the contents of a file.<br>
  Source files are usually read from top-to-bottom meaning that the order, in general, should reflect that the declarations higher up will inform understanding of those farther down. Different files may choose to order their contents differently. Similarly, one file may contain 100 properties, another 10 functions, and yet another a single class.<br>
  What is important is that each class uses some logical order, which its maintainer could explain if asked. For example, new functions are not just habitually added to the end of the class, as that would yield “chronological by date added” ordering, which is not a logical ordering.
  <h4>Class member ordering</h4>
  The order of members within a class follow the same rules as the top-level declarations.
<a id="formatting"><h2>Formatting</h2></a>

  <a id="formatting_braces"><h3>Braces</h3></a>
  
  Braces are not required for ```when``` branches and ```if``` statement bodies which have no ``else if`` / ``else`` branches and which fit on a single line.<br>
  For example:
  ```java
  if(TextUtils.isEmpty(inputId?.text)) dbResultPresenter?.execute()
  ```
  Braces are otherwise required for any if, for, when branch, do, and while statements, even when the body is empty or contains only a single statement.
  For example:
  ```java
  // NO
  if(TextUtils.isEmpty(inputId?.text))
      dbResultPresenter?.execute()
      
  // YES
  if(TextUtils.isEmpty(inputId?.text)){
      dbResultPresenter?.execute()
  }
  ```
  <h4>Empty blocks</h4>
  An empty block or block-like construct must be in K&R style.<br>
  For example:
  
  ```java
  // NO
  try {
      App.getSnappyDBSession()
              .put("android:" + i.toString(), generateEntity(0))
  } catch (e: SnappydbException) {}
  
  // YES
  try {
      App.getSnappyDBSession()
              .put("android:" + i.toString(), generateEntity(0))
  } catch (e: SnappydbException) {
  }
  ```
  <a id="formatting_indentation"><h3>Indentation</h3></a>
  
  Each time a new block or block-like construct is opened, the indent increases by four spaces. When the block ends, the indent returns to the previous indent level. The indent level applies to both code and comments throughout the block.
  
  <a id="formatting_one_statement_per_line"><h3>One statement per line</h3></a>
  
  Each statement is followed by a line break. Semicolons are not used.
  
  <a id="formatting_line_wrapping"><h3>Line wrapping</h3></a>
  
  Code has a column limit of 100 characters. Except as noted below, any line that would exceed this limit must be line-wrapped, as explained below.<br>
  For example:
  ![1](resources/string_length_screen.png)
  
  Exceptions:
  - Lines where obeying the column limit is not possible (for example, a long URL in KDoc).
  - ```package``` and ```import``` statements.
  - Command lines in a comment that may be cut-and-pasted into a shell.
  
  <h4>Continuation indent</h4>
  When line-wrapping, each line after the first (each continuation line) is indented at least +8 from the original line.<br>
  When there are multiple continuation lines, indentation may be varied beyond +8 as desired. In general, two continuation lines use the same indentation level if and only if they begin with syntactically parallel elements.
  
  <h4>Functions</h4>
  When a function signature does not fit on a single line, break each parameter declaration onto its own line. Parameters defined in this format should use a continuation indent (+8). The closing parenthesis (```)```) and return type are placed on their own line with no additional indent.<br>
  
  For example:<br>
  __Неправильно__:
  ![2](resources/functions_screen0.png)
  __Правильно__:
  ![3](resources/functions_screen1.png)
  
  When a function contains only a single expression it can be represented as an expression function.<br>
  For example:
  ```java
  fun toString(): String {
    return "Hello world!"
  }
  ```
  ```java
  fun toString(): String = "Hello world!""
  ```
  
  <h4>Properties</h4>
  When a property initializer does not fit on a single line, break after the equals sign (```=```) and use a continuation indent(+8).
  
  For example:<br>
  __Неправильно__:
  ![4](resources/properties_screen0.png)
  __Правильно__:
  ![5](resources/properties_screen1.png)
  
  <a id="formatting_whitespace"><h3>Whitespace</h3></a>
  
  <a id="formatting_specific_constructs"><h3>Specific constructs</h3></a>
