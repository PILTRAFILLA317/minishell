     ________  ________  ________  ___  ___  ________  ________  ________     
    |\   __  \|\   __  \|\   ____\|\  \|\  \|\   __  \|\   ___ \|\   __  \    
    \ \  \|\ /\ \  \|\  \ \  \___|\ \  \\\  \ \  \|\  \ \  \_|\ \ \  \|\  \   
     \ \   __  \ \   __  \ \_____  \ \   __  \ \   __  \ \  \ \\ \ \  \\\  \  
      \ \  \|\  \ \  \ \  \|____|\  \ \  \ \  \ \  \ \  \ \  \_\\ \ \  \\\  \ 
       \ \_______\ \__\ \__\____\_\  \ \__\ \__\ \__\ \__\ \_______\ \_______\
        \|_______|\|__|\|__|\_________\|__|\|__|\|__|\|__|\|_______|\|_______|
                           \|_________|                                       

 
#   minishell
Simple Shell system based on BASH for 42cursus-minishell

# Table of contents  
1. [Introduction](#introduction)  
2. [How BASHado works](#how-bashado-works)  
    1. [Lexer](#lexer)  
    3. [Parser and Expander](#parser-and-expander)  
3. [Another paragraph](#paragraph2)  

# Introduction
## Features  

- Functional history
- Finder and executor of any executable (in PATH)
- **echo**, **cd**, **pwd**, **export**, **unset**, **env** and **exit** builtins
- Functional expander with "$"
- **<**, **>**, **<<** and **>>** redirections
- Pipes ( **|** )
- **ctrl + C**, **ctrl + D** and **ctrl + 4** signals
- Working on Linux and Mac :D

## Run Locally  

Clone the project  

~~~bash  
  git clone https://github.com/PILTRAFILLA317/minishell
~~~

Go to the project directory  

~~~bash
  cd minishell
~~~

Install readline

- Mac

~~~bash  
brew install readline
~~~

- Linux

~~~bash  
sudo apt-get install libreadline6 libreadline6-dev
~~~

Compile

~~~bash  
make bonus
~~~

Run 

~~~bash  
./minishell_bonus
~~~

Clean executable and temp files

~~~bash  
make fclean_all
~~~

# How BASHado works
## Lexer
The first thing to do is to remove extra spaces  at the beginning, between arguments, and at the end.
Let's take an example:

~~~bash  
BASHado >       l"s" "-la"   |grep 'e' | wc -l   >a && echo       "  '$USER'"
~~~

It will end up like this
~~~bash  
BASHado > l"s" "-la" |grep 'e' | wc -l >a && echo "  '$USER'"
~~~

Then it separates the arguments so that they can be well executed.
The lexer receives this string and separates it by spaces, pipes, and redirects, regardless of those inside the single or double quotes.
The example string would look like this:
~~~bash  
- l"s"
- "-la"
- |
- grep
- 'e'
- |
- wc
- -l
- >
- a
- &&
- echo
- "  '$USER'"
~~~

Now pipes, redirects and other characters that affect the executor are replaced by words that differentiate them from those inside quotes.
After lexing the example string would look like this:
~~~bash  
- l"s"
- "-la"
- <PIPE>
- grep
- 'e'
- <PIPE>
- wc
- -l
- <GREATER>
- a
- <DOUBLEAMPERSAND>
- echo
- "  '$USER'"
~~~

## Parser and Expander

The first thing the parser does is to separate the quotation marks that are inside another argument.
In this case only *l"s"* contains quotation marks. The double array would look like this:

~~~bash  
- l
- "s"
- "-la"
- <PIPE>
- grep
- 'e'
- <PIPE>
- wc
- -l
- <GREATER>
- a
- <DOUBLEAMPERSAND>
- echo
- "  '$USER'"
~~~

Now, the quotes at the beginning and end of the arguments are removed and arguments that do NOT have single quotes are sent to the expander before being put back together. The expander checks if there is a "$" inside and if it is expandable by any environment variables.

In this case only *"  '$USER'"* will be expanded.

The expander ignores everything before the "$" and puts it in a string, then takes from the "$" to another "$", a space or a character that is NOT a special character (in the case of BASHado these special characters are from 33 to 64 of the ASCII table without considering the numbers).
So *"  '$USER'"* will end up like:

~~~bash
-   '
- $USER
- '
~~~

Now $USER is replaced with the environment variable with the same name, in this example *USER=username*.

~~~bash
-   '
- username
- '
~~~

After Parser and Expander the final double array would look like this:
~~~bash  
- ls
- -la
- <PIPE>
- grep
- e
- <PIPE>
- wc
- -l
- <GREATER>
- a
- <DOUBLEAMPERSAND>
- echo
-   'username'
~~~

**Observations**

Bash (and BASHado) manages the quotes so that when he finds one, whether it is single or double, it takes what is inside that one and the next one the same as it finds, whatever is inside.
For example:
~~~bash
BASHado > ""'hello'""
~~~
Bash will take:
~~~bash
- ""
- 'hello'
- ""
~~~

## Executor
### Executor linked list

## Special Thanks
