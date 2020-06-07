Welcome to the first `git`/github tutorial in the Yesselman Group's general programming repo
## Part I: What is `git`? Why does it matter? 
`git` is a command-line, open-source version control system for source code. In plain english, `git` is a development tool for sharing, changing and updating projects. The main idea behind version control is to make it easier for multiple programmers to work on a project together by automating the process of updating, saving and distributing the source files for a project. Consider a scenario where you and another programmer are both contributing to a project. You both start with a static copy of the source files and work on different features. When you have finished your ground-breaking code, it's time to merge your changes into an updated version of the project. The "old" way of doing this is to take each of the changed copies and to copy and paste the changes from one into the other, in turn making this the new master source code. While this method can work, there are a number of issues with manual version control:
  + poor scalability - especially for larger projects (10k lines of code or more) this method becomes increasingly slow, easily taking 10-15 minutes to apply an update
  + potential for human error - updates are subject to copy and pasting mistakes! this is a major problem as every update can lead to a potential change in functionality or the emergence of new bugs
  + no back up - since all the files are stored as local copies, a crash for any of the contributors could lead to significant loss of progress
  `git` aims to solve most of the above problems by using an automated system to monitor changes. Namely, `git` boasts the following advantages over manual version control:
  + strong scalability - `git`'s system is fast, even for large projects with thousands to millions of lines of code
  + consistent procedures - in being automated, `git` avoids unpredictable behavior and the potential for human error
  + distribution - because `git` is a commandline tool, projects can be downloaded with a single command instead of having to email around tarballs or zipped files of source code
  + security - by using `git` in tandem with github, projects can be backed up remotely so that the failure of any one computer's memory will not jeopardize a project at large
  + version access - `git` can keep track of changes in a project, allowing programmers to revert back to a specific saved state in a project. this is hard to achieve without making unique copies of a project for each update, which can become storage intensive very quickly

Clearly, `git`/github are superior to manual version control, but there are other reasons to use the technology. Github is the standard means for sharing code and contributing to projects, especially in science. Some examples of projects hosted on github include:
  + Gromacs
  + OpenMS
  + RNAMake
  + Rossetta
  + XCMS
*...and many many more!*

So now that you see the importance of using `git`/github, we can start using it! To complete the rest of the tutorial, you will need to have `git` installed as well as a github account. If you do not have `git`, you can:
+ install it on mac with `$ brew isntall git`
+ install it on linux with `$ sudo apt install git-all` (sub `apt` for `dnf` for most non-Debian distributions)
+ install it on windows by going to this [link](https://git-scm.com/download/win) and follwing the directions

If none of the above options work, go to this [link](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) to find additional instructions for your machine. 
To setup a github account, go github's [website](https://github.com/) and follow the on-screen directions to setup an account. With this all set up, you can move onto the next stage!
## Part II: Understanding repo's and making a clone of an existing project

In the scope of github, a repository, or repo, is the space in which a single project lives. For most purposes, a repo is equivalent to a directory and can hold almost anything you can put in a directory on your computer, though there are often storage limits on github. Roughly speaking, a repo **is** a project, so understanding how to maneuver them is key to using `git`/github. 

There are two main types of repos: remote and local. Remote repos are stored on github and serve as "master" copies of a project. These are usually where the main changes are updated and saved, thereby making them accessible to all of the people working on a project. On the other hand, a local repo is the copy of a project that you have on your computer. A repo can be downloaded to your computer using the following command `$ git clone <github-URL>`. Moving forward, you will be working with the `test_project` project. Clone the repo using the command `$ git clone https://github.com/YesselmanLab/test_project.git`.

As updates are made to a project (how to do so will be discussed later) there are three main scenarios you can find yourself in:
1. The local and remote repo's are identical. This scenario is pretty straightforward and where you likely where you find yousrself now. There is no difference between the the local and remote versions of the project. 
1. The local repo is "ahead" of the remote repo. In this situation, updates have been made to the local version of the project and these updates have not been applied to the remote repo. 
1. The remote repo is "ahead" of the local repo. In this situation, updates have been made to the remote version of the project and these updates have not been applied to the local version of the repo.
