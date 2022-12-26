# What is Git?

Hello World!

In this blog let us see what is git and how it is used in industry.

#### What is Git?

Git is a *Distributed Version Control System* (DVCS), that holds the whole history of the project, including the changes. It is built with security, performance and flexibility in mind. It was developed in 2005 by **Linus Torvalds** the famous creator of the Linux kernel.

#### What is a Version Control System (VCS)?

A system that records changes to a file or set of files over time is called a Version Control System. This enables us to recall a specific version later.

#### Why do we need a VCS?

* VCS are essential for **collaboration**. When many people work on the same project, they will be working on shared files. There are many conflicts like only one person will have access to a file at a time. There are chances that someone may overwrite your content. In VCS, this is prevented. Everybody can work on any files, without any conflicts and can merge all into a common version.
    
* It is very hard to maintain different versions of the project, like naming versions, comparing two versions, etc. But VSC will make these tasks simple.
    
* We can restore previous versions of the project easily and it acts as a backup as well.
    

**Some of the previous version control tools**:

* RCS (Revision Control System)
    
* SCCS (Source Code Control System)
    
* Bit Keeper (Proprietary VCS, where Linux is built)
    

### History of VCS

As I said earlier, it is a Distributed Version Control System. Let us quickly look into DVCS and other previous VCSs.

1. **Local Versioning System (LVS)**: A database that stores different versions of files. Its main drawback is that we cannot collaborate with another team member. Everything is local.
    
2. **Centralized Version Control System (CVS)**: Here all the versioned files are stored in a centralized server. The members of the team can check out the files from the server. There was a certain degree of possibility to know what other members of the project are doing. Its drawback is everything is stored in the centralized server. When the server crashes, everything is gone. We cannot also work when the server is down. Saving the entire history of the project in a single place is a high risk.
    
3. **Distributed Version Control System (DVCS)**: In DVCS, unlike the other VCS, the whole project including its history is mirrored into the client’s device. So even when the centralized server crashes, we can revamp from the client’s clone. This enables us to collaborate with different groups of people differently, simultaneously.
    

#### Git vs other DVCS

Like Git we have other DVCS like Mercurial, Bazzar, and Darcs. Let us see how Git stands out from these DVCS.

* Git thinks about data, whereas others think about file changes.
    
* Git stores the snapshots and not the differences.
    
* Nearly every operation is local, as we have the entire history of the project on our local disk. We can work even when we don’t have internet or we have a bad network. The files will be uploaded once we get a good network connection.
    
* Integrity: Everything is check-summed before getting stored (SHA1 hash).
    

Let’s dive technically into git.

#### The three states

There are three states in git

* Modified — When some file is modified in the repo.
    
* Staged — When modifications are done and files are staged.
    
* Committed — When staged files are finalized and committed.
    

#### How to install it?

> **Linux**:

> $sudo dnf install git-all (For RPM-based distributions)

> $sudo apt install git-all (For Debian, Ubuntu distributions)

**Mac**:

> $git — version

If it is not installed, it will prompt to install.

**Windows**:

> Follow this link: [https://git-scm.com/download/win](https://git-scm.com/download/win)

#### Git config

Get and set configuration variables that control all aspects of how it looks and operates

**Global Configuration**

Here we will be configuring things like username, email, etc

> git config — global user.name “sriram23”

> git config — global user.email

### Repository (or) Repo

Any directory that has a ‘.git’ directory in it is called a git repository. The ‘.git’ directory will have the complete history of the project.

#### Creating a git repo

I will create a new directory and make it a git repository.

> $mkdir myFirstGitRepo

> $cd myFirstGitRepo

> $git init

This will create a directory called myFirstGitRepo and once the git init command is executed, a *.git* directory will be created.

#### Cloning an existing repo

We can clone an existing remote repo. We can do it by using the **git clone** command.

> git clone “[https://github.com/sriram23/Battery-Tracker.git](https://github.com/sriram23/Battery-Tracker.git)”

Hope this is useful. Thank you!