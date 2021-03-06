Version control (Git) and remote collaboration (Github)
=======================================================

From [Why should I use version control?](http://stackoverflow.com/questions/1408450/why-should-i-use-version-control):

> Have you ever:

> * Made a change to code, realised it was a mistake and wanted to revert back?
* Lost code or had a backup that was too old?
* Had to maintain multiple versions of a product?
* Wanted to see the difference between two (or more) versions of your code?
* Wanted to prove that a particular change broke or fixed a piece of code?
* Wanted to review the history of some code?
* Wanted to submit a change to someone else's code?
* Wanted to share your code, or let other people work on your code?
* Wanted to see how much work is being done, and where, when and by whom?
* Wanted to experiment with a new feature without interfering with working code?

> In these cases, and no doubt others, a version control system should make your life easier.

> To misquote a friend: A civilised tool for a civilised age.

My personal experience is inheriting projects that look like this:

<p align="center">
  <img src="img/folder.png" height="400"/>
</p>

Which version do you use? What are the differences between versions, and *why* were the changes made? Do any have useful functionality that's not in the main version? Version control cleans this mess up, and offers a host of other useful features.

Git is the standard, and, like json, there are *so many* users that you can find tutorials everywhere. Here is a curated list:

 * [An entire section in Software Carpentry](http://software-carpentry.org/v5/novice/git/index.html) and [the corresponding git repo](https://github.com/swcarpentry/boot-camps/tree/master/version-control/git/local)
 * [A tutorial written by the founder of Github](http://git-scm.com/doc)
 * [A three-hour youtube video explaining git, Github, and science](https://www.youtube.com/watch?v=T0BE9ApIegc)
 * [A stack overflow post on git for beginners](http://stackoverflow.com/questions/315911/git-for-beginners-the-definitive-practical-guide)
 * [An interactive web app for learning git, by Github](https://try.github.io/levels/1/challenges/1)
 * [A git lesson in a scientific programming tutorial](http://nbviewer.ipython.org/github/jrjohansson/scientific-python-lectures/blob/master/Lecture-7-Revision-Control-Software.ipynb)

**Install Git (if necessary)**
* Windows (go to github)
  * https://windows.github.com/
* Mac (brew install git)
  * If you don't have homebrew go to (http://brew.sh/) for instructions
* Linux
  * `sudo apt-get install git`
  * `sudo yum install git`
  * etc.

**Configure Git (if necessary)**
* Using the commandline
  * Open "GitShell" on Windows
  * Otherwise just open a terminal
* Type:
  * `git config --global user.name "John Doe"`
  * `git config --global user.email johndoe@example.com`

**A "Hello World" example for version control**
* Creating your first repository
* Start with a folder you already have OR
* Create a new folder (which is what we'll do now)
  * `mkdir firstrepo`
  * `git init`
  * `cd firstrepo`
* Create your first few files, "stage" them, and then commit them
  * `touch helloworld.txt`
  * notice that git has detected a change to the repository already
  * `touch goodbyeworld.txt`
  * Let's say we're pretty sure we want to commit helloworld but not necessarily goodbyeworld
  * `git add helloworld.txt`
  * `git status`
  * `git commit` <-- you will be asked to describe the new change
  * helloworld.txt is now permanently part of your git repository
  * `rm helloworld.txt`
  * `git checkout -- helloworld.txt`
  * Let's add a line to helloworld.txt, open text editor and type "2+2=5"
  * If you add a bunch of files, you don't have to individually stage them
  * `git add *.txt`
  * `git commit` <-- now both of our text files are committed
* Looking at differences between versions
  * Open helloworld in a text editor and edit the first line to "2+2=4"
  * Assume you have a very short memory and want to know what helloworld.txt used to contain before you commit
  * `git diff`
  * Ah, it use to say "2+2=5" which is clearly wrong, so you can safely commit
  * `git commit` <-- "corrected basic arithmetic error"

**Contributing to projects on GitHub**
* A big benefit of good version control is working in teams on a project
* GitHub is a very popular platform for hosting Git repositories and makes everything easier to work with
* Start by forking a GitHub repository (you will need a GitHub account)
  * Go to https://github.com/patrickfuller/fomms-2015
  * Click "fork" on the upper right hand corner of the screen
* You have a forked copy of the project online, but you also want a local copy on your laptop
  * Navigate to a folder where you want to put the downloaded repository
  * `git clone https://github.com/[YOUR ACCOUNT NAME]/fomms-2015.git`
  * That's it, you've now downloaded a fork of our tutorial repository
* Make a change to it (any change!)
  * Open the "README.MD" file in a text editor
  * Change some text
  * `git add README.MD`
  * `git diff` <-- double check your changes
  * `git commit`
  * The change you've made is still local to your computer
  * `git push origin master`
* Now that your change is made in your online GitHub repository, you can request that your change is merged with the "master" copy by issuing a pull request
  * Go to your GitHub repository and click on pull request
  * Then click on "Issue pull request" and describe in detail your changes
  * The project maintainer will then approve if the pull request if he/she likes it, or comment on your changes if there is a problem
