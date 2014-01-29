# lt-theme-kilroysoft

## kilroySoft's theme on LightTable

Theme for our own usage of LightTable at kilroySoft's.

- Marked external brackets.
- Raibow brackets.
- Constants in italic (strings, numbers, keyworks, true, false, nil, ...)
- More contrasted colors, I'm a bit daltonian... :D

The CSS file should be placed in .lighttable\css\themes\ directory.

Warning if you change the name of the file, you should change the names of the classes in the CSS, else LightTable will not recognize them...

## Images

![Clojure](https://raw.github.com/ivanpierre/lt-theme-kilroysoft/master/img/editclj.png)
![CSS](https://raw.github.com/ivanpierre/lt-theme-kilroysoft/master/img/editcss.png)
![JavaScript](https://raw.github.com/ivanpierre/lt-theme-kilroysoft/master/img/editjs.png)

## Changes v0.0.2

For now its just tested with Clojure codemirror so the only used classes are

- builtin (sublist of known vars and function from the core library)
- comment ; xxxxxxx \\n
- string
- char
- atom (true false nil and quoted? I have to look the code)
- number (for now only, integer including octal and hex, and all floats) radix and fractional number not recognized
- bracket \(\[\{\}\]\)
- keyword (special forms and macros thereof)

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

## Problems with ' on QWERTZ keyboards

There's a problem with keyborad recognition with ' (quote). It's not in LightTable but in codemirror
.
Well a 'pis aller' can be a little modification in the
.lighttable/js/lib/codemorror.js file @ line 1330 and suppress the entry for "["

It's a problem with Javascript key event insanity with multiple keyboards. I prefer not
to report the arguments so it's bullshitesque... (Privacy reason...)

``` javascript
  var keyNames = {3: "Enter", 8: "Backspace", 9: "Tab", 13: "Enter", 16: "Shift", 17: "Ctrl", 18: "Alt",
                  19: "Pause", 20: "CapsLock", 27: "Esc", 32: "Space", 33: "PageUp", 34: "PageDown", 35: "End",
                  36: "Home", 37: "Left", 38: "Up", 39: "Right", 40: "Down", 44: "PrintScrn", 45: "Insert",
                  46: "Delete", 59: ";", 91: "Mod", 92: "Mod", 93: "Mod", 109: "-", 107: "=", 127: "Delete",
                  186: ";", 187: "=", 188: ",", 189: "-", 190: ".", 191: "/", 192: "`", 220: "\\",
                  221: "]", 222: "'", 63276: "PageUp", 63277: "PageDown", 63275: "End", 63273: "Home",
                  63234: "Left", 63232: "Up", 63235: "Right", 63233: "Down", 63302: "Insert", 63272: "Delete"};

```
Enjoy

Ivan

## Licence

Eclipse Public License - v 1.0, the same as Clojure

see LICENSE file in the directory
