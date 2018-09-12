Lesson 1: Version control using git
========================================================
author: Máté Csaba Sándor
date: 2018 September
autosize: true

Version control: why?
========================================================

- When you create documents and codes, usually you do not get to produce a perfect version that you do not have to modify anymore
- The creative process includes a lot of try and error, making mistakes, revising your work now and then
- Sometimes you add parts that you did not wanted to or delete some that you wanted to keep
- You would like to keep backup of your material, preferably in many place

**How could I make sure I keep the whole evolution of my document in sync on multiple locations?**

Version control: sharing is caring
========================================================

- It would be nice to share my codes and its history with others
- It would be nice to let that suggest modifications

**How can I do this without sending around emails of zip files and sharing dropbox libraries?**

Git
========================================================

*Git* is a version control system for tracking changes in computer files and coordinating work on those files among multiple people.

- Developed in 2005 by Linus Torvalds
- Free and open source software
- Market standard

Usual research workflow using git
========================================================

- **Pulling** codebase from remote directory
- **Editing** files
- Review/**add**/**commit** changes
- **Pushing** codebase to remote directory

Cooperation on common codebase
========================================================

- Pulling the **master** branch
- Creating a **feature** branch
- Edit/review/add/commit/push features
- **Merge** to master branch

Remote repositories
========================================================

- A place where you can backup your code
- A place where you can share your code and gather others from
- You can set up a git server yourself or use a commercial provider (*GitHub, GitLab, BitBucket, etc.*)
- For this class I have suggested to regirster on **GitHub** (public repos are free)

Creating my first project
========================================================

- Create a new project in GitHub
- Do not forget to check the README file inclusion
- Go to your (git) terminal and clone the repository:

```
git clone SSH LINK FROM GITHUB
```
Pushing changes
========================================================

- Create a text file named ``` hello_world.txt  ```
- Write something into it
- ``` git add hello_world.txt ```
- ``` git commit -m "initiating my first file" ```
- ``` git push ```
- Provide your credentials (advanced users can [set up an ssh key](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/))
- Check out the contents on GitHub

Reverting to an earlier version
========================================================

- Add a few "accidental" lines to your file
- Check ```git status```
- Add and commit to your changes
- Now check your commit history: ```git log```
- Revert the file: ```git checkout COMMITNO -- hello_world.txt```

I want to try something.. let's start a branch!
========================================================

- ```git checkout -b mybranch```
- ```git status``` -> now we are not on master
- Modify/add/commit file
- ```git checkout master``` -> this does not have the modifications
- ```git merge mybranch``` -> now it has them (*when the conflicts have been resolved...*)
- ```git log``` -> the merge is a separate commit

I need help!
========================================================

- Read the manuals on [Git](https://git-scm.com/doc) and [GitHub](https://help.github.com/)
- Google and StackOverflow is always there to help you
- If there is no solution to your problem on the internet, you are either a pro or you have not searched just long enough. *(Hint:most probably you are not a pro)*

