# lt-theme-kilroysoft

## KilroySoft's theme on LightTable

Theme for my own usage of LightTable.

- Marked external brackets.
- Raibow brackets.
- Constants in italic (strings, numbers, keyworks, true, false, nil, ...)
- More contrasted colors, I'm a bit daltonian... :D

The CSS file should be placed in .lighttable\css\themes\ directory.

Warning if you change the name of the file, you should change the names of the classes in the CSS, else LightTable will not recognize them...

## Changes

For now its just tested with Clojure codemirror so the only used classes are
- builtin (sublist of known vars and function from the core library)
- comment ; xxxxxxx \\n
- string
- char
- atom (true false nil and quoted? I have to look the code)
- number (for now only, integer including octal and hex, and all floats) radix and fractional number not recognized
- bracket \(\[\{\}\]\)
- keyword (special forms and macros thereof)

Seems to be a bug on the quote management (perhaps my FR-ch keyboard) so test for atoms are reported.

## I dive in the code...

Ok, To apply correctly the various languages you have to read in the .lightable/js/lib/mode/ directory where are the 
language analysis scripts. The "token" function return the string for the type of token analysed. This type is used 
to generate the classname for token colorization i.e. for the "string"" type :

    .cm-s-kilroysoft span.cm-string {color: LightGreen; font-style:italic;}


I'll just take the standard files for clojure management and give the present types. Say :

### clojure-mode.js

    "builtin", "comment", "string", "char", "atom" "number", "bracket"(0-12), "keyword"

### coffeescript.js

    'variable', 'property', 'punctuation', 'operator', 'error' 
    ;; 'atom', 'number', 'comment', 'keyword'

### css.js

     "meta", "qualifier", "variable-2", "tag", "interpolation", "string-2"  
     ;; "atom", "variable", "keyword", "number", "operator", "property", "string", "builtin"

### htmlmixed.js

    No token, managed by css, javascript and xml.

### javascript.js

    "variable-3" 
    ;; "operator", "atom", "keyword", "string", "number", "comment", "variable", "variable-2"  

### less.js

    ;; "keyword", "number", "string", "tag", "atom", "variable", "comment", "meta"

### markdown.js

    'header', 'quote', 'hr', 'link', 'em', 'strong', 'emstrong'
    ;; 'comment', 'string', "tag"


### mysql.js

    ;; "variable", "variable-2", "atom", "comment", "string", "keyword" ;;; operator (missing null)


### xml.js

    "word", "attribute", "equals" 
    ;; "meta", "error", "atom", "tag", "comment"

Enjoy

Ivan
