\

GitHub Inc. is a web-based hosting service for version control using
Git. It is mostly used for computer code. It offers all of the
distributed version control and source code management functionality of
Git as well as adding its own features.

Github repo - **origin or remote**

To install git : **yum -y install git-core**

To view git version : **git \--version**

[[Few commands to customise git environment
:]{.underline}]{style="color: rgb(128,0,0);"}

[        To change username : ]{style="text-decoration: none;"}[**git
config \--global
[user.name](http://user.name)**]{style="text-decoration: none;"}
**"user_name"**

        To change email id : **git config \--global user.email
email_id**

        To enable colour highlighting : **git config \--global color.ui
true**

**                                                                  git
config \--global color.status true**

**                                                                  git
config \--global color.branch true**

        Listing git settings : **git config \--list**

**\**

**\
GIT LIFECYCLE :**

\

\

[**GOOD PRACTICE :**]{.underline}

When creating a feature, always branch off to a new branch and make
changes there. And push your branch and create a pull request which is
to be reviewed by your manager/mentor. He will then merge your branch
into the main master branch and your code would be live.

\

[Important commands :]{.underline}

      Create branch -\> **git branch branch_name**

      Go to that new branch -\> **git checkout branch_name**

      Add your files to staging area -\> **git add filename or git add**
.

      Commit your changes with a message -\> **git commit -m "Commit
message"**

      Push your changes -\> **git push -u origin branch_to_be_pushed**

      Adding existing project to github -\> **git init**(in project's
working directory) + **git remote login origin \<repository url\>**(just
before pushing the project)

      Useful commands -\> **git status, git log, git clone, git pull**

\

\

-Seren Jhanwar

\

\
