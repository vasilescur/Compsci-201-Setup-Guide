# Compsci 201 Setup Guide
An opinionated in-depth setup guide for Duke CompSci 201 students.

## Prerequisites

The following things need to be installed before you continue:

- Latest version of the Java JDK - [Link](https://www.oracle.com/technetwork/java/javase/downloads/index.html).
You're going to want the **SE** version. Pick the most recent version. At the 
time of this writing, it's JDK 11. It should be the big button at the top. 

## Installing Git

### Windows

Install from here: [https://git-scm.com/download/win](https://git-scm.com/download/win)

In the installer, use all the default options. If it asks you if you want to 
add git to your `PATH`, say **yes**.

Then, log out, and log back in. (or restart)

### MacOS

#### Step 1 - Install Homebrew

If you don't have it already, you're gonna need to first install *Homebrew*, 
the package manager for MacOS.

Copy and paste the following into a terminal window and hit enter:

```bash
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew doctor
```

You will be asked to install the *Command Line Developer Tools* from *Apple*. 
Confirm by clicking **Install**. After that finishes, continue installing 
Homebrew by hitting enter again.

#### Step 2 - Install Git

Copy and paste the following into a terminal window and hit enter:

```bash
brew install git
```

### Linux

If you're running linux, you should probably know how to install git.

```bash
sudo apt-get install git
```

or

```bash
sudo pacman -S git
```

if you're an Arch kind of person.

## Windows Only -- Adding Java to the PATH

For y'all windows users out there, you have to do these terribly convoluted 
steps to get your system to see Java.

1. Open the Start menu search bar or whatever and type "sytem environment"
2. Click on the option that says "Edit the system environment variables"
3. Click the "Environment Variables" button at the bottom-right
4. In the pop-up, look at the **bottom** half of the window. **Click on the entry in that list called `PATH`**. Then, click the "Edit" button. Then, click the "New" button.
5. Open a File Explorer window. `Go to C:\Program Files\Java`
6. Go into the folder of the jdk you installed. 
7. Click the address bar of your file explorer to select the current directory path and then  hit `Ctrl-C` to copy it. It should be something like `C:\Program Files\Java\jdk-something`.
8. Back in your environment variables path "New" window, paste that path in and save it.
9. Go back to File Explorer. Go into the `bin` folder inside the JDK. Copy and paste that file path into a "New" `PATH` entry as well, just like last time.
10. Click `Apply` or `OK` or whatever on all the windows, then re-open it to make sure it saved the new entries.
11. **Go back to the window with a top and bottom list** (where you selected the PATH one to edit). Click the "New" button (IN THE BOTTOM HALF) to create a new variable (it will go in the same list as PATH is in). Call this variable `JAVA_HOME` and give it a value of the **first** path you copied into the PATH. (the path to your main JDK folder, **not** the `bin`)
12. `OK`, `Apply`, Save, whatever. Open it again to make sure it saved.
11. Restart your computer.

All that junk basically made it so Windows can see java from a terminal window.

## Installing the IDE

Eclipse is old and ugly and crashes a lot, so instead, we're gonna use a much newer, better editor called Visual Studio Code. **IMPORTANT! Visual Studio Code and Visual Studio are two very different things.**

Install the correct version for your computer from [here](https://code.visualstudio.com/download).

When it's done installing, open it.

## A Quick Tour of VS Code

When you first open it up, it should land at a Welcome page with a bunch of stuff. Close that tab.

On the left you have your sidebar. This has a few tabs on the very left of the window (the big icons) that allows
the sidebar to show different things.

1. The first icon from the top is the file browser. This will show all the files in the folder that is currently open
in VS Code. Each Java program you write should probably have its own folder. You'd make that folder with your File
Explorer (or Finder on mac), and then go in VS Code and click Open Folder and select it to open that as a project.

2. The second icon searches your project.

3. The third icon is a handy dandy Git integration.

4. The fourth icon is a debugger. It allows you to go through and run your code step by step. 

5. The fifth icon is a boxy-lookin thing and it is the Extensions manager. This is what you'll use for the next steps. Click on it.

## Configuring Visual Studio Code

### Extensions

The main difference between VS Code and Eclipse is that Eclipse was built for Java
specifically, while VS Code is for any programming language. That means it doesn't know
jack about Java unless we install a Java extension. Same for other languages-- if you want
to use VS Code with Python, for example, you have to install a Python extension.

Go to the extensions tab in VS Code (in the sidebar, the boxy icon, 5th down probably).

Go through this list, typing the name in the search bar, and clicking install on the right one. Make sure you check
that you're installing the one by the right Author as some have similar names.

#### Useful Extensions

- Java Extension Pack *by Microsoft*
- Better Comments *by Aaron Bond*
- Nord *by arcticicestudio*
- Python *by Microsoft* -- if you want it

After you've clicked install on all of them one by one, do `Ctrl+Shift+P` (or `Command+Shift+P` on Mac) and then 
type `Reload Window` and hit enter.

(Fun fact: VS Code actually runs in a browser and is built in HTML and JavaScript. Reload Window basically "refreshes" it to
apply the new extensions.)

### Settings

Go to a main VS Code window and hit `Ctrl+comma`. In the top-right, click the `{ }` icon. 

Click in the right-hand pane. Delete everything. Paste this in and then save:

```js
{
    // Workbench and Editor
    "workbench.startupEditor": "newUntitledFile",
    "explorer.confirmDelete": false,

    "editor.smoothScrolling": true,
    "editor.mouseWheelZoom": true,
    "window.zoomLevel": 0,
    "editor.fontSize": 14,
    "editor.minimap.enabled": false,
    "editor.wordWrap": "on",
    "editor.highlightActiveIndentGuide": true,
    "explorer.confirmDragAndDrop": false,

    // Files
    "files.autoSaveDelay": 3000,
    "files.autoSave": "afterDelay",

    "files.associations": {
        "*.md": "markdown",
        "*.html": "html",
        //".zsh_aliases": "shellscript",
        //"*.asm": "mips"
    },

    // Python

    //"python.pythonPath": "/usr/bin/python3",
    //"python.linting.pylintPath": "/usr/local/bin/pylint",
    //"python.linting.pep8Path": "/usr/local/bin/pep8",
    //"python.formatting.autopep8Path": "/usr/local/bin/autopep8",

    // Git
    "git.enableSmartCommit": true,
    "git.autofetch": true,

    // Integrated shell (Platform-dependent)
    //"terminal.integrated.shell.linux": "bash",
    "terminal.integrated.shell.osx": "bash",
    //"terminal.integrated.shell.windows": "C:\\Windows\\System32\\cmd.exe",
    
    // Themes and Colors
    "workbench.colorTheme": "Nord",
    //"workbench.iconTheme": "eq-material-theme-icons-ocean",

    "editor.tokenColorCustomizations": {
        "[Nord]": {
            "comments": "#697d8b"   // Make comments a bit brighter
        }
    },

    // Extension Settings

    // SmoothType
    //"smoothtype.duration": 80,
    //"smoothtype.autoReload": true,

    // Java
    "java.errors.incompleteClasspath.severity": "ignore",
}
```

Go up to the `"terminal.integrated.shell.xxxxxx"` section and un-comment out the one for your system and 
comment out the others. If you're a `zsh` person feel free to do that.

Reload the window again (`Ctrl+Shift+P`, "Reload Window", enter).

## Using VS Code for Java

Like I said, VS Code doesn't know what Java is unless you have that extension. So it won't have a "Run Code" button.
You have to run the code from the terminal. Here's how:

1. Write your code
2. Press `Ctrl` and the backtick character below escape to open the integrated terminal
3. To compile your code, type:

```bash
javac Program.java
```

4. To run your code, type:

```bash
java Program
```

You can put these together on the same line, too:

```bash
javac Program.java && java Program
```

If you have more than one class/Java file, you can use

```bash
javac *.java && java MyMainClass
```

to compile all `.java` files at once.

If you are working on an assignment and you have a `src` and a `bin` folder and stuff, it's a bit more compicated:

1. Open integrated terminal (Control + backtick)
2. `cd src` to go into the `src` folder
3. `javac *.java -d ../bin/` to compile files in there, outputting the result to the `bin` folder
4. `cd ../bin` to go back to the main folder and then into `bin`
5. `java MyMainClass` to run your program
6. `cd ..` to return to your main project folder

You can probably also put those together (not tested):

```bash
cd src && javac *.java -d ../bin/ && cd ../bin && java MyMainClass & cd ..
```

## The Debugger

To use the debugger, go to the debug pane on the left, then click the little gear icon. Save the file that
is auto-generated, and go back to your main file. In the debug pane, click the little green Play icon to start debugging.

This will launch your program in debug mode. Whenever you use Run or Debug from within VS Code, **BE WARNED!** You
won't be able to give your program any input (from the console).

In order to be able to step through your code one line at a time, you have to place a breakpoint. That's like a little
flag that tells the debugger, "Hey, pause here!". To do that, click in the left-hand gutter of the editor (between the
line numbers and the sidebar -- just to the left of the line numbers). You should get a little red bubble on the line
you want to set a breakpoint on. To clear it, just click it again.

Now when you hit the play button and enter the debugger, it'll pause at that breakpoint and you can use the controls
at the top to step through your program.

- Resume does what you think it does
- Step Over runs the current line and then goes to the next line, but if the current line is a function call it won't
show you inside the function. This is useful when you don't want to have to step through a billion lines in 
the internals of java's libraries whenever you make a function call.
- Step Into does the same thing but it does go into the function
- IDK what Step Out does
- Restart and Stop do what you think they do

You can also watch the left panes to see your variables update in real time as their values change.

## Using Git

**Make sure you've followed ola's instructions about SSH keys and stuff!**

To download a git repository to your computer, do:

```bash
git clone [link goes here]
```

(you get the link from GitHub / GitLab where you say Clone and it has the link in a little text box. Copy paste that.)

Open the newly created folder in VS Code and do your work. To save it back up to GitHub/GitLab, do:

```bash
git add .
git commit -m "Short message describing what you did since the last time you pushed changes"
git push
```

To sync your local copy with the online copy by downloading any new changes, do:

```bash
git pull
```

The command `git status` is also useful (if a bit confusing).

## Conclusion

Ok, you're ready to go. Make sure you go follow the rest of ola's instructions for Git SSH keys and stuff.
