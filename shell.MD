# Shell (ZSH) Cheat Sheet

## Cursor

`Ctrl-a` - Moves the cursor to the beginning of the line

`Ctrl-e` - Moves the cursor to the end of the line

`Option-RightArrowKey` - Moves the cursor forward by a word

`Option-LeftArrorKey` - Moves the cursor backward by a word

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

## Variables

`ls -ld $(date +%B).txt` - Performs a command substitution which embeds the result in an another command

Performs a command substitution which considers a variable $var1.

```
var2=$(echo "$var1")
```

## Generating

`openssl rand -base64 12` - Generates a base64 string with a length of 12

`openssl rand -hex 13` - Generates a hex string with a length of 1## Generating

## Tailing

`less +f` - Less and follow (shift-f to reattach after scrolling)

## Piping

`cat somefile | tee -a log.txt | cat > /dev/null` - Log output but not show on the console

## Iterating

```
for COLOR in red white; do
< wine-$COLOR.csv tr '[A-Z]; ' '[a-z],_' | tr -d \" > wine-${COLOR}-clean.csv
done
```

Iterates the string list 'red white' and applies it to the line which follow do and prepends done. tr replaces and deletes some characters.

```
`for i in {0..100..2}
> do
> echo "$i^2" | bc
> done | trim
```

Iterates from 0 to 100 with steps of 2 and passes the value to bc.

```
$ while read line                          
> do
> echo "Sending invitation to ${line}."    
> done < emails 
```

Reads from the stdin an echos some text.

```
$ for chapter in /data/*
> do
> echo "Processing Chapter ${chapter}."
> done
```

Loops over files in a directory.

```
$ while read line; do
> echo "$line"
> done < "$filename"
```

Loops over the lines of a file.

`$ seq 0 2 100 | parallel "echo {}^2 | bc" | trim` - Iterates a sequence and passes the value to a parallel execution of bc

## History

`fc` - Fix or change a really long command that you run last with a text editor

` ls -s` - Don't add a command to the history

`ls $_` - Rerun a command (i.e. ls) with the last argument

`ls !$` - Rerun a command (i.e. ls) with the last argument

## Compression

`tar -zcvf archive.tar.gz directory-name` - Tar.gz a whole directory

## Curl

`curl -h "Accept-Encoding: gzip" -I https://www.google.com` - Retrieves a web page asking for a gzip compression

## Date

`date +"%Y%m%d-%H%M%S"` - Return a formatted datetimestamp

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

`grep -rn /foobar/ -e text_to_find` - Find a text in a directory resursively

`echo "${s%%.*}" - Match some characters from the passed string

## Calculating

`echo "4+2" | bc` - Basic caluclator which adds 2 to 1

## Json Processing

`cat example.json | jq '.'` - Print a json file nicely formatted

`cat example.json | jq '.[0]' - Print the first element of a json file nicely formatted

`cat example.json | jq '.[0]["greeting"]' - Print the greeting element of the first element of a json file nicely formatted

`cat example.json | jq --arg e "${variable}" '.data[$e] += ["test1"]'` - Pass a variable or environment variable to jq to use it in a jq operation

## Csv Processing

```
csvstack -g red,white -n type wine-{red,white}-clean.csv | 1
xsv select 2-,1 > wine.csv
```

Combines two csv files to a single file using xsv select as well as csvstack

## AWK

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

## Image Processing

`exiftool -d '%Y%m%d-%H%M%S.jpg' '-filename<CreateDate' .` - Rename file names of pictures and use a formatted datetimestamp

## Video Processing

`ffmpeg -i input.mts -c:v copy -c:a copy -f mp4 output.mp4` - Converts a mts into a mp4 video

`ffmpeg -i input.mp4 -vcodec libx265 -crf 30 output.mp4` - Convers a mts into a libx265 encoded video

## Security and SSL/TLS

`openssl x509 -in keyname.pem -text` - Prints the content of a certificate

## Docker

`docker run -it -rm alpine` - Runs an alpine image and logs into the shell

## Printing

`tldr` - Shows simplified and community-driven man pages

`bat` - Cat clone with syntax highlighting and git integration

`bat -A file.csv` - Pretty prints a csv and shows also non-printable characters

## Searching

`find /tmp -name 'foo.txt'` - Search for a file called foo.txt

## Sorting

`sort -u` - Sorts and removes duplicates

## More Commands

`watch docker ps` - Watch a command

`ls -1 | parallel echo` - Parallel echo

`parallel --jobs 2 ./slow.sh ::: {A..C}` - Parallel execution of a slow shell script

`cmp <file1> <file2>` - Compares the difference between two files

`comm <file1> <file2>` - Find lines in common

`script <filename>` - Record a log of your terminal session

`jot <number>` - Generate test data with jot
