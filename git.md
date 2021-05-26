# Git

Git can be run in command line (Bash) environment or in a GUI environment. This workship will work exclusively in the command environment.

Bring up the git shell (this may be listed as the **Git Bash** application on **Windows** and it may be accessed via your **Terminal** application on the **Mac**). 

<img src="img/image-20210526102426954.png" alt="image-20210526102426954" style="zoom: 50%;" />

### Configure your global Git environment

If you haven't used Git on your computer yet, you will need to configure a few settings: Your name and your contact information (email address). This info is used to keep track of the author behind any changes made to a Git repository. This is not necessarily tied to an existing account, you can assign and name/email address you see fit.

Type the following while replacing `Jane Doe`  and `jdcolby@colby.edu` with  your name and email address respectively.  (Do not type the `$` character! This is only referencing the existing prompt in your terminal).

```bash
$ git config --global user.name 'Jane Doe'
$ git config --global user.email 'jdcolby@colby.edu'
```

To check your settings, type:

```bash
$ git config --global --list
```
You should see something like:
<pre>
user.name=jdcolby
user.email=jdcolby.com
</pre>

Note that all Git operations start with the `git` command.

## Create a new project folder

A Git repository (**repo**  for short) usually consists of project folder. You can create a Git repo in an existing project folder, or from a newly created folder. In this exercise, you'll create a new empty folder that you'll call `proj1`.  You can do this in a file manager window, or via the Bash command line. In this working example, we'll use Bash to create the folder under the user's home directory.

```bash
$ mkdir proj1
```
Next, we'll jump into the project folder using the `cd` (change directory) command.

```bash
$ cd proj1
```
In Bash, you can check the contents of a folder using the `ls` function. We'll add the `-a` option to list any hidden files and/or folder.

```bash
$ ls -a
```
Given that this is  a newly created  folder, you should only see a few dots

```html
. ..
```

##  Creating a new git repo

Now that we have a project folder, we can create a new git repo in it. 

```bash
$ git init
```

If the project folder is empty, Git will return the following message:

```html
Initialized empty Git repository in C:/Users/jdcolby/proj1/.git/
```

More to come ...
