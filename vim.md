# Vim Cheat Sheet

## Navigation

Move the cursor

```
h
j
k
l
H
M
L
```

`w` - Jump forwards to the beginning of a word

`e` - Jump forwards to the end of a word

`b` - Jump backwards to the start of the a word

`0` - Jump to the start of the line

`$` - Jump to the end of the line

`gg` - Go to the first line of the file

`Shift + G` - Goto end of file

`Ctrl + f` - Jumps to the next page

`Ctrl + b` - Jumps to the previous page

`:123` or `123G` or `123gg` - Goto line 123

## Insert

`i` - Enter the insert mode

`A` - Append at the of the line and enter the insert mode

## Delete

`dw` - Delete from the current position to the beginning of the next word

`d0` - Delete from the current position to the beginning of the current line

`d$` or `D` - Delete from the current position to the end of the current line

`c$` or `C` - Delete from the current position to the end of the current line and enter insert mode

`dG` - Delete from the current line to the end of the file

## Visual

`v` - Enter the visual mode

`V` - Enter the visual line mode

`Ctrl + v` - Enter the block visual mode

## Copy and Paste

`yy` - yank the current line

`5yy` - yank the following five lines

`dd` - delete the line

`p` - paste the line after the current line

`P` - paste the line before the current line

## Undo and Redo

`u` - Undo last change

`Ctrl-r` - Redo last change

## Search and Replace

`:substitute` - Command to search for a text pattern and replace it with a text string

`:s/foo/bar/g` - Find each occurance of foo and replace it with bar in the current line

`:%s/foo/bar/g` - Find each occurance of foo and replace it with bar

`:%s/foo/\r/g' - Replaces foo with a new line

`:%s/\n\n/\r/g' - Replace two new lines with one new line

## Search and Command

`:g/pattern/d` - Delete all lines matching the pattern

`:g/^match/yank` - Copy all lines matching the pattern

`:g/^match/yank A` - Copy all lines matching the pattern and appends it to buffer a

`:g!/pattern/d` - Delete all lines not matching the pattern

`:v/pattern/d` - Delete all lines not matching the pattern

`:g/pattern/z#.5` - Display context (5 lines) for all occurences of a pattern

`:g/^\s*$/d` - Delete all blank lines where `^` is the start of the line `\s*` is zero or more whitespaces and `$` is the end of the line

`:g/pattern/t$` - Copy all lines matching a pattern to end of file

`:g/pattern/m$` - Move all lines matching a pattern to end of file

## Change on multiple lines

`:'<,```> normal .` - Execute the chosen command, select a new selection in the visual editor, use the given command to repeat

## Replace in multiple files

`:args *.py` - Creates a list of files on which the following commands will be executed

`:argdo %s/From/To/g` - Performs a search and replace on the list of files

`:argdo update` - Saves all files in the argument list

## Bookmark lines in files

`:marks` - Shows all bookmarks for any given file

`:ma` - Creates a bookmark called 'a'

````a` - Jump to the bookmark 'a'

## Formatting

`:%!jq .` - Formatting JSON Blocks

## Sorting

`:sort` - Sort alphabetically

`:%sort!` - Sort in reverse

`:%sort u` - Remove duplicates

## Tab Management

`gt` - Go to the next tab

`gT` - Go to the previous tab

`1gT` - Goes to the first tab as tabs are indexed from 1

`:tabe` - Opens a new tab

`:tabc` - Closes current tab

`:tabo` - Close all but current tab

## Window Management

`:split` - Horizontally split the editor

`:vsplit` - Vertically split the editor

`Ctrl + W` - Switches to an other window

`:close` - Closes the current window

`:term` - Opens a terminal window

## File Management

`:edit foo.txt` - Starts editing another file foo.txt

## JSON

:%!jq .

## Plugins

https://github.com/junegunn/vim-plug

https://github.com/vim-airline/vim-airline

https://github.com/vim-airline/vim-airline-themes
