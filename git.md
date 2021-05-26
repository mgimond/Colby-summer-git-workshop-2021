# Git

Git can be run in command line (Bash) environment or in a GUI environment. This workshop will work exclusively in the command environment.

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
Now lets check the folder's content. Don't forget to add the `-a` option to list hidden folders/files.

```BASH
$ ls -a
```

You should now see `.git` added to the folder. The dot `.` in front of its name indicates that it's a *hidden" file.

```BASH
.  ..  .git
```

We'll add another option to `ls` to differentiate files from folders.

```BASH
$ ls -aF
```

```BASH
./  ../  .git/
```

`.git` is a hidden folder. This is the  guts of this folder's git repo. If you were to remove this folder, you would lose all tracked changes to the current project folder, so this  folder you should not be touched!

## Create a new file

Next, you'll create a new file called `fruit.txt`  in the `proj1` folder.  Feel free to use any plain text editor using a GUI (such as *TextEdit* on Macs, or *Notepad* on Windows) or a command line application such as *vim* or *nano*.

In this newly created file, add the following text (make sure that each word is placed on its own line, i.e. use a carriage return).

```
apple
pear
```

Save, then close the file.

## Checking the state of your repo  using `status`

One of the most frequently used Git commands in a Git session is `status`. This command will identify what files/folders have been modified or created since the last saved state of the repo. 

```BASH
$ git status
```
You should see the following output.

```
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fruits.txt

nothing added to commit but untracked files present (use "git add" to track)
```

The above message indicates that git recognizes that a new file was created. But it has not been *committed*  to a snapshot.

## Creating a snapshot of your project folder: `add` and `commit`

If at any point in your project's development you wish to create a snapshot of your project folder, you will make use of Git's `add` and `commit` functions. Both functions serve different purposes but are more often than not used together when creating snapshots. In its basic use, `add` identifies which files and/or folders are to be stored in a snapshot and `commit` grabs the staged elements  and *commits* those elements to a snapshot that is identified using a timestamp and a unique *hash* identifier.



### Stage: `add`

Let's first stage the `fruits.txt` file.

```BASH
$ git add fruits.txt
```

Now let's check the status:

```BASH
$ git status
```
```
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   fruits.txt

```

The message indicates that the `fruits.txt` file  has been staged but has not yet been committed to a snapshot.


### Other `add` options
* If you have more than one item to stage, you can add these items on the same line separated by a space, e.g.:

    ```BASH
$ git add fruits.txt file2.txt file3.txt ...
    ```

* If you want include all files and folders in your current project folder in the staging area, simply use the `-all` option:

     ```BASH
     $ git add --all
     ```

### Commit: `commit`

When you have identified the files to be committed, the final step is to execute the `commit` command. The `commit` function takes as argument a *message* which allows you to add a brief comment to the commit for future reference (comment should be less than 80 characters). 

In this example, you will commit the staged files and append the message `"initial commit"`.

```BASH
$ git commit -m "initial commit"
```

You might see the following message (some of the hash numbers will probably differ on your machine):

```
[main (root-commit) a04294e] initial commit
 1 file changed, 2 insertions(+)
 create mode 100644 fruits.txt
```

Now check the status once again:

```BASH
$ git status
```
```
On branch main
nothing to commit, working tree clean
```
The above message indicates that Git has a snapshot of the most recent state of your project folder.

## Creating a second snapshot of your repo

Next, you will make changes to the `fruits.txt` file, then create a snapshot of this project folder's modified state.

Using your text editor of choice, add `orange` to the file.

```
apple
pear
orange
```
Save and close the text file.

Now check the status of your repo.

```BASH
$ git status
```

```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   fruits.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

Git recognizes that the content's of `fruits.txt` has changes since the last snapshot.

Next, you will create a second snapshot of the project folder.

```BASH
$ git add fruits.txt
$ git commit -m "added orange"
```

At this point, you've commit two snapshots of your current repo. Next, you will learn how to list the different snapshots in your Git repo.

## Using `log` to list snapshots.

To view all snapshots in a Git repo, use the log function.

```BASH
git log
```

```
commit afcdbd43051860e8837dc5561c33f227a89fea57 (HEAD -> main)
Author: Jane Doe <jdcolby@colby.edu>
Date:   Wed May 26 14:58:16 2021 -0400

    added orange

commit a04294e626e8046ff643627397a2c5aae587a7b5
Author: Jane Doe <jdcolby@colby.edu>
Date:   Wed May 26 14:44:56 2021 -0400

    initial commit
```

You should see the two snapshots listed in descending order. Each commit lists the author and timestamp associated with the commit (the author and email address are those you defined a the beginning of this tutorial). You'll also see the comment you added to each commit. Note that properly commented commits are important to help identify the different snapshots
