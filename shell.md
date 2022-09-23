# Shell (ZSH) Cheat Sheet

## Metacharacters

`|` - Pipes the result of a command into a subsequent command

`>` - Redirects the output of the result of a command

`2>` - Redirects the stderr as output of a command

`*` - Asterisk * or wildcard

`~` - Home directory shortcut

`$` - Any string which ends with a given string, e.g.: 'png$'

`^` - Any string which starts with a given string, e.g.: '^$Screen'

## Cursor

`Ctrl-a` - Moves the cursor to the beginning of the line

`Ctrl-e` - Moves the cursor to the end of the line

`Option-RightArrowKey` - Moves the cursor forward by a word

`Option-LeftArrorKey` - Moves the cursor backward by a word

`Ctrl-t` - Swaps the current character with the one preceding it

`Ctrl-l` - Clears the screen

`Ctrl-r` - Reverse search

`Ctrl-s` - Reverses the search direction

`Ctrl-g` - Leave the search

## Cut and Yank

`Ctrl-k` - Cut / kill to the end of the line

`Ctrl-u` - Cut / kill to the beginning of the line

`Ctrl-y` - Yanks the line

`Ctrl-w` - Cut / kill to the previous whitespace of the line

`Alt-d` - Cut / kill to the next whitespace of the line

`Ctrl-x-e` - Edits the current command in an editor

`alt-.` - Repeats the previous argument

## Operators

`sudo !!` - !! expands into the previous command

`sudo !N` - !N expands into the nth previous command in the history list

`ls !$` - !$ expands into the previous command's last parameter

`ls index.*` - Matches any file with an arbitrary file ending

`ls index.???` - Match any file with a three letter file ending

## Navigtaion

`pushd /var/www/html` - Changes directory and pushes the directory on the stack

`dirs` - Shows the current directories on the stack

`popd` - Changes directory and pops the directory from the stack

`(cd /pathtosome/dirc; somecommand)` - Executes somecommand in a subshell in a specific directory

## History

`history` - Shows the history commands entered in the shell

`history 3` - Shows the previous three command of the history

`history | sort -nr | less` - Shows the latest to earliest entry in less

`history | grep -w cd` - Shows the historical commands containing the word cd

`history -c` - Clears the history

`echo $HISTSIZE` - Shows the history size

`echo $HISTFILE` - Shows the location of the shell history

`HISTCONTROl=ignoredups` - Sets the variable which ignores duplicates in the history

`!!` - Repeats the previous command even if it was only printed

`!grep` - Repeats the most previous command starting with grep

`!?grep?` - Repeats the most previous command containing grep

`!-3` - Repeats the third previous command from the history

`!-3:p` - Prints the third previous command from the history

