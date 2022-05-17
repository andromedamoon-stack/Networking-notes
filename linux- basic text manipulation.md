### Text manipulation

## stdout redirection
  > redirection operator that lets us change where the standard output goes

  ex
  - $ echo Hello World > peanuts.txt

  instead of writing Hello World on the screen it sends it to a file. If the file dosn't exist it will create the file

  if you don't  want to overwrite your text file use
    -$ echo Hello World >> peanuts.txt

##stdin 
< 
- cat < peanuts.text > banana.tx

the cat command normally sends a file to become the stdin, however in the example above we redirected peanuts.txt to be our stdin. 

the output of the peanuts.txt, Hello World, gets redirected to the banana.txt file.

## stderr Standard Error
-is the default file descriptor where a process can write error messages.

-In the terminal, standard error defaults to the user's screen.

-In bash, standard error can be redirected on the command line. Redirecting stderr can be useful if you need to capture any error messages to a separate log file, or hide the error messages entirely.

## pipe and tree
|   
-allows you to get the stdout of a command and make that stdin to another process

ex
-$ ls -la /etc | less

we took the stdout of ls -la and piped it into the less command

if you wanted to write the output of my command to two different streams:

-$ ls| tee peanuts.tx

output is on your screen and in the file

## env Enviroment
env ouputs information about the enviroment variables you currently have set.

- one important variable is the PATH.  you can access them by sticking a $ in front of the variable name

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/bin

## cut command
extracts portion of a text from a file

$ cut -c 5 sample.txt

- outputs the 5th character in each line of the file

the -f flag ( field tag) buts based off fields, by default it uses TAB's as delimiters, so everything separated by a TAB is considered a field

you can combine the -f flag with the -d (delimiter) flag to extract by a custom delimiter

## paste

-similar to the cat command in that it merges lines together in a file. 

## head 

if you want to se ejust the first few lines in a text file the head command shows you the first 10 lines.

 head /var/log/syslog

 you can also use the -n flag to modify the number of lines you want it to show

## tail

tail is also similar to the head command in that you see the last 10 lines by default

$ tail /var/log/syslog

## expand and unexpand

expand to change the TABs space you want

$ expand sample.txt

The command above will print output with each TAB converted into a group of spaces. To save this output in a file, use output redirection like below.

$ expand sample.txt > result.txt

unexpand converts back the group of spaces 

$ unexpand -a result.txt

## join and split

The join command allows you to join multiple files together by a common field

You can also split a file up into different files with the split command:

$ split somefile

This will split it into different files, by default it will split them once they reach a 1000 line limit. The files are named x** by default. 

## sort

useful for sorting lines

-r flag for reverse sort
-n sort for numerical value

## translate

translate a set of characters into another set of characters

$ tr a-z A-Z

hello

HELLO

## uniq

useful for parsing text

if you have a file with alot of duplicates you can use the uniq command to remove them if they are adjacent
 
 -c 
 count how many occourances
 -u
 unique values
 -d 
 duplicate values

## wc & nl

wc shows the total count of words in a file
$ wc -l /etc/passwd

96

no shows the number of lines in a file

## grep

this command lets you search files for characters that match a certain pattern. 

ex.

$ grep fox sample.txt

You should see that grep found fox in the sample.txt file.

You can also grep patterns that are case insensitive with the -i flag:

$ grep -i somepattern somefile

To get even more flexible with grep you can combine it with other commands with |.

$ env | grep -i User

As you can see grep is pretty versatile. You can even use regular expressions in your pattern:

$ ls /somedir | grep '.txt$'

Should return all files ending with .txt in somedir. 