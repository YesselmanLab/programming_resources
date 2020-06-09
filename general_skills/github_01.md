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
## Part II: Understanding repo's, cloning and branches

In the scope of github, a repository, or repo, is the space in which a single project lives. For most purposes, a repo is equivalent to a directory and can hold almost anything you can put in a directory on your computer, though there are often storage limits on github. Roughly speaking, a repo **is** a project, so understanding how to maneuver them is key to using `git`/github. 

There are two main types of repos: remote and local. Remote repos are stored on github and serve as "master" copies of a project. These are usually where the main changes are updated and saved, thereby making them accessible to all of the people working on a project. On the other hand, a local repo is the copy of a project that you have on your computer. A repo can be downloaded to your computer using the following command `$ git clone <github-URL>`. Moving forward, you will be working with the `test_project` project. Clone the repo using the command `$ git clone https://github.com/YesselmanLab/test_project.git`.

As updates are made to a project (how to do so will be discussed later) there are three main scenarios you can find yourself in:
1. The local and remote repo's are identical. This scenario is pretty straightforward and where you likely where you find yousrself now. There is no difference between the the local and remote versions of the project. 
1. The local repo is "ahead" of the remote repo. In this situation, updates have been made to the local version of the project and these updates have not been applied to the remote repo. 
1. The remote repo is "ahead" of the local repo. In this situation, updates have been made to the remote version of the project and these updates have not been applied to the local version of the repo.

Another important facet of using `git`/github is understanding branches. A branch is a specific version of a repo and can be manifested both locally and remotely. It's very common for each branch to be devoted to a specific purpose. A typical project would often have branches as follow:
  + a `master` branch that contains the production code ready for use (note that each project comes with a single `master` branch by default)
  + a `devel` or `developer` branch that contains code for in-progress features not ready for deployment
  + a variety of programmer-specific branches where person stores the specific updates and progress they are working on
  + versions of the code for different target operating systems

With all of this basic knowledge, we can now take a look at typical `git`/github workflow.

## Part III: Basic Workflow
Here we will cover what basic workflow you will encounter when using `git`/github. It should be noted that this coverage is slanted towards doing work on a large project, so some of these steps will not be relevant for smaller projects. In general, it's good to remember that there are not one size fits all solutions. Follow along with the below commands and their descriptions:
  + from `test_project/`, enter the command `git checkout -b "[NAME]_dev"`. This action creates a new local branch, called `[NAME]_dev`, which is where you will be doing your work.
  + enter the command `git show-branch`. This should show all of branches in the project and there should be an asterisk next to the branch you are on. 
  + `$ echo "THIS IS AN EXTRA LINE" >> README.md && echo "THIS IS A NEW FILE" >> newfile.txt`. This will concatenate the text "THIS IS AN EXTRA LINE" to the end of the readme and make a new file, `newfile.txt`
  + `$ git status`. This will show the current status of the local repo, which includes things like untracked files and changes.
  + `$ git add newfile.txt` The command `git add` will add the named file to the repo. To add all of the files in a directory, you can altertnatively run the command `$ git add .`. At this point, running `$ git status` would show that `newfile.txt` had been added to the repo.
  + `$ git commit -a -m "[COMMIT COMMENT]"`. This command will commit the changes on the local repo. These changes will be associated with the `[COMMIT COMMENT]` you choose, so make sure that it is a meaningful comment that describes the changes you are making. If you were to run `$ git status` again, you would see that 
  + `$ git checkout master`. This changes the current branch to `master`, instead of the `[NAME]_dev` branch you have been using.
  + `$ git merge [NAME]_dev`. This command will merge the changes made on the `[NAME]_dev` branch to `master`. If there are no conflicts this will occur automatically, but if there are merge conflicts, you will have to manually resolve these merge conflicts. Conflicts generally emerge from when the same code is altered on different branches. In reality, this is unlikely to occur on smaller projects, but if you find yourself in a situation where you need to resolve a conflict, you can refer to this [guide](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-merge-conflicts). 
  + `$ git pull origin`. This command will "pull" any changes from origin, as some files may have been changed on the remote side since the last local pull. Here there is also potential for merge conflicts to arise. The procedure for resolving them is the same as in the `merge` step.
  + `$ git push origin`. This command will "push" any changes from the local origin to the remote origin, in turn updating it with the local changes made on your machine. Again, as before there is a potential for merge conflicts to arise. 
  
