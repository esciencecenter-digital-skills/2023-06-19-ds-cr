![](screenshots/iywjz8s.png)


# Day 1 - 2023-06-19-ds-cr

Welcome to The Workshop Collaborative Document.

This Document is synchronized as you type, so that everyone viewing this page sees the same text. This allows you to collaborate seamlessly on documents.

[TOC]

----------------------------------------------------------------------------


## 👮Code of Conduct

Participants are expected to follow these guidelines:
* Use welcoming and inclusive language.
* Be respectful of different viewpoints and experiences.
* Gracefully accept constructive criticism.
* Focus on what is best for the community.
* Show courtesy and respect towards other community members.

## 🎓 Certificate of attendance

If you attend the full workshop you can request a certificate of attendance by emailing to training@esciencecenter.nl .

## ⚖️ License

All content is publicly available under the Creative Commons Attribution License: [creativecommons.org/licenses/by/4.0/](https://creativecommons.org/licenses/by/4.0/).

## 🙋Getting help

To ask a question, raise your hand in zoom. Click on the icon labeled "Reactions" in the toolbar on the bottom center of your screen,
then click the button 'Raise Hand ✋'. For urgent questions, just unmute and speak up!

You can also ask questions or type 'I need help' in the chat window and helpers will try to help you.
Please note it is not necessary to monitor the chat - the helpers will make sure that relevant questions are addressed in a plenary way.
(By the way, off-topic questions will still be answered in the chat)

## 🖥 Workshop website

[link](https://esciencecenter-digital-skills.github.io/2023-06-19-ds-cr/)

🛠 Setup

[link](https://esciencecenter-digital-skills.github.io/2023-06-19-ds-cr#setup)

## 👩‍🏫👩‍💻🎓 Instructors

Barbara Vreede, Dani Bodor

## 🧑‍🙋 Helpers

Candace Makeda Moore, Ewan Cahen



## 🗓️ Agenda
| Time  | Topic                                    |
|------:|:-----------------------------------------|
| 9:00  | Welcome and icebreaker                   |
| 9:15  | Introduction to version control with Git |
| 10:15 | Coffee break                             |
| 10:30 | Introduction to version control with Git |
| 11:30 | Coffee break                             |
| 11:45 | Introduction to version control with Git |
| 12:45 | Wrap-up                                  |
| 13:00 | END                                      |

## 🔧 Exercises

### Tracking changes exercise

#### 1. Which command(s) below would save the changes of myfile.txt to my local Git repository?

1. `git commit -m "my recent changes"`
2. `git init myfile.txt`
   `git commit -m "my recent changes"`
3. `git add myfile.txt`
   `git commit -m "my recent changes"`
4. `git commit -m myfile.txt "my recent changes"`


**Correct answer:** 3

#### 2. Committing Multiple Files
Remember that the staging area can hold changes from any number of files that you want to commit as a single snapshot.

- Add some text to ``mars.txt`` noting your decision to consider Venus as a base
- Create a new file ``venus.txt`` with your initial thoughts about Venus as a base for you and your friends
- Add changes from both files to the staging area, and commit those changes.

#### 3. (optional) A new repository
1. Create a new Git repository on your computer called bio.
3. Write a three-line biography for yourself in a file called me.txt.
4. Add the file to the staging area, and commit your changes.
5. Make a modification.
6. Display the differences between its updated state and its original state.


### Exercises for Ignoring Things
#### Ignoring Nested Files
Given a directory structure that looks like:
```
results/data
results/plots
```
How would you ignore only `results/plots` and not `results/data`?

#### (optional) Including Specific Files

How would you ignore all `.dat` files in your root directory except for `final.dat`? Hint: Find out what `!` (the exclamation point operator) does

## 🧠 Collaborative Notes

### Why version control
![Why version control](https://phdcomics.com/comics/archive/phd101212s.gif)

* Version control is track changes on steroids.
* Version control is an unlimited undo.
* Version control also allows many people to work in parallel

### Setting up Git
Setup your name and email:
```bash
git config --global user.name "My Name"
```

```bash
git config --global user.email "me@example.com"
```
For consistent line endings between different operating systems:
For Windows:
```bash
git config --global core.autocrlf false
```

For Mac or Linux or WSL (Windows Subsystem for Linux):
```bash
git config --global core.autocrlf input
```

Change the default branch:
```bash
git config --global init.defaultBranch main
```

See your settings:
```bash
git config --list
```

Config help:
```bash
git config --help
```

General help:
```bash
git help
```

Change the default editor to e.g. nano:
```bash
git config --global core.editor nano
```


### Making a repository
Make a new directory:
```bash
mkdir planets
```

Go to that directory:
```bash
cd planets
```

Initialise a new git project:
```bash
git init
```

Check if it worked:
```bash
git status
```
or
```bash
git branch --show-current
```

See all files, but it doesn't show anything:
```bash
ls
```

See all files, including the *hidden* `.git` folder:
```bash
ls -a
```

Checkout a new branch `main`:
```bash
git checkout -b main
```

Make a subdirectory:
```bash
mkdir moons
cd moons
```

Create a nested git repository, **don't do this:**
```bash
git init
```
Git is not good at handling nested Git repositories. If you did this, you can delete the `.git` directory:
```bash
rm -rf .git
```
If you need nested repositories, check out [Git submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

Go back to the `planets` folder:
```bash
cd ..
```

### Add content and track changes
Create and open a new file:
```bash
nano mars.txt
```
Enter the following text:
```
Cold and dry, but everything is my favorite color
```

See if the text was written to the file correctly:
```bash
cat mars.txt
```

Check that you have one untracked file:
```bash
git status
```

Track the untracked file:
```bash
git add mars.txt
```

Commit that file:
```bash
git commit -m "start notes on Mars"
```

Now `git branch` will show the `main` branch, `git status` should say that there is nothing to commit.

See the logs:
```bash
git log
```

We will make more changes:
```bash
nano mars.txt
```
Add the following line
```
There are two moons on Mars, which might be a problem for Wolfman
```

Show the changes:
```bash
git diff
```

Running `git status` says there is a modified file. Add it again with
```bash
git add mars.txt
```

After staging files, you can see the changes only with
```bash
git diff --staged
```

Commit your changes:
```bash
git commit -m "Add concerns about effects of Mars' moons on Wolfman"
```

**TIP:** if you ever get stuck, run `git status` for helpful suggestions.

Edit the file again:
```bash
nano mars.txt
```
Change the word `two` to `2` and ddd the line
```
But the Mummy will appreciate the lack of humidity
```

Check out `git diff` again, you will see the two changed lines. Even though you only changed one word on the second line, Git will consider the full line to be changed. You can run `git diff --color-words` to see changes at a more granular level.

We will add the file again:
```bash
git add mars.txt
```

**Note on commit messages:** commit messages should not be too long, they should be short, descriptive and imperative and ideally under 50 characters long.

Now commit the changes:
```bash
git commit -m "add concerns regarding mummy"
```

With `git log` you can see the 3 commits. When the amount of commits grows, you can limit the output with e.g. `git log -2`. You can also get compressed output with `git log --oneline`.

**Note on undoing commits:** It is hard, but possible to undo commits, see e.g. https://www.git-tower.com/learn/git/faq/undo-last-commit for more info. However, commits pushed to remote repositories could have already been downloaded by others, so always be careful, especially when potentially committing sensitive data.


### Tracking Changes: Key Points

* Files can be stored in
    * working directory: the files you can see
    * staging area / index: files about to be committed
    * local repository: the permanent record
* git status  shows the status of a repository
* git add  puts files in the staging area
* git commit  saves the staged content as a new commit in the local repository
* Write short, descriptive, and imperative commit messages


### Exploring History
In `git log --oneline`, you see the identifier `HEAD`, which points to the newest commit, along with the *commit hashes* and commit messages.

To see changes further in history, you can use e.g. `git diff HEAD~2` to see the difference between the current commit and two commits before.

You can also checkout a specific commit with e.g. `git checkout a7e88be`, replace the hash with a has from your history. This will switch over to `detached HEAD` state.

You can make changes in this state, so let's change the `mars.txt` file:
```bash
nano mars.txt
```
Add some text *above* the first line.

We add the changes again:
```bash
git add mars.txt
```

And commit:
```bash
git commit -m "write an introduction for mars"
```

Check `git status`. We will now switch to a new branch:
```bash
git checkout -b marsintro
```
Let's check the history with `git status` and `git log`. Let's go back to main:
```bash
git checkout main
```
Now `git branch --all` should show two branches.

**Note on checkout:** The `git checkout` command does a lot of things, you can checkout branches but also individual commits. To switch between branches only, `git switch` is a cleaner option.

### Merging branches
We will now merge the `marsintro` branch into `main`:
```bash
git merge marsintro
```

If you merge two branches, there might be conflicts. As always, `git status` will show you what's happening. You should edit the conflicted files to resolve the conflicts. A conflict might look like the following example:
```
Cold and dry, but everything is my favorite color
The two moons may be a problem for Wolfman
But the Mummy will appreciate the lack of humidity
<<<<<<< HEAD
We added a different line in the other copy
=======
This line added to Wolfman's copy
>>>>>>> dabb4c8c450e8475aee9b14b4383acc99f42af1d
```

The `<<<<<<< HEAD` tag shows your changes, the `=======` is a separator between the conflicted changes and `>>>>>>>` marks the end of the conflicted changes.


### Ignoring files
The `.gitignore` file is a text file in which you can put files that you don't want Git to track.

Create one with
```bash
touch .gitignore
```
and open it for editing:
```bash
nano .gitignore
```
A good use case is to ignore binary files, so for example add `*.docx` as an entry. This means that Git will ignore all files with a name that ends with `.docx`. You can also add folders, e.g. `/data` or specific files like `saturn.txt`.

If you did this, create two files:
```bash
touch saturn.txt
touch pluto.txt
```
If you run `git status`, you will see that `saturn.txt` is not listed at all, even though you did not even start tracking the `.gitignore` file itself. It is still a good idea to track it though:
```bash
git add .gitignore
git add pluto.txt
git commit -m "add .gitignore and pluto.txt"
```

You can keep tracking specific files or folders that were excluded previously with the exclamation operator (`!`). Just add it at the start of the line of the file or folder you want to track, e.g. `!example.txt`

The following repository lists useful `.gitignore` configurations for common programming setups: https://github.com/github/gitignore


### Interactive commits
You can interactively choose what parts of a file to commit with `git add --patch` or `git add -p`. See https://git-scm.com/docs/git-add#_interactive_mode for more information


### Check your SSH keypair
The follwing command will check if your SSH keypair is working.
```bash
ssh git@github.com
```
It should say something like
```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed
```



## 📚 Resources
- Undoing a commit: https://www.git-tower.com/learn/git/faq/undo-last-commit
- Permanently deleting file from GitHub: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository
- Useful "default" .gitignore files: https://github.com/github/gitignore
- Selectively add edits to the staging area: https://git-scm.com/docs/git-add#_interactive_mode
- Git submodules: https://git-scm.com/book/en/v2/Git-Tools-Submodules
- Create SSH keys on your computer: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
- Add SSH keys to yor GitHub account: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account

