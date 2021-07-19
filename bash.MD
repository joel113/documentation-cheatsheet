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
`Ctrl-k` - Kill to the end of the line
`Ctrl-u` - Kill to the beginning of the line
`Ctrl-y` - Yanks the line
`Ctrl-w` - Kill to the next whitespace of the line
`Ctrl-x-e` - Edits the current command in an editor

`alt-.` - Repeats the previous argument

## Moving

`mv file{,extension}.log` - Appends "extension" to the file name

## Renaming

`for f in *.pdf; do mv "$f" "$(date "+%Y%m%d"-"$f").pdf"; done` - Prepends file date to the file name

`for f in *.*; do mv -v "$f" "${f:11}"; done`- Removes first eleven characters from a filename

## Editing

`tr --delete '\n' < file.txt` - Removes newline character from file.txt
`tr -d '\n' < file.txt > newfile.txt` - Removes newline character from file.txt and writes the result to newfile.txt


## Tailing

`less +f` - Less and follow (shift-f to reattach after scrolling)

## Compression

`tar -zcvf archive.tar.gz directory-name` - Tar.gz a whole directory

## Curl

`curl -h "Accept-Encoding: gzip" -I https://www.google.com` - Retrieves a web page asking for a gzip compression

## Files

`lsof -u joel` - Gets the open files of the user joel
`kill -9 `` ` ``lsof -t -u joel`` ` ``` - Kills all open files of the user joel
`lsof -i :8090-9090` - Gets the connections between port 8090 and 9090
`lsof -p 23619` - Gets the process of pid 23619

## Networking

`netstat -tulpn` - Gets all ports in use

## Administration

`sudo !!` - Reruns to the previous command with sudo prepended

## Processes

`ps -ef` - Gets all processes
`ps aux --sort=-%mem` - Gets all processes and sorts them by memory 

## Text Processing

`sort -u input.txt` - Remove duplicates with sort command
`awk '!a[$0]++` - Remove duplicates with awk command
`tr -d '[:space:]'` - Remove space characters, form feeds, new-lines, carriage returns, horizontal tabs, and vertical tabs
`tr -d .` - Remove . character from the string
`sed -r 's/[xyz]+/_/g'` - Remove some characters from the passed string
`grep -oh "\w*th\w*" *` - Match some characters from the passed string
`echo "${s%%.*}" - Match some characters from the passed string

### Json Processing

`cat example.json | jq '.'` - Print a json file nicely formatted
`cat example.json | jq '.[0]' - Print the first element of a json file nicely formatted
`cat example.json | jq '.[0]["greeting"]' - Print the greeting element of the first element of a json file nicely formatted

### AWK

`ps | awk '{print $1}'` - Print the first column of each line
`cat /etc/passwd | awk -F ":" '{print $1}'` - Use a different column separator than space and print the first column
`awk -F ":" '{print $1} /etc/passwd` - A different notation to use a different column separator than space and print the first column
`awk 'BEGIN{FS=":"; OFS="-"} print $1,$6,$7}' /etc/passwd` - Replace a field separator with another field separator and print some columns
`cat /etc/shells | awk -F "/" '/^\// {print $NF}' | uniq` - Last field when searching for a pattern
`df | awk '/\/dev\/loop/ {print $1 $4 + $5}'` - Again awk but having a sum of $4 and $5
`cat /etc/shells | awk 'length($0) > 7'` - Print only the lines which have a first column length of longer than 7
`awk 'BEGIN { for(i=1; i<=10; i++) print "The square root of",i,"is",i*i;}'` - Kind of programming in AWK
`cat /etc/shells | awk '{print substr($0,4)}'` - Use the substr function of AWK
`df | awk 'NR==7, NR==11 {print NR, $0}'` | Print line 7 to 11 and print the line including the line number
