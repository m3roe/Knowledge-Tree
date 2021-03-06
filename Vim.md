## Modes

* `i`, `a`, `A` - Insert mode
* `s` - Substitutes and inserts
* `R` - Replace (overwrite) mode (`r` for one-shot)
* `<esc>`, `<ctrl> + [` - Normal mode
* `Q` - Go to ex mode
* `visual` - To vim from ex mode`
* Operator-pending mode - After you enter a command, it waits for an operator to execute it
* `Ctrl+o` - Insert-Normal mode, one-shot normal command then back to insert
* `Ctrl+g` in Visual mode - Switches to select mode, which works the same as GUI text editors
* Visual mode
    * `v` for character-wise
    * `V` for line-wise
    * `Ctrl+v` for block-wise
    * `gv` to highlight the previous visual area
    * `o` - Toggle which end of a visual selection is fixed
    * `I` and `A` allow you to insert- `i`/`a` are for text objects
    * `:` to enter `ex` mode with that range selected
* `q:` - In normal mode, open a buffer with your command history- searchable, editable

## CLI Commands

* `vim <filename> <filename>` - Open multiple files
* `vim + <filename>` - Open file at last line
* `vim +<num> <filename>` - Open file at a specific line
* `vim +/<pattern> <filename>` - Open file at the first occurrence of pattern
* `vim -R <filename>` - Read-only
* `vim -r` - Show recovered files
* `vim -r <filename>` - Recover file

## Save/Quit

* `:w <new filename>` - Save (write)
* `:w! <new filename>` - Save with overwrite
* `:w %` - Save current file
* `:q` - Quit
* `:q!` - Force quit, no save
* `:wq` - Write and quit
* `:x` - Write and quit (doesn’t update modified time if not changed)
* `:e!` - Reset this file
* `:r` - Import contents of file
* `:pre` - Preserve buffer (if the file turns out to be read only, for example)
* `ZZ` - Save and quit

## Open

* `:n` - Next open file
* `:e <filename>` - Edit a file while keeping the current one open
    * `Ctrl + ^` - Switch between open files
    * `:e #` - Switch between open files

## Movement Commands

* `w` - forward one word
* `W` - Forward one word, skip punctuation
* `b` - Backward one word
* `B` - Backward one word, skip punctuation
* `0` - Beginning of line
* `$` - End of line
* `gg` - Beginning of file
* `G` - End of file
* `G<number>` - Go to line
* ``` `` ``` - Go to your last edit
* `''` - Go to the beginning of the line your last edit was on
* `+` - First character of next line
* `-` - First character of previous line
* `^` - First non-blank character in a line
* `<num> |` - Move to a specific line’s column
* `(` - Beginning of sentence
* `)` - End of sentence (looks for . ? or ! followed by two spaces)
* `{` - Beginning of paragraph
* `}` - End of paragraph (looks for sentence followed by paragraph marker)
* `{{` - Beginning of section
* `}}` - End of section (looks for sentence followed by section marker)

## Markers

* `m <marker name>` - Set a named marker
* `' <marker name>` - Jump to beginning of marker’s name
* `` `<marker name>`` - Jump to marker

## Registers

`"<character><command>`

* `"ayy` - Yank line into register `a`
* `"ap` - Paste register `a`
* `"1p` - Paste the last yanked thing
* `"9p` - Paste the thing that was yanked 9 things ago
* `""yy` - Yank into the unnamed register (what yank uses)
* `"+yG` - Yank until the end of the file into the system register
    * Vim must be compiled with clipboard support
* `"+p` - Paste the system register and keep formatting intact
* Macros use the same registers, and can be edited and yanked into
* `Ctrl+r a` - Paste register `a` in insert mode

## Screen Commands

* `ctrl + f` - Page forward
* `ctrl + b` - Page backward
* `ctrl + d` - Half page forward
* `ctrl + u` - Half page backward
* `ctrl + y` - One line forward
* `ctrl + e` - One line backward
* `z <enter>` - Cursor to top and recenter
* `z .`, `zz` - Recenter screen
* `z -` - Cursor to bottom and recenter
* `<num>z` - Center on a specific line
* `H` - "home", top line of screen
    * numeric prefix is lines away from top
* `M` - "middle", middle line on screen
* `L` - "last", last line on screen
    * numeric prefix is lines away from bottom
