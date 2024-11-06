# Modular Git

## Installation

* Open your Bash or Zsh terminal.

    * On Windows, you can use Git Bash by installing [Git for Windows](https://git-scm.com/downloads/win) (MINGW64).

* Clone the repository:
    ```bash
    mkdir ~/git
    cd ~/git
    git clone git@github.com:anarchic-pro/modulargit.git
    ```

* Add the script to your `.bashrc` or `.zshrc`:
    ```bash
    source ~/git/modulargit/bin/gitmod-starter-bash
    ```

    * **(Windows only)**: If you’re using Git Bash and can’t find your `.bashrc`, create one by running `vim ~/.bashrc` and add the following:
        ```bash
        #!/bin/bash

        source /c/git/modulargit/bin/gitmod-starter-bash
        ```
        Then restart Git Bash. Upon restarting, you might see:
        ```bash
        WARNING: Found ~/.bashrc but no ~/.bash_profile, ~/.bash_login or ~/.profile.

        This looks like an incorrect setup.
        A ~/.bash_profile that loads ~/.bashrc will be created for you.
        ```
        After this, everything should work. You won’t need to restart Git Bash again.

    * **(Windows only)**: It’s fine to store your Git folder under `/c/git` instead of `$HOME/git` if you’re the sole user of the computer. This is often more convenient, considering Windows' longer directory paths and complex environment variables.

* Enable modules by creating a `~/.gitmods` file with a structure like this:
    ```bash
    DEFAULT
    prohibit-branch
    base-git
    ```
    You can replace `DEFAULT` with any directory path where you want to store additional modules.
    
    **WARNING: please don't forget to put base-git in the end of the list!**

* Configure all the modules.    

## Modules

### base-git

Runs your original command in the end of the execution chain.

No configuration needed.

### prohibit-branch

This module prohibits the use of the `branch` command to encourage trunk-based development and a branch-by-abstraction workflow.

#### Configuration:

Create a `~/.gitprohibit` file in your home directory and fill it as shown below:

For Linux:

```bash
/home/olegchir/repo1
~/myrepo2
# /home/olegchir/disabled-repo
```

For Windows:

```bash
C:/git/myrepo1
C:/git/myrepo2
# C:/git/disabled-repo
```

You can use comments.

Both POSIX (Linux, Mac) and Windows directory paths are supported. The `~` will expand to your `$HOME` directory.

On Windows, the `CYGPATH` command is used to convert paths between representations. This setup is designed for Git Bash on Windows and has not been extensively tested on other shells (like MYSYS2 and MobaXTerm).

All actual `git` commands will be logged in `~/.git_command_log`.
