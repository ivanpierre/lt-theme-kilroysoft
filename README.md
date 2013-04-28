lt-theme-kilroysoft
===================

KilroySoft's theme on LightTable

Theme for my own usage of LightTable.

- Marked external brackets.
- Raibow brackets.
- Constants in italic (strings, numbers, keyworks, true, false, nil, ...)
- More contrasted colors, I'm a bit daltonian... :D

The CSS file should be placed in .lighttable\css\themes\ directory.

Warning if you change the name of the file, you should change the names of the classes in the CSS, else LightTable will not recognize them...

Changes
=======

For now its just tested with Clojure codemirror so the only used classes are
- builtin (sublist of known vars and function from the core library)
- comment ; xxxxxxx \\n
- string
- char (seems to be managed as type but problems in the code)
- atom (true false nil and quoted? I have to look the code)
- number (for now only, integer including octal and hex, and all floats) radix and fractional number not recognized
- bracket \(\[\{\}\]\)
- keyword (special forms and macros thereof)

Seems to be a bug on the quote management (perhaps my FR-ch keyboard) so test for atoms are reported.

I dive in the code...

Ok, first constatation. Modular code, so it should be no problem... I shall study more in the deep. ;)

Enjoy

Ivan