* `Ctrl + L` - Redraw the screen`

## Search

These can all be used with the other vim commands (eg, change, delete)

* `/<search>` - Regex search (n for next, N for previous)
* `?<search>` - Regex search backward (n for next, N for previous)
* `/<enter>` - Repeat search
* `?<enter>` - Repeat search backward
* `/~` - `~` is a glob for your last regex

## Find within a line

These can all be used with the other vim commands (eg, change, delete)

* `f <character>` - Find next character in the current line
* `F <character>` - Find previous character in the current line
* `t <character>` - Find the character before the next <character> in the current line
* `T <character>` - Find the character before the previous <character> in the current line
* `;` - Next, same direction
* `,` - Next, opposite direction

## Replace

* `%s/<search>/<replace>/<options>` - Regex search and replace
    * `g` - Global
    * `i` - Case insensitive
    * `c` - Confirm
* `:g/<pattern>/s/<old>/<new>/g` - Find lines that match, then run :s
* `ctrl + v` - Escape next character

## Insert Commands

`<num><insert command><character><normal mode>` - Insert repeating characters.

* `a` - Add text after cursor
* `A` - Add text at end of line
* `i` - Add text before cursor
* `I` - Add text at beginning of line
* `o` - Insert blank line after
* `O` - Insert blank line before

## Change Commands

* `c<num><type>` - Change some text. `w`/`W`, `e/E`, `b/B`, `0`, `$`, `G`, `gg`, <pattern>
    * Shortcuts: `cc` (whole line), `C` (to end of line)
* `r` - replace character
    * Can take a numeric prefix to change multiple characters
* `R` - Replace text, insert style
* `s` - (substitute) delete character, enter insert mode
    * Can take a numeric prefix to change the middle part of a word
* `S` - Delete line, enter insert mode

## Delete Commands

* `d<num><type>` - Delete some text. `w`/`W`, `e/E`, `b/B`, `0`, `$`, `G`, `gg`, <pattern>
    * Shortcuts: `dd` (whole line), `D` (to end of line)
* `"<buffer name><command>` - delete into named buffer
* `x` - Delete character under cursor
* `X` - Delete character behind cursor
* Insert mode deletes:
    * `Ctrl + h` - Character
    * `Ctrl + w` - Word
    * `Ctrl + u` - Changes in line`
    * These also work in bash and ex

## Copy/Paste Commands

* `y<num><type>` - Copy some text. `w`/`W`, `e`/`E`, `b`, `0`, `$`, `G`, `gg`
    * Shortcuts: yy/Y (copy current line)
* `"<buffer name><command>` - Yank into named buffer
* `p` - Paste
* `"<num>p` - Paste buffers 1-9
    * `.` increments the number
* `"<buffer name>p` - Paste named buffer
* Yank and delete share number buffers. Yank can also use named buffers.
* `Ctrl-r0` - From insert mode- Paste the last buffer
* `Ctrl-r={expression}` - Insert an expression, such as basic math
* `Ctrl-k{character}{character}` - Add a digraph to the page, like ½ and ⅔. Look up the list of digraphs with `:h digraph-table`
* `Ctrl-v{character-code}` - Insert a character code

## QuickFix

`:Grep <pattern> <files>` / `make` generate a list that can be navigated

* `:copen` - Open quickfix list
* `:cn` / `:cp` - Next/previous line on the quickfix list
* `:ccl` - Close quickfix list

## Edit

* `J` - Join current and next line
    * Accepts numeric argument
* `~` - Change case of letter
* `>` / `<` - Change indentation
* `gu` / `gU` - Chase case
* `=` - Autoindent
* Repeating a character makes it operate on the whole line (`dd`, `yy`, `cc`, `>>`, `<<`, `==`, `gUU`, `guu`

## Undo/Repeat

* `u` - Undo last change (a change is normal -> insert -> normal)
* `U` - Undo all changes on this line
* `.` - Repeat last change
* `@:` - Repeat Ex command, macro
* `&` - Repeat last substitute command

## Text Objects

* `a` - Around
* `i` - Inside

## Increment/Decremnet

* `{count}Ctrl+a` / `{count}Ctrl+x` - Increment/Decrement next number on line

## CLI

* `:!<command>` - Execute a unix command
    * `%` references the current file name
* `:sh` - Temporarily switch to a console
    * `Ctrl+D` or `exit` to switch back
    * `Ctrl+z` / `fg` is usually quicker

## Ex Commands

* Ex takes a line address, a command, and a return.
* `|` - Execute multiple ex commands
* `:<address>r !<some unix command>` - Insert result of a unix command
* `:w !ls` - Write to STDIN
* `:r !ls` - Read from STDOUT
* `:{range}!ls` - Filter (write/read) through command
* `:t` - Copy (eg. :5,6t 9)
* `:m` - Move
* `:normal` - Execute a normal command across a range (better than a simple macro, good for repeating)
* `Ctrl+d` list options
* `Ctrl+r Ctrl+w` - Paste in currently highlighted word to ex

### Line addresses

* A number (`10`)
* A range (`1,100`)
* A relative range (`1;+8`)
* `$` (last line)
* `%` (all lines)
* `.` (current line)
* Expression (eg `$-20`)
* `+`,`++`, `-`, `--`
* `/pattern/`

### Edit Commands

* `:<lines>co<destination>` - Copy (also could use “t”)
* `:<lines>m<destination>` - Move
* `:<lines>d` - Delete
* `:<lines>w <new filename>` - Save out part of a file
* `:<lines>w >><new filename>` - Append to a file
* `:<address>r` - Read a file in

## Set Options

* `:set option` to set, `:set nooption` to unset
* `:set all` - Show all current settings
* `:set` - Show all settings that have been explicitly set
* `:set option?` - Show a specific setting

### Useful options

* `wrapmargin=15`
* `ignorecase`
* `wrapscan` (during global searches)
* `magic` (recognize wildcard characters)
* `autoindent`
* `showmatch`
* `tabstop`
* `shiftwidth`
* `number`
* `list`
* `autowrite`

## Vim Scripts

* Save ex commands in a file with a `.vim` extension
* Run it with `:source`
* Open multiple files, and then use `:argdo source batch.vim`

## Miscellaneous

* `<number><command><text>` is the same as `<command><number><text>`
* `Ctrl + G` - Show page stats at the bottom of the screen`
* The leader key is a prefix for custom hotkeys
* `ga` tells you information about the character under your cursor

## Vim philosophy

* Lean heavily on `.`- prefer it to counts. It undos/redos better.
