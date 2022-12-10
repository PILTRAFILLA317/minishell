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
2. [Some paragraph](#paragraph1)  
    1. [Sub paragraph](#subparagraph1)  
3. [Another paragraph](#paragraph2)  

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
## lexer
The first thing to do is to separate the arguments so that they can be well executed.
Let's take an example:
~~~bash  
BASHado > ls "-la" |grep 'e' | wc -l >a && echo "  '$USER'"
~~~
The lexer receives this string and separates it by spaces, pipes, and redirects, regardless of those inside the single or double quotes.
The example string would look like this:
~~~bash  
- ls
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
- ls
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
**Observations**

Bash (and BASHado) manages the quotes so that when he finds one, whether it is single or double, he takes what is inside that one and the next one the same as he finds, whatever is inside.
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

## Parser and Expander

## Screenshots  

![App Screenshot](https://lanecdr.org/wp-content/uploads/2019/08/placeholder.png)

## Special Thanks