`!!:s/jg/jpg/ - Repeats the previous command but replaces jg with jpg

## Commands

`eval $command` - Runs a command stored in a variable (breakout possible!)

`which cp` - Locates a command in the search path

`type cp` - Locates a command in the search path including aliases, functions and shell builtins

`echo $PATH | tr : "\n"` - Shows the directories of the search path

`alias` - Shows the available aliases

`source .zshrc` - Rereads a configuration file

`cd dir && touch new.txt` - Conditional list of commands where the second command is only executed if the first command was successful

`cd dir || mkdir dir` - Conditional list of commands where the second command is only executed if the first command was not successful

`sleep 300; echo "remember to walk the dog"` - Unconditional list where the second command is executed if the first command is done

`mv $(grep -l "Artist: Kansas" *.txt) kansas` - Command substitution

`diff <(ls *.jpg | sort -n) <(seq 1 1000 | sed 's/$/.jpg/'` - Process substitutuion where `<(` performs the commands in a new process

`bash -c "ls -l"` - Passes the given command to a new shell

`echo "ls -l" | bash` - Pipes the given command to a new shell

`echo "ls -" > outfile" | ssh -T myhost.example.com` - Passes a given command to a remote host using ssh

## Redirecting

`ls > output` - Redirects the stdout

`cp nonexistent.txt file.txt 2> errors` - Redirects the stderr

`cp nonexistent.txt file.txt 2>> errors` - Redirects the stderr and appends to erros

`ls &> output` - Redirects both stdout and stderr

## Qoutes

`echo 'filename with spaces.txt'`

`echo "filename with spaces.txt'`

`echo filename\ with\ spaces.txt`

`echo "with double quotes $VARIABLES are evaluted"`

`echo 'with single quotes $VARIABLES are not evaluated"`

`echo "with double quotes \$VARIABLES are not evaluated if the \$ is esacaped"`

## Here

`cat <<< 'hello'` - Passses a here string to the cat command

`cat <<EOF` - Passes a here document to the cat command

`bat < /home/foobar` - Passes the foobar file to the bat command std in

## Xargs

`find . -name "*.tmp" -print0 | xargs -0 rm` - Passes the result of the first command to the second command using xargs

`ls | xargs -I XYZ echo XYZ is my favorite food` - Passes the result of ls to xargs where XYZ is a placeholder for the passed argument

## Moving

`mv file{,extension}.log` - Appends "extension" to the file name

## Renaming

`for f in *.pdf; do mv "$f" "$(date "+%Y%m%d"-"$f").pdf"; done` - Prepends file date to the file name

`for f in *; do mv $f "$(echo $f | sed s/20211100/20211109/g)"; done` - Renames files using sed search and replace

`for f in *.*; do mv -v "$f" "${f:11}"; done`- Removes first eleven characters from a filename

Renames file ending of all files matching *.txt, where `*.txt` is a globbing pattern, `--` marks the end of the option list, `${f%.txt}` is a parameter expansion

```
for f in *.txt; do 
    mv -- "$f" "${f%.txt}.text"
done
```

## Editing

`tr --delete '\n' < file.txt` - Removes newline character from file.txt

`tr -d '\n' < file.txt > newfile.txt` - Removes newline character from file.txt and writes the result to newfile.txt

## Replacing

`echo bla | tr 'abcd' 'jkm'` - Replaces all occurences of a character with another character

`echo foobar | sed 's/bar/bla/'` - Replaces the first occurence of bar with bla

`echo foobar | sed 's/bar/bla/g'` - Replaces all occurences of bar with bla

## Removing

`echo foobar | cut 2- | rev | cut 2- | rev` - Removes the first and the last character of a string

## Extracting

`ls -l /usr/lib | cut -c1` - Lists the /usr/lib directory and extracts the first column

`cut -f1 grades | sort | uniq -c` - Extracts the first column from grades, sorts and counts unique elements

`cut -f3 file.txt | sort -nr | head -n1` - Extracts the third column, sorts reverse and shows the first element`

`head -n5 /etc/passwd | cut -d: -f1` - Extracts the fifth column of /etc/passwd and extracts the first column using the : delimiter

`md5sum *.jpg | cut -c1-32 | sort | uniq -c` - Takes a subpart of the md5sum, sorts and counts duplicates

## Brace Expansion

`echo {1..10}` - Prints numbers from 1 to 10

`echo {10..1}` - Prints the numbers from 10 to 1

`ls file{2..4}` - Lists the files file2 file3 and file4

`ls file[2-4]` - Matches existing filesnames as square brackets are pattern matching

## Variables

`touch count-{123}.txt` - Generatres three files count-1.txt, count-2.txt and count-3.txt

`touch count-{1..3}.txt` - Generates the same files as above

`ls -ld $(date +%B).txt` - Performs a command substitution which embeds the result in an another command

`echo ${animal}s` - Performs a parameter substitution where a character immediately follows the variable name

`mkdir dir && cd $_` - Creates a command while changing directory to it as $_ holds the argument passed to the previous command

Performs a command substitution which considers a variable $var1.

```
var2=$(echo "$var1")
```

## Generating

`yes` - Repeats print the character y until terminated

`yes woof!` - Repeats printing woof! until terminated

`openssl rand -base64 12` - Generates a base64 string with a length of 12

`openssl rand -hex 13` - Generates a hex string with a length of 1## Generating

## Tailing

`less +f` - Less and follow (shift-f to reattach after scrolling)

## Job Control

`dosth &` - Runs the command in the background, the process can be stopped using ctrl+z and continue it with bg or in the foreground with fg

`nohup dosth &` - Runs the command in the background while decoupeling it from unix signals

`dosth &> /dev/null &` - Runs the command in the background while detaching it from the output/error streams of the shell

`jobs` - Shows the currently running jobs

`fg` - Return to the background job

`fg %2` - Return to the background job 2

`kill %2` - Kill the background job 2

`Ctrl-C` - Kill the current foreground job

`Ctrl-Z` - Pause the current foreground job

`bg` - Background and resume a job again

`echo "command_to_be_run" | at 09:00` - Runs the given command at 9 am

`at 09:00 -f /home/linux/script.sh` - Runs the given command at 9 am

## Piping

`cat somefile | tee -a log.txt | cat > /dev/null` - Log output but not show on the console

## Variables

`export E="I am an environment variable` - Sets an environment variable

`L="I am just a local variable` - Sets a local variable

## Iterating

```
for dir in */; do
	zip -r ${dir}.zip $dir
done
```

Iterates through the directories in the current directory and zips the directories.

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

`ls -s` - Don't add a command to the history

`ls $_` - Rerun a command (i.e. ls) with the last argument

`ls !$` - Rerun a command (i.e. ls) with the last argument

## Compression

`tar -zcvf archive.tar.gz directory-name` - Tar.gz a whole directory

## Curl

`curl -h "Accept-Encoding: gzip" -I https://www.google.com` - Retrieves a web page asking for a gzip compression

## RSync

`rsync -avu --delete "/home/user/A/" "/home/user/B"` - Syncs the files of A into B while preserving the file system attributes, verbosly, with a newer modification time and delete if a file does not exist in the source

## Web Sockets

`wscat -c ws://websocket-echo.com` - Connects to host via web sockets

## Date

`date +"%Y%m%d-%H%M%S"` - Return a formatted datetimestamp

`date` - Prints the date in the default format

`date +%Y-%m-%d` - Prints the date in the year-month-day format

`date +%H:%M:%S` - Prints the date in the hours:minute:second format

`date +"I cannot believe it's already %A!"` - Prints the day within a sentence

`cal` - Shows a calendar in the terminal

## Files

`lsof -u joel` - Gets the open files of the user joel

`kill -9 `` ` ``lsof -t -u joel`` ` ``` - Kills all open files of the user joel

`lsof -i :8090-9090` - Gets the connections between port 8090 and 9090

`lsof -p 23619` - Gets the process of pid 23619

## Networking

`netstat -tulpn` - Gets all ports in use

`iftop` - Shows network traffic

`lspci | egrep -i 'network|ethernet'` - List network interfaces

`curl ip.sb` - Shows the current ip

`curl ifconfig.me` - Shows the the current ip

## Administration

`sudo shutdown -h 19:05 "Some message..."` - Shutdown at a specific time

`sudo !!` - Reruns to the previous command with sudo prepended

`sudo systemctl start servicename` - Starts a service using systemd

`sudo systemctl stop servicename` - Stops a service using systemd

`sudo systemctl restart servicename` - Restarts a service using systemd

`sudo systemctl status servicename` - Checks the status of a service using systemd

`sudo systemctl enable servicename` - Enables a service using systemd

`sudo systemctl disable servicename` - Disables a service using systemd

`sudo systemctl edit servicename` - Edits a systemd unit file with an overwrite

`sudo journalctl -u servicename` - Shows the logs of a servvice

`crontab -e` - Edits the cronjobs

## System Management

`htop` - Shows the system resources as an alternative to top

`btop` - Shows the system resources as an alternative to top

## Processes

`ps -ef` - Gets all processes

`ps aux --sort=-%mem` - Gets all processes and sorts them by memory 

`pgrep chrome` - Helps to quickly find the process id of the chrome application

`sudo lsof -i :3000` - Returns the process id of the application hodling the 3000 port

## Text Processing

`sort -u input.txt` - Remove duplicates with sort command

`awk '!a[$0]++` - Remove duplicates with awk command

`tr 'a-z' 'A-Z'` - Replaces lower case with upper case letters

`tr -d '[:space:]'` - Remove space characters, form feeds, new-lines, carriage returns, horizontal tabs, and vertical tabs

`tr -d .` - Remove . character from the string

`sed -r 's/[xyz]+/_/g'` - Remove some characters from the passed string

`grep -oh "\w*th\w*" *` - Match some characters from the passed string

`grep -rn /foobar/ -e text_to_find` - Find a text in a directory resursively

`echo "${s%%.*}"` - Match some characters from the passed string

`tac poem1.txt poem2.txt`- Reverses the lines of a file line by line

`paste poem1.txt poem2.txt` - Combines the lines of files side by side line by line

`diff file1 file2` - Compares two files line by line

`tr` - Translates characters into other characters

`rev` - Reverses characters on a line

`awk` and `sed` - General purpose transformers

`pandoc -f markdown readme.md > readme.html` - Converts markdown into html

## Calculating

`echo "4+2" | bc` - Basic caluclator which adds 2 to 1

## Binary Data Processing

`echo "abcd" | xxd -r -p | base64` - Turn a hex encoded string into a base64 encoded string

`echo "foobar" | base64 --decode | od -t x1 -An` - Turn a base64 encoded string into a hex encoded string

`echo -ne "\x1e\x07" | od -t x1` - Turns a unicode bytes into a hex encoded string

`truncate -s -1 file` - Removes one byte from the file

## Json Processing

`cat example.json | jq '.'` - Print a json file nicely formatted

`cat example.json | jq '.[0]'` - Print the first element of a json file nicely formatted

`cat example.json | jq '.[0]["greeting"]'` - Print the greeting element of the first element of a json file nicely formatted

`cat example.json | jq --arg e "${variable}" '.data[$e] += ["test1"]'` - Pass a variable or environment variable to jq to use it in a jq operation

`jq <<< {}` - Creates an empty json document

`jq '."my_arg"="my_val"' <<< {}` - Creates a json document containing only my_arg and my_val

```
$ command="sleep '5'; echo 'done here'"
$ jq --arg key "commands" --arg value "$command" '.[$key]=[$value]' <<< {}
```

Creates a json document containing a key and a value passed by arguments.

## Csv Processing

```
csvstack -g red,white -n type wine-{red,white}-clean.csv | 1
xsv select 2-,1 > wine.csv
```
Combines two csv files to a single file using xsv select as well as csvstack

```
in2csv input.xlsx > input.csv
```

Converts an excel file into csv file

## Image Processing

`exiftool '-filename<CreateDate' -d %y%m%d_%H%M%S%%-c.%%le *` - Renames a list of pictures with respect to the exif date

`convert -resize x16 -gravity center -crop 16x16+0+0 avatar.png -flatten -colors 256 -background transparent favicon.ico` - Converts an image to a favicon

`for file in 202208*_*.jpg; convert $file -resize 1000x750 resized/$file` - Converts files matching the pattern to a certain size

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

## SSH

`ssh -f -N -D 127.0.0.1:8080 remoteserver` - Creates a socks proxy for application level fowarding

`curl --proxy socks5h://127.0.0.1:8080 https://remote.remoteserver` - Requests a remote server via a socks proxy

## Printing

`tldr` - Shows simplified and community-driven man pages

`bat` - Cat clone with syntax highlighting and git integration

`bat -A file.csv` - Pretty prints a csv and shows also non-printable characters

## Searching

`find /tmp -name 'foo.txt'` - Search for a file called foo.txt

## Sorting

`sort -u` - Sorts and removes duplicates

## More Commands

`df -k` - Shows disk usage information

`lscpu` - Shows CPU usage information

`man hier` - Shows a description of the file system hierarchy

`uptime` - Shows the uptime of the machine

`watch docker ps` - Watch a command

`watch -n 5 echo "foobar"` - Watch a command every 5 seconds

`ls -1 | parallel echo` - Parallel echo

`parallel --jobs 2 ./slow.sh ::: {A..C}` - Parallel execution of a slow shell script

`cmp <file1> <file2>` - Compares the difference between two files

`comm <file1> <file2>` - Find lines in common

`script <filename>` - Record a log of your terminal session

`jot <number>` - Generate test data with jot

`uname -a` - Shows kernel release information

## Samba Administration

`smbpasswd -a username` - Readd a user to reset the password

`smbpasswd -U username` - Change the password

## Shell Programming

`if [[ $var ]]; then` - var is set and not empty

`if [[ ! $var ]]; then` - var is not set or it is set to an empty string