That's it! The commands above are the basic workflow for a larger project with multiple branches. In practice, you will often make commits directly to the `master` branch, especially on smaller projects. If this is the case, the below commands will usually be sufficient:
+ `$ git add [FILES]`
+ `$ git commit -a -m "[COMMIT COMMENT]"`
+ `$ git pull origin`
+ `$ git push origin`

It should be noted that this method is NOT recommended for projects you do not own. That being said, it is often not necessary to have multiple branches especially for smaller projects. 
### Part IV: Starting A Repository

The last major topic to discuss is how to create a repo. There are two general cases when it comes time to start one:
1. Nothing has been done and you are starting the repo from scratch (typically more common)
1. Some work on the project has already been done but you still want to start a new repo

In both of these cases, you will need to press the "create a new repository" button on your profile page or go to [this](https://github.com/new) link. Before clicking the "create repository" button at the bottom, you will need to give the repo a name. This project name will be identical to the project name later on, so make sure you like it! While it can be changed, re-naming a repo is generally not recommended. In the event that some work has already been done on the project, you will want to make sure that the repo has the **EXACT** same name as the directory you are working out of. Next, you will choose the privacy setting of the repo. There are two options: public and private. These settings behave as you would expect and other users must be directly invited to private repos, else they will be unreachable/not visible to outside users. More settings do exist on this page, but at this point you can create the repo by clikcing the green "Create Repository" button at the bottom of the page. 

With the repo created, it is time to make the first commit. For both situations, github presents clear instructions on what to do, and they are largely the same, with the major difference being that a commit must first be made for the "from-scratch" project. In this case, the command `$ git init` must first be run, which serves to establsh a git repository in the current directory. Next, the directions recommmend making a Readme and then adding and comitting it to the repo with the commands `$ git add README.md` and `$ git commit -m "first commit"`, respectively.

From here on, the steps are identical for either repo situation. At this point, there is a local repo on your computer and an empty one on Github's server. These two need to be merged, which is accomplished with the command `$ git remote add origin [URL]`. Now that these two are linked together, the initial push from the local to remote repo is achieved with `$ git push -u origin master`. Congrats, you have now created a repo! It is actually surprisingly easy, and in the event that you run into any issues, do not hesitate to search for answers on Google, stackoverflow, etc! `git`/github are industry standard and a lot of questions have already been answered out there. 
### Homework
(T/F) Manual version control actually has many advantages and it is often difficult to determine if you should use `git`/github or not. 

(T/F) There are two types of repos: local and remote.

(T/F) `git` is the underlying version control software whereas Github is a commercial implementation leveraging the technology for remote use. 

(T/F) When starting a repo, you **CANNOT** have any files in the initial directory. 

Bug busters: You have been working very hard on a team repository and making great progress. You have been saving your amazing files to your local repo using `$ git commit` to avoid losing progress. When your co-worker Allison clones in the repo, however, she does not see the work you have done. What could be going on here? 

Explain what the following `git` commands do:
  + `$ git commit`
  + `$ git pull origin`
  + `$ git init`
  + `$ git remote add` 

Make a **public** repo on your own account called "github-hw1". Once you create the repo, you must: 
+ Add a python script, an image of some sort, a .csv file and update the README.md using `$ git commit`
+ Make at leat **5** commits to the remote repo using the commands `$ git pull origin` and `$ git push origin`
+ Make another `branch` using `$ git checkout` and naming the branch `devel`. You will put another python script on this branch. 
