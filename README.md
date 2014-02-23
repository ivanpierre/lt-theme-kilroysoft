# lt-theme-kilroysoft

## kilroySoft's theme on LightTable

Theme for our own usage of LightTable at kilroySoft's.

- Marked external brackets.
- Raibow brackets.
- Constants in italic (strings, numbers, keyworks, true, false, nil, ...)
- More contrasted colors, I'm a bit daltonian... :D

The directory should be placed in the plugin directory. user.behaviors file can be modified to activate the theme, then restart LightTable :

     ;; The editor tag is applied to all editors
     :editor [(:lt.objs.style/set-theme "kilroysoft")]

Warning ! if you change the name of the file, you should change the names of the classes in the CSS, else LightTable will not recognize them...

## Integrated as plugin

Now plugin manager can be used to directly load the theme from the Light Table repository.

You can find it under : LightTable kilroySoft's theme.

## Changes version 0.0.2

Adapted to the new plugin model

## Changes version 0.0.3

Corrected LightRed invalid color.
Added all color codes for tokens of standard syntax files, except apl.js... ;)

## Images

Clojure file
![Clojure](https://raw.github.com/ivanpierre/lt-theme-kilroysoft/master/img/editclj.png)

CSS file
![CSS](https://raw.github.com/ivanpierre/lt-theme-kilroysoft/master/img/editcss.png)

Javascript file
![JavaScript](https://raw.github.com/ivanpierre/lt-theme-kilroysoft/master/img/editjs.png)

## I dive in the code...

Ok, To apply correctly the various languages you have to read in the .lightable/core/node-modules/codemirror/modes/ directory where are the
language analysis scripts. The "token" function return the string for the type of token analysed. This type is used
to generate the classname for token colorization i.e. for the "string" type :

    .cm-s-kilroysoft span.cm-string {color: LightGreen; font-style:italic;}

I've taken the whole standard files and completed types. I only put new types for each
.js file, not the repeated used ones.

Say :

### clojure-mode.js

    builtin, comment, string, char, atom, number, bracket(0-12), keyword

### coffeescript.js

    variable, property, punctuation, operator, error

### css.js

     meta, qualifier, variable-2, tag, interpolation, string-2

### javascript.js

    variable-3

### markdown.js

    header, quote, hr, link, em, strong, emstrong

### xml.js

    word, attribute, equals

### jasmin.js

    instr, label, class, directive, access, base, type

### diff.js

    positive, negative

### eiffel.js

    ident

### erlang.js

    special

### gfm.js

    link

### http.js

    string-2

### plsql.js

    plsql-string, plsql-comment

### r.js

    arrow, arg-is, dollar, semi

Enjoy

Ivan

## Licence

Eclipse Public License - v 1.0, the same as Clojure

see LICENSE file in the directory
