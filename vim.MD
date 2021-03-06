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
E
```

Jump forwards to the end of a word

```
w
```

Jump forwards to the start of the a word

```
b
```

Jump to the start of the line

```
0
```

Jump to the end of the line

```
$
```

Goto end of file

```
Shift + G
```

## Undo and Redo

`u` - Undo last change

`Ctrl-r` - Redo last change

## Search and Replace

`:substitute` - Command to search for a text pattern and replace it with a text string

`:s/foo/bar/g` - Find each occurance of foo and replace it with bar in the current line

`:%s/foo/bar/g` - Find each occurance of foo and replace it with bar

### More information

https://vim.fandom.com/wiki/Search_and_replace

## JSON

:%!jq .

## Plugins

https://github.com/junegunn/vim-plug
https://github.com/vim-airline/vim-airline
https://github.com/vim-airline/vim-airline-themes
