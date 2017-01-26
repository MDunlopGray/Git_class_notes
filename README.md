![Git image from https://git-scm.com/](images/git.png)
# **TTA566 - Introduction to Git**

# **Introduction**

## Links
* [Git](https://git-scm.com/) - some documentation, downloads, etc. 
* [GitHub](https://github.com/) - a free web-based Git hosting service
* [MITRE GitHub Page](https://mitre.github.io/) - Open Source at MITRE
* [Personal GitHub Page](http://coached.github.io/) - My personal GitHub site
* [Atlassian Bitbucket](https://bitbucket.org/) - another free web-based Git hosting service
* [Gitlab at MITRE](https://gitlab.mitre.org/) - like GitHub, but inside MITRE
* [MITRE Atlassian Portal](https://login.codev.mitre.org/portal) - log in to access MITRE Codev tools
    * [Atlassian Stash](https://git.codev.mitre.org/) - like Gitlab but requires access
	
## What even is Git?
* *Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.*
* Makes it easy to manage project versions, among one or many authors
* Facilitates versioning, branching, and merging
* Popular

## What is a Git "repo"?
* "repo" stands for "repository"
* A data structure with information to manage a project
* To get a repo, **clone** it

## What is GitHub?
* A web-based Git hosting service
* Free
* Hosts important open source projects like: [Linux](https://github.com/torvalds/linux), [Bootstrap](https://github.com/twbs), [Node.js](https://github.com/nodejs), [JQuery](https://github.com/jquery), [Ruby on Rails](https://github.com/rails)
* [Bitbucket](https://bitbucket.org/) is similar

## Before Git...
* *Mary, Jim, and Sarah work on a project.*
* **Jim**: I've made my changes. I emailed you a zip file of the project.
* **Sarah**: Got it. I'm making my changes now.
* **Mary**: Sarah- I'll stop by with a USB stick to copy your files.
* **Jim**: I have more changes, but I'll wait for Mary to finish.

## After Git...
* **Jim**: My changes are in.
* **Sarah**: I saw that. I already merged my changes.
* **Mary**: I just pulled the latest version. My changes will be in shortly.
* **Jim**: I just pushed in more changes, but it won't affect either of you.

# **Getting Git**

## You may already have it.
```sh
user@yourmachine:~$ git --version
```

## Download It: [link](https://git-scm.com/downloads)

## On Ubuntu: ```user@yourmachine:~$ sudo apt install git ```

## Configure It

Every Git commit identifies you by name and email. From your local machine, tell Git who you are: 
```sh
user@yourmachine:~$ git config --global user.email "ertorres@mitre.org"
user@yourmachine:~$ git config --global user.name "Ed Torres"
```
  
# **Is Git Secure?**

* Remote repos may be in the cloud (e.g., GitHub.com)
* Remote repos may be inside a corporate network (e.g., Gitlab.mitre.org, MITRE Atlassian Stash)
* Repos can be private
* Two-factor authentication (e.g., Bitbucket.org)
* Clone repos via HTTPS or SSH (including passwords)
* Secure your local computer

## Create Your SSH Public Key

From Git Bash (Windows) or Terminal (Ubuntu):

* Check if the .ssh directory exists in your home directory: ```user@yourmachine:~$ ls -a ~/.ssh ```
    * If not, create it: ```user@yourmachine:~$ mkdir ~/.ssh ```
* Create the public and private SSH keys: ```user@yourmachine:~$ ssh-keygen ```
* See the new files: ```user@yourmachine:~$ ls -a ~/.ssh```
* Print the contents of the public SSH key: ```user@yourmachine:~$ cat ~/.ssh/id_rsa.pub ```
* Copy the public key and paste it into _GitHub > Settings > SSH and GPG keys > New SSH key_
* Now you can clone the repo from your local machine using the SSH URL

# **Lab 1 - Create a GitHub Repository**
1. Go to [GithHub.com](https://github.com/) and sign up for a free account
1. For now, consider everything **public**
1. Add an avatar to your profile
1. Create a new repository
    * Name it **helloworld**
	* Add a *Description*
    * Select *Public*
	* Check *Initialize this repository with a README*
1. Find the HTTPS and SSH URLs to clone the repository (you will need this later)

# **Concepts**
* Make changes in your local computer's repo, then push them to the remote repo
* Developers have all revisions of the code, since the most recent *pull*
* There are three areas: working directory (local), staging area (local), and repository host (remote)
* You add files to be versioned, modify/delete files, commit changes to the staging area, and push files to the remote repository for all to see.

# **Basic Git Commands**

## git clone
* Clone(copy) the remote repository to your local computer
* Creates a local folder with the same name as your remote repo
* You can now make changes locally and push them to the remote server
* You need the HTTPS or SSH URL to clone a repo
* Syntax:

```sh
user@yourmachine:~$ git clone git@github.com:CoachEd/HelloWorld.git
```
* Note the new *HelloWorld* folder on your computer
* Add, modify, or delete files and folders in the local repo (HelloWorld folder)

## git status
* See the current status of your local repo
* Are there new files/folders not currently versioned?
* Are there any changes to existing files/folders?
* Are there any deleted files/folders?
* Are there any changes that need to be committed to the staging area?
* Is there anything in the staging area that needs to be pushed to the remote repo?
* Syntax:

```sh
user@yourmachine:~$ git status
```

## git add
* Add new local files to the staging area
* Can add one file at a time or all at once(.)
* Syntax:

```sh
user@yourmachine:~$ git add somefile.txt
user@yourmachine:~$ git add .
```

## git rm
* Remove a file from version control
* An alternate way is to just delete it from your local folder and commit that change
* Syntax:

```sh
user@yourmachine:~$ git rm somefile.txt
```

## git commit
* Commit any changed files
* Commit any added files
* Still have to *push* to update online repo
* Syntax:

```sh
user@yourmachine:~$ git commit -m "some useful message" .
```
* The -m option specifies a useful message for the commit

## git push
* Push commited changes from one repo to another repo
* Syntax:

```sh
user@yourmachine:~$ git push origin master
```
* The above command pushes your local changes to the master branch of your online repo

## git checkout
* Restore working files
* Switch branches
* For example, if you want to revert to the repo version of somefile.txt:

```sh
user@yourmachine:~$ git checkout somefile.txt
```
* The above command replaces your local version of *somefile.txt* with the remote repo version of it

## git diff
* Show the differences between local and/or committed files
* Syntax:

```sh
user@yourmachine:~$ git diff somefile.txt
```
* The above command compares your local version of somefile.txt with the online repo version

## Typical Workflow

```git add, git commit, git push, git commit, git push, git status, git commit, git push, ...```. 

Here are some examples:

## Example - Adding a new file
```sh
user@yourmachine:~$ git add somefile.txt
user@yourmachine:~$ git commit -m "adding a new file to the repo" .
user@yourmachine:~$ git push
```

## Example - Modifying a file
```sh
user@yourmachine:~$ git commit -m "adding a new file to the repo" somefile.txt
user@yourmachine:~$ git push
```

## Example - Deleting a file from version control, but keeping it in the remote repository
```sh
user@yourmachine:~$ git rm somefile.txt
user@yourmachine:~$ git commit -m "removed this file from version control" somefile.txt
user@yourmachine:~$ git push
```

## Example - Remove a file from version control, but leave it in the working tree and local repository
```sh
user@yourmachine:~$ git rm --cached 'docs/some dir/somefile.txt'
user@yourmachine:~$ git update-index --assume-unchanged 'docs/some dir/somefile.txt'
user@yourmachine:~$ git commit -m "removed this file from version control" 'docs/some dir/somefile.txt'
user@yourmachine:~$ git push
```

## Example - Get the online version of a file (reverting local changes)
```sh
user@yourmachine:~$ git checkout somefile.txt
```

## Example - Diff a file with the version from three commits ago
```sh
user@yourmachine:~$ git diff HEAD~3 somefile.txt
```

# **Lab 2 - Using the *helloworld* GitHub Repository**
1. Clone your *helloworld* repo to your local machine
1. Go to the local *helloworld* directory
1. Create three files named: *fruit.txt*, *colors.txt*, and *universities.txt*
1. Add three entries to each file
1. Add the files to your *helloworld* GitHub repository
1. Commit the files to your *helloworld* GitHub repository
1. Add three more entries to each of the files
1. Commit these changes to your repo
1. View your files on GitHub.com
1. Look at the commit history on GitHub.com
1. Delete the *universities.txt* file from your repository
1. Commit the deletion to your repository
1. **Bonus question**: Is the *universities.txt* file gone forever? If not, can you retrieve it?

# **Ignoring Files**

Sometimes you don't want Git to version files. Instead, Git should ignore these files completely. You do that with a *.gitignore* file.

* A *.gitignore* file is a plain text file
* Commit the *.gitignore* file to your repo
* Git ignores entries in the *.gitignore* file 
* Entries may be file types, file names, or directories
* Use # for comments

Here is a sample *.gitignore* file:

```sh
# ignore a particular file
a.out

# ignore some file types in the current folder and subfolders
*.class
*.o

# ignore an entire directory
foo/
```

# **Lab 3 - Ignoring Files and Folders**
1. Create a new repository in GitHub
    * Name it *project1*
	* Add a *Description*
    * Select *Public*
	* Check *Initialize this repository with a README*
1. Clone the *project1* repo to your local machine
1. Go to the local *project1* directory
1. Create a C program named *main.c* that prints *Hello C!* to the screen
1. Compile the *main.c* program
1. Create a Java program that prints *Hello Java!* to the screen
1. Compile the Java program
1. Create a folder named *private*
1. In the *private* folder, create text files named: *ids.txt*, *addresses.txt*, *logging.c*, and *logging.java*
1. Enter ```git status``` to see the files Git knows about
1. Create a *.gitignore* file to ignore the a.out, Java class, ids.txt, and addressess.txt files
1. Enter ```git status``` to check your work 
1. Commit all additions and changes to your repo

# **Lightweight Tags**
What if you want to go back to a specific commit point? This could be a specific version of the project. You can use lightweight tags to tag the project at a particular point in time. To tag a repo:

* Commit all changes for the current version of the project
* Create the tag: ```git tag sometag```
* Push the tag: ```git push --tags```

To list existing tags in the repo:
```git tag -l```

To check out a tagged version of the project:
```git checkout sometag```

To get the tag of the current version in the local folder:
```git describe --abbrev=0 --tags```

# **Lab 4 - Tagging a Project**
1. Create a new repository in GitHub
    * Name it *project2*
	* Add a *Description*
    * Select *Public*
	* Check *Initialize this repository with a README*
1. Clone the *project2* repo to your local machine
1. Go into the *project2* directory
1. Create a file named *play.txt* with the following entries:
	* Soccer
	* Football
	* Tennis
1. Create a file named *professionals.txt* with the following entries:
	* Ronaldo
	* Prescott
	* Federer
1. Add, commit, and push the files to the remote repo
1. Create a lightweight tag named "sports.yyyymmdd", where yyyymmdd is the current date
1. Push the tag to the remote repo
1. List the tags in the local repo
1. Modify the *play.txt* file to have just these entries:
	* Rock
	* Rap
	* Country
1. Modify the *professionals.txt* file to have just these entries:
	* Journey
	* Run-D.M.C.
	* Garth Brooks
1. Commit and push your changes to the remote repo
1. Create a lightweight tag named "music.yyyymmdd", where yyyymmdd is the current date
1. Push the tag to the remote repo
1. List the tags in the local repo
1. Check out the sports.*yyyymmdd* tagged version of the project
1. Note that the *play.txt* and *professionals.txt* files have changed back

# ** Git Branching **

Git allows you to create branches of your project. 

* Branches are like different versions of your project
* Branches may stay separate, or they can merge
* For example, you may have three branches of a project for three separate customers
* Another example is having master and develop branches
    * You typically see this in DevOps environments
	* You can think of a master branch as a production or release version of software
	* The master branch always has a working version of the software
	* Developers *never* make changes in the master branch
	* Developers *do* make changes in the develop branch
	* When the develop branch is tested and ready for production, you *merge* the develop and master branches
	* Create a lightweight tag to tag the master release version
	* Tell the deployment team to pull the tagged release from the master branch

To create a branch:
```git branch branchname```

To check out a branch:
```git checkout branchname```

To commit changes to a branch:
```git commit -m "some message" .```

To push changes to a remote branch:
```git push origin branchname```

To pull the latest to a remote branch:
```git pull origin branchname```

To merge the current branch with another branch:
```
git checkout develop
git pull origin develop
git checkout master
git merge develop
git push origin master
```
	
# **Lab 5 - Using Master and Develop Branches**

1. Create a new repository in GitHub
    * Name it *project3*
	* Add a *Description*
    * Select *Public*
	* Check *Initialize this repository with a README*
1. Clone the *project3* repo to your local machine
1. Go into the *project3* directory
1. Create a helloworld.java program that prints "Hello world." to the terminal.
1. Add, commit, and push it to the master branch. This is the initial push to create the master branch.
1. Create a new branch named *develop*
1. Switch to the *develop* branch
1. Modify the helloworld.java file
1. Commit and push the change to the develop branch
1. Make a few more changes to the helloworld.java file and commit/push them to the develop branch
1. Go into GitHub and note the differences in the master and develop versions of the helloworld.java file
1. Switch to the master branch
1. View the helloworld.java file; note that the development changes are not there yet
1. Merge the master branch with the develop branch
1. Push the merge into the remote repo
1. Create a lightweight tag named *v1.0*
1. Push the tag into the remote repo
1. Go into GitHub and note the differences in the master and develop versions of the helloworld.java file

# Multiple Contributors

Git allows multiple developers to contribute to the same project. With a web host like GitHub, developers may be remote. 

If possible, try to avoid having multiple developers modify a single file simultaneously. However, Git can merge changes if developers modify independent sections.

# **Lab 6 - Multiple Contributors on One File **

This lab demonstrates how multiple contributors can work in the same repo. If multiple developers modify independent sections of the same file, then Git will merge changes.

*Teacher*

1. Clone the MultipleContributors repo: ```user@yourmachine:~$ git clone git@github.com:CoachEd/MultipleContributors.git```
1. Add each student as a collaborator: MultipleContributors > Settings > Collaborators > Add collaborator
1. Assign students to modify specific sections in Foo.java
1. Install Java JRE and SDK

    ```user@yourmachine:~$ sudo apt-get update```
	
	```user@yourmachine:~$ java -version```
	
	```user@yourmachine:~$ sudo apt-get install default-jre```
	
	```user@yourmachine:~$ sudo apt-get install default-jdk```
		
1. Run the completed Java program

*Students*
1. Clone the MultipleContributors repo: ```user@yourmachine:~$ git clone git@github.com:CoachEd/MultipleContributors.git```
1. Modify your section in Foo.java
1. Commit your change

# Gitlab at MITRE
[Gitlab at MITRE](https://gitlab.mitre.org/)
Gitlab at MITRE is like GitHub, but it's hosted inside MITRE. You have access to Gitlab.

# **Lab 7 - Access Your MITRE Gitlab Account**

* Go to [Gitlab at MITRE](https://gitlab.mitre.org/)
* Log in with your MITRE SUI and passwords
* Create a repository
* Add your public SSH key to your Gitlab account
* Clone the repo
* Add a file to the repo
* Commit the file to the repo

# MITRE Atlassian Portal
[MITRE Atlassian Portal](https://login.codev.mitre.org/portal)
The MITRE Atlassian Portal is like Bitbucket.org. It includes MITRE Codev tools (more than just Git). The MITRE Atlassian Portal requires access from the administrator.

# **Lab 8 - Atlassian Stash Overview**

* Log into the [MITRE Atlassian Portal](https://login.codev.mitre.org/portal)
* Navigate the different sections
* View other repos
* View Confluence (documentation)
* View Kanban

# Collaboration and Git

* Communication is important in an Agile Development Environment
* Email is klunky
* Skype is also klunky
* Knowledge and communication are better in the flow

## Slack

* Slack is a popular, web-based, real-time, persistent chat application
* Lots of integrated applications (e.g., JIRA, Trello, ...)
* Available on multiple platforms (desktop, web, mobile)
* NASA JPL uses Slack
* MITRE approves Slack, but under specific security requirements

# **Lab 9 - Create a Personal Slack Account**

Create a Persona Slack account:

* https://slack.com/
* Use a personal email address
* Send me your email address, so I can invite you to the _eatstraw_ Slack team: https://eatstraw.slack.com
* Explore Slack
* Send a message to a public channel
* Send a direct message to someone

## Trello

* Trello is a popular, web-based, collaboration tool that allows you to organize tasks in _boards_
* Like Kanban boards in the Agile Development Methodology
* Integrates with Slack
* Wekan is an open source version of Trello
* MITRE has an internal Wekan site: http://kanban.mitre.org/

# **Lab 10 - Create a Personal Trello Account**

Create a personal Trello account:

* https://trello.com/
* Use a personal email address
* Send me your email address, so I can invite you to the _eatstraw_ Trello team: https://trello.com/
* Claim one of the Student tasks by renaming it with your name
* Move your Student task to the In-Progress List
* Add some information to your Student task
* Tell the Slack _trellobot_ user to do Trello things
* See Trello notifications in the Slack _#trello_ channel

# Git and Slack

* Git integrates with Slack
* See notifications in the _#git_ Slack channel

# **Lab 11 - Pulling it all Together**

In this lab, we will assign tasks, collaborate on Slack, and modify a Git repository.

* Send me your GitHub email address, so I can invite you to be a collaborator on my _eatstraw_ GitHub repository
* Look for a Trello task with specific instructions (I will assign tasks to teams of students)
* Coordinate on Slack with your teammate(s) to make the changes
* Commit your changes to the GitHub repository
* See the notifications in the _#git_ and _#trello_ Slack channels
* Mark your Trello task as done

# Markdown Files

* Markdown is a lightweight syntax for styling documentation on GitHub
* [GitHub Guides: Mastering Markdown](https://guides.github.com/features/mastering-markdown/) 
* [Atlassian Documentation: Markdown syntax guide](https://confluence.atlassian.com/bitbucketserver/markdown-syntax-guide-776639995.html) 
* Some online Markdown editors:
    * [Dillinger](http://dillinger.io/)
    * [JBT](https://jbt.github.io/markdown-editor/)
    * [StackEdit](https://stackedit.io/editor)
* Guess what? This course is taught through a Git README.md file

# **Lab 12 - Create a Markdown File**

It is good practice to place a README.md file in your repo. Create a README.md file in any of your repos:

* Use H1 and H2 headings
* Create a ordered list
* Create an ordered sublist
* Create an unordered list
* Create an unordered sublist
* Make some text *bold*
* Make some text _italics_
* Add an _images_ folder to your repo
* Add some image to the _images_ folder in your repo
* Add the image to your README.md file

###### **TODO:**
* Git submodule example
* Cloning or downloading zip file of TTA566 Gitlab repo


