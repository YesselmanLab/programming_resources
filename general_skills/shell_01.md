Welcome to the first shell tutorial in the Yesselman Group's general programming repo
# Part I: What is the shell? Why use it? How does it work? 
A shell is a low-level, command-line interface (CLI) that lets you directly access a computer's resources. Shells have been in use since the 70s and are probably what you have seen in movies when a "hacker" is on screen (Dennis Nedry in Jurassic Park, for example). Despite their age the emergence of Graphic User Interfaces (GUIs), shells remain a critical tool for any developer or scientific developer. In practice, the shell is accessed via the terminal on Max/Linux or PowerShell on
windows. At this point it is worth mentioning that the following lesson is designed for a Mac/Linux style shell, **NOT** Windows Powershell. Though Powershell has come a long way and the Windows Terminal is converging with the Linux version [somewhat](https://www.theverge.com/2019/5/6/18527870/microsoft-windows-terminal-command-line-tool), many of the below commands/methods will not work on windows. Likewise, it is worth noting there are a variety of shells available including bash, csh, zsh, dash, to name a few. In this series we will be focusing on bash, which is one of the most commonly used. Don't worry though, most of the skills established in bash seamless transfer to other shells.

Now that you understand what a shell is, you might be worndering why you should use it. In practice, the utility of the shell comes from a few core qualities:
    
    + customizability: A shell is highly tunable and can have its astethics and functionality set to the user's desires. It is extremely common to customize your shell's command prompt with appealing colors and also program in hot-keys.
    + efficiency: Shells generally have very low overhead which helps to conserve resources for higher priority tasks. This efficeincy is why CLI tools have persisted for 50 years as GUI tools frequently consume considerable resources, hampering performance.
    + flexibility: Each shell is very modular and allows the user to easily combine desired functionalities. Unlike coding in C++, Python or Javascript, alterations to a shell command can be interpreted instantaneously. 
    + workflow improvement: Shells are extremely powerful and you will quickly find that they will improve your workflow and efficiency. the tools they provide target many common tasks in software development/usage including file writing, content searching, file deletion, data wrangling and more.

More generally, shell tools have been developed BY software users FOR software users, so many common tasks can be handled with these tools.

At this point you're probably wondering how to actually *use* the shell. The basic format is shown below:

`$ [COMMAND] [OPTIONS] [INPUT]`

This is all done on the commandline, or terminal, which is denoted with the `$` symbol. To run the command, you press enter. 
