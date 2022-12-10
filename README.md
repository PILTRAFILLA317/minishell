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

Start the server  

~~~bash  
npm run start
~~~

## Screenshots  

![App Screenshot](https://lanecdr.org/wp-content/uploads/2019/08/placeholder.png)

## Environment Variables  

To run this project, you will need to add the following environment variables to your .env file  
`API_KEY`  

`ANOTHER_API_KEY` 

## Acknowledgements  

- [Awesome Readme Templates](https://awesomeopensource.com/project/elangosundar/awesome-README-templates)
- [Awesome README](https://github.com/matiassingers/awesome-readme)
- [How to write a Good readme](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)

## Feedback  

If you have any feedback, please reach out to us at fake@fake.com

## License  

[MIT](https://choosealicense.com/licenses/mit/)
