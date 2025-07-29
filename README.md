# Unix Command Intro for Windows Folks

Just a little unix command intro for some family members that have always used only windows.

## First Things First

- Watch this video: https://www.youtube.com/watch?v=yoZ910JQzrg
- Install Git Bash on your Windows system
- When installing, select the option to add a desktop Git Bash icon
- Installer: https://gitforwindows.org/

## Git is a Version Control System

But we aren't starting there. We're just using it because they provide a nice Bash (Born Again Shell) Unix command line emulator for Windows.

If you want to learn about Git:

- https://git-scm.com/docs
- https://git-scm.com/docs/gittutorial
- https://www.youtube.com/watch?v=zTjRZNkhiEU

You'll want to learn about GitHub as well.

- https://en.wikipedia.org/wiki/GitHub
- https://docs.github.com/en/get-started/using-github/github-flow

And, if you actually want to code, you'll want some kind of code editor:

- Visual Studio Code: https://www.youtube.com/watch?v=cu_ykIfBprI&t=33s

And, if you are going to code, you can't go wrong starting with Python:

- Python Getting Started Video Series: https://www.youtube.com/watch?v=jGE4aLSgRDs&list=PL2iGGYc-iqtyVjCXzFCSH1yggyUDOEpSL

## Using the Git Bash Environment

### Fixing the Tiny Screen Size

Open a Git Bash terminal, drag the corners out to the size you normally want to use, right click on the title bar, click on Options, choose Window, choose Current size, and Save. Note: there are other settings in Options that you might want to explore, like Options>Looks>Theme.

### Enabling Copy/Paste Within the Git Bash Terminal

You can't use Control-C for copy in Git Bash because Unix shells use Control-C to send a signal to a process to tell it to shut down. So, some other keys must be used.

You can enable Ctrl+Shift+C and Ctrl+Shift+V for a more familiar copy-pasting experience within Git Bash:

- Right-click on the top bar of the Git Bash window.
- Select "Options".
- Go to the "Keys" section.
- Check the box for "Ctrl+Shift+letter shortcuts".
- Click "Apply" and then "Save".
  - To Copy: Ctrl + Shift + C
  - To Paste: Ctrl + Shift + V

### Using Git Bash for Git/GitHub (Advanced - not needed for this effort)

https://www.geeksforgeeks.org/git/working-on-git-bash/

## Now for Some Unix

### Good Quick-Intro Vidoes

For a super quick intro to get you started, please watch this video: https://www.youtube.com/watch?v=sw9kdFka8rA

And even though some of the material is repeated in this video, please watch this one also because you will see some clearer explanations of some of the commands and some new stuff. This video also references using nano, which is a command-line code editor that is simpler-to-learn (than vim) for beginners. Nano is installed with Git Bash. https://www.youtube.com/watch?v=S0XegNhpTs8&t=17s

That video just above references explainshell.com, which is rather cool and useful, and will attempt to show you what a particular sheel command means: https://explainshell.com/. If you have a shell command example that you are confused about, give that web page a try by pasting it in there.

### Some Background on Unix

#### Do One Thing Well

Unix was built using a few philosophies: it stores configs and text and such in text (not binary) files; internally it treats many of its parts as files or file-like objects; it has a bunch of commands that “do one thing well”.

#### Auto-Connect to Standard Interfaces

When you open a unix terminal, it automatically opens three “file like” (stream) interfaces: standard input (“stdin”), standard output (“stdout”), and standard error (“stderr”). And, it (normally) automatically connects these to hardware devices on your computer.

    - stdin: Keyboard
    - stdout: Display
    - stderr: Display

https://en.wikipedia.org/wiki/Standard_streams#/media/File:Stdstreams-notitle.svg

#### Home Folder

Unix environments use the tilde symbol as a mapping to your home folder. So, instead of having to type out your home folder path, you can just type "~" and the rest of the path you desire. For example, instead of `cat c/users/myusername/dev/myfile.txt` you can type `cat ~/dev/myfile.txt`.

#### Tab Completion

Unix shells normally offer command line tab completion. This means you can start typing what you want and hit the tab key and if the shell can figure out what you are trying to do, it will finish filling in the command. This is most often used with directory and file names. So, if you are trying to type in a long file name, you can start the name and then hit tab and if there are no conflicting file names, the tab completion with fill in the rest of the name. Typically, if there is a name conflict, the shell will show you the conflicting names and you can type one/more additional characters as needed to identify the desired name.

![Tab Completion Example](images/bash-shell-tab-completions.png)

#### History

Unix shells keep a short history of commands you employ to make it easier to reuse them later without typing so much. Typically, this will be between 1,000 and 10,000 lines. You can look through the history by being at the terminal and using the up and down arrows. When you find a previous command you want, you can change it using the left and right arrow keys, and then run it, or just hit return to run it as is.

The history info is normally stored in a hidden file called .bash_history.

### Some Commands

#### alias

The alias command can be used to configure shortcut commands that basically just call something else. They are typically used to provide an easier way to call a command with options or provide a provide a shorter way to call long command strings. Aliases get loaded in when you open the shell. You can see which aliases are currently loaded by calling the alias command.

![alias example](images/alias.png)

If you want to add an alias that will show a long listing that includes hidden files, you can run this command on the terminal `echo 'alias lla="ls -al"' >> ~/.bashrc`. This will append the line to your config file, but you will need to restart your terminal for it to become active (cause the terminal to reread the configs). If that scares you, you can add `alias lla="ls -al"` as a new line to .bashrc using nano.

By the way, I'm not sure how Git Bash on Windows is including those aliases that come with the terminal as they are not in .bashrc. So, just add what you want as custom aliases to .bashrc.

Tip: You can use custom aliases to save yourself a lot of typing. For example, let's say you work in a specific folder a lot and are tired of typing cd blah blah. You could create yourself a custom alias and then just use that by adding this line to .bashrc `alias cdmar="cd ~/dev/marimotest/"`. Then, you can restart the terminal and just type cdmar return and whalaa! Some folks have 10-20 custom aliases they always set up on a new system.

#### ls/ll
