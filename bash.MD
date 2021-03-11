# Bash Cheat Sheet

## Cursor

`Ctrl-a` - Moves the cursor to the beginning of the line
`Ctrl-e` - Moves the cursor to the end of the line
`Option-b` - Moves the cursor forward by a word
`Option-f` - Moves the cursor backward by a word
`Ctrl-l` - Clears the screen
`Ctrl-r` - Reverse search
`Ctrl-s` - Reverses the search direction
`Ctrl-g` - Leave the search

## Moving

`mv file{,extension}.log` - Appends "extension" to the file name

## Compression

`tar -zcvf archive.tar.gz directory-name` - Tar.gz a whole directory

## Text Processing

`sort -u input.txt` - Remove duplicates with sort command
`awk '!a[$0]++` - Remove duplicates with awk command
`tr -d '[:space:]'` - Remove space characters, form feeds, new-lines, carriage returns, horizontal tabs, and vertical tabs
`tr -d .` - Remove . character from the string
`sed -r 's/[xyz]+/_/g'` - Remove some characters from the passed string
`grep -oh "\w*th\w*" *` - Match some characters from the passed string
`echo "${s%%.*}" - Match some characters from the passed string
