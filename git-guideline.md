# Git Guideline

## Table of Contents
  1.  [Introduction](#introduction)
      1. [Clone project](#clone-project)
      1. [Remote upstream](#remote-upstream)
      1. [Rebase upstream](#rebase-upstream) 
  1.  [Gitflow](#gitflow)
      1. [Resources](#resources)
      1. [Main branches](#main-branches)
      1. [Features](#features)  
  1.  [Commit messages](#commit-messages)
      1. [Format](#format)
      1. [Types](#types) 
      1. [Subject](#subject)
      1. [Body](#body)
      1. [Footer](#footer)   

## Introduction 
Before you begin you must make a copy of the project. Go on project and click on fork. You now have a copy of the project in your github repositories.

### Clone project
Now you can clone the project to your computer :

```sh
git clone git@github.com:myname/myrepo.git
```

### Remote upstream
To update your fork it's necessary to have a remote from main project in upstream directory :

```sh
git remote add upstream https://github.com/mythiqueteam/mythique.git
```

Now you can fetch code from main project :

```sh
git fetch upstream
```

### Rebase upstream
Before proposing the feature it's important to be updated, this requires rebase
. 
First, update your upstream branch :

```sh
git checkout upstream/master
git pull
```

Then go to origin/develop and rebase from upstream :

```sh
git checkout master
git rebase upstream/master
```

Once corrected, you can push on your project and make a pull request !

## Gitflow
To facilitate teamwork, it's best to use gitflow. Gitflow is a workflow for git users with a lot of conventions. 

### Resources

- Understand Gitflow : http://nvie.com/posts/a-successful-git-branching-model/

### Main branches

- **master**: Contain the released versions of the project
- **develop**: Contains the latest valid feature

### Features
Every features should be develop in his own branch. To create feature use this command when you are on develop:

```sh
git flow feature start feature-name
```

When the feature is finished, specifiy the id of closed issue on footer(#footer) and run command :

```sh
git flow feature finish feature-name
```

Now the feature is merged on your develop, push it and make pull request !

## Commit messages
Naming conventions in commit messages makes reading pull request easier and gives a better view of the existing application.

### Format
A commit message can contain up to three parts `header`, `body` and `footer`.
The `header` is required, while `body` and `footer` depend on context.

```sh
type : subject
[blank line]
body
[blank line]
footer
```

### Types
Types are allow for a quick overview of the commit. Respect these conventions lets talk about the same thing !

- **refactor**: Code change but nothing else
- **feat**:     Add or modify feature
- **fix**:      For bug fix
- **perf**:     Improve code performances
- **test**:     Improve application tests
- **design**:   Improve design
- **content**:  Add or modify content
- **doc**:      Improve documentation
- **typo**:     Correct typography
- **noise**:    When the commit is just noise like non-breaking space 

Usually you need to reduce your commit to one type, but in practice it will happen that several types are found in one commit. In such cases the previous hierarchy is important.

For example, if my commit fix a bug and add some documentation, the first in the list (fix) is the type to use. 


### Subject
The subject is a short description which specifies the commit.

    - First word are an action verb 
    - Use the present imperative
    - Written in lower case
    - No point at the end
    - Less than 10 characters

### Body
The body can sometimes be used to clarify an important part of commit.It brings the precision when necessary and is often longer than the subject.

    - First word are an action verb 
    - Written in lower case
    - Use the present imperative
    - No point at the end
    - Less than 100 characters

### Footer
The footer is used to specify the id of closed issue. Simply specify the ticket number as shown below :

```sh
close #9
```

### Example

```sh
feat : change the countdown display

change count to depends on the number life points at level 10

close #32
```

### Annotations

Annotations should usually be written on the line immediately above the relevant code. The annotation keyword is followed by a colon and a space, then a note describing the problem:

  - use TODO to note missing features or functionality that should be added at a later date
  - use FIXME to note broken code that needs to be fixed
  - use OPTIMIZE to note slow or inefficient code that may cause performance problems
  - use HACK to note code smells where questionable coding practices were used and should be refactored.

Note: copy from synbioz/guidelines
