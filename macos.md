# MacOs Cheat Sheet

## Window Management

`Ctrl + Left or Right` - Moves to fullscreen window if there is one

`Ctrl + Up` -  Shows the applications in an overview

`Ctrl + Down` - Shows the instances of an application in an overview

`Ctrl + w` - Closes the front window of an application

`Opt + Ctrl + w` - Closes all windows of an application 

`Cmd + Ctrl + f` - Opens the current application in full screen

## System Management

`sudo powermetrics --samplers smc | grep -i "CPU die temperature"` - Print the CPU die temperature

## Java

```
/Library/Java/JavaVirtualMachines

/usr/libexec/java_home -V

export PATH=/Library/Java/JavaVirtualMachines/<graalvm>/Contents/Home/bin:$PATH

export JAVA_HOME=/Library/Java/JavaVirtualMachines/<graalvm>/Contents/Home
```

## Brew

`echo $(brew --prefix)` - Shows the location where brew is installed

## Finder Dialog

`Shift + CMD + .` - Shows also hidden files toggle

`Shift + CMD + G` - Opens the go to the folder direct entry dialog 
