# Using the Command Line

## GUIs v. CLIs

Most computer users are more comfortable using graphical user interfaces \(GUIs\), where point-and-click interactions dominate the landscape. Several steps of the installation processes required you to use what is known as a command line interface \(CLI\). Contrary to graphical windows, menus, and buttons, you entered textual commands into a console application.

There are many examples of CLIs, some of which you've already seen—the Command Prompt and Git Bash on Windows, as well as iTerm2 and the Terminal on macOS. Going forward, you'll be asked to enter commands into a terminal. I'm using this term as a generic reference to the CLI of your choosing. A lot of times, I'll use application-agnostic code blocks. The screenshots I use will be of iTerm2, which serves as an enhanced Terminal application on macOS. Don't worry if you're using something else—the commands are nearly identical, and I'll point out any instances where they differ.

## Common Linux Commands

Windows is the most popular desktop operating system by market share, with just over 77% of computers running some flavor of it as of May 2020. macOS, including its Mac OS X predecessors, holds slightly more than 18% of the global market share. The remaining 5% is shared among various Linux distributions, Chrome OS, and other lesser known operating systems.

Linux is largely unknown to the average computer user, but it is an extremely powerful operating system. Its distributions often come with GUIs that don't look all that different than typical Windows or Mac environments, but the Linux operating system is primarily known for its CLI. This will be our focus.

### Navigating Directories

First and foremost, you need to know where you are, what files and folders are available, and how to move back and forth between folders. These commands do just that.

* `pwd`
* `cd`
* `ls`

{% embed url="https://www.youtube.com/watch?v=7pBFbROYYdg" %}

The video discussed two techniques to find documentation on how to use a command and its flags.

* `man <command>`
* `<command> --help`

These two do more or less the same thing. `man` is not installed in Git Bash, but you can get the same information using the `--help` flag.

### Manipulating Files and Folders

Moving around and looking at stuff is great, but I'm sure you want to actually do stuff. These commands create, move, and delete files and folders.

* `touch`
* `mkdir`
* `mv`
* `cp`
* `rmdir`
* `rm`

{% embed url="https://www.youtube.com/watch?v=ZsLg7eLkYbs" %}

Remember, these commands are very powerful \(especially the removals\). Use them with care.

### Tips and Tricks

A few of these were mentioned in the videos, but deserve some more emphasis. Others were glossed over a bit, and could use a more formal description.

* Use the `tab` key to autocomplete files, folders, and commands.
* Use the arrow keys to cycle through previously executed commands.
* Use `Ctrl+C` or `Ctrl+Z` to kill long-running commands or programs.
* Use the `clear` command to clear the terminal.

#### Autocomplete

Pressing the `tab` key will prompt the shell to try to figure out what you mean. If it can narrow it down to one possible option, it'll autocomplete whatever file, folder, or command you're typing. If it can't narrow it down, it'll show you what the possible options are. This can save a lot of time, and make you much more efficient.

#### Previous Commands

Don't waste time typing in commands over and over. The `UP` arrow cycles backwards, while the `DOWN` arrow cycles forwards. Again, this is a huge timesaver when working from the command line.

#### Killing Commands

If a command or program you've run seems to be stuck, you can quit using `Ctrl+C`. If `Ctrl+C` doesn't terminate the process, use `Ctrl+Z` to force-quit.

#### Clearing the Terminal

A few times throughout the video, the terminal seemed to clear itself. This can be tremendously helpful. The terminal can get cluttered with commands and output, and sometimes you just want a clean slate. The aptly named `clear` command does just that.

