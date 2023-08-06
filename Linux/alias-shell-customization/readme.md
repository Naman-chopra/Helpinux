# Use the shell like a pro

Many times, users that are new to linux donot remember the commands, or those who are into serious usage of it, end up entering long command into the CLI repetetively. Guess what! You don't need to do that anymore.
## Which are the commands that are so repetitive in nature??
For beginners it might not seem so initially, but using the command line, you can do almost everything directly from one single app. I for one at the beginning used linux only for the fun of it but as time went by, I kept coming back to the terminal for various purposes. Most of my commands seemed like they were being run repeatedly and I had to type a whole "sudo apt install package" again and again. And then I found out about aliasing.

## What is aliasing??
In linux, you can assign aliases to commands, i.e. instead of typing the whole `sudo apt install package`, you can just "rename" the command to install. This might not seem like much but just try to install 10 packages without aliasing.

## How to do it?
Firstly you'll have to find out which type of shell your linux system is using. This can be easily done by typing
``` console
echo $SHELL
```
into the terminal.

Now I've done aliasing in both garuda and ubuntu but for ease of understanding, the commands below assume you have ubuntu with bash shell.

### Find your bashrc
The bashrc is the file where bash shell checks for any aliases and other functions that it might use when the terminal is launched. It is generally located in /home/username directory.
Once you've found the bashrc, type the code below into the terminal
``` console
sudo gedit ~/.bashrc
```
A new graphical text editor window would open up. Now scroll to the bottom of this window and create your aliases.
here we'll be creating the alias for launching a jupyter notebook that doesn't open up a browser window.

The original command to launch a notebook like this is 
``` console
jupyter-notebook --no-browser
```
Now imagine typing this command everytime to launch a jupyter server........


Now you have the gedit window opened. on the bottom of the window type:
``` console
alias jnb='jupyter-notebook --no-browser'
```
Save the changes by hitting `ctrl+s` and then close the window (press `ctrl+w` twice).

Now to make the shell recognise the aliases, type `source ~/.bashrc` in the terminal.
To check if the alias is working, type `jnb` (the alias we just assigned) in the terminal and kaboomm the server should fire up!!

I'll be attaching a text file that contains the aliases that I tend to use often and might give some idea to you where you could use them.
`Note: The glut alias is a little advanced for beginners so just hmu if you have any queries`
