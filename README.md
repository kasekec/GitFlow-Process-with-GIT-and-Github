# Gitflow Workflow
## A step by Step guide on using GitFlow worklow with GIT and Github for collaboration

Gitflow Workflow is a Git workflow design that was first published and made popular by Vincent Driessen at nvie. The Gitflow Workflow defines a strict branching model designed around the project release. This provides a robust framework for managing larger projects.

Gitflow is ideally suited for projects that have a scheduled release cycle. This workflow doesn’t add any new concepts or commands beyond what’s required for the Feature Branch Workflow. Instead, it assigns very specific roles to different branches and defines how and when they should interact. In addition to feature branches, it uses individual branches for preparing, maintaining, and recording releases. Of course, you also get to leverage all the benefits of the Feature Branch Workflow: pull requests, isolated experiments, and more efficient collaboration.

## Getting Started

### Installation
To use GitFlow, you will first need to install Git on your machine.

For installation on Windows, Mac or Linux, follow the instructions in the article [here](https://www.digitalocean.com/community/tutorials/how-to-contribute-to-open-source-getting-started-with-git)

Once Git is installed and ready to go, you can begin working with GitFlow.

### Step 1 - Create a new Directory and Initialize GitFlow
```sh
mkdir GitflowGuide
cd GitflowGuide
git flow init
```

### Step 2 - Create New Feature Branch

 Each new feature resides in it's own branch, which can be pushed to the central repository (GitHub, Bitbucket etc.) for backup/collaboration. But, instead of branching off of 'master', 'feature' branches use 'develop' as their parent branch. When a feature is complete, it gets merged back into 'develop'. A common rule of thumb is that features should never interact directly with master.

#### Starting a feature branch
```sh
git flow feature start flowFeature
```
#### Finishing a feature branch
```sh
git flow feature finish flowFeature
```

### Step 3 - Release Feature Branch

Once 'develop' has acquired enough features for a release, you fork a 'release' branch off of 'develop'. Creating this branch starts the next release cycle, so no new features can be added after this point. Only bug fixes, documentation generation, and other release-oriented tasks should go in this branch.

#### Starting a Release branch
```sh
git flow release start 0.1.0
```

#### Finishing a Release branch
```sh
git checkout master 
git merge release/0.1.0 
git flow release finish '0.1.0'
```
This will send you into the vim text editor 
- Press i to enter insert modeType in your message (e.g. v0.1.0), 
- press ESC to exit insert mode, and 
- type zz to save and exit. Alternatively, you can type in :wq and hit ENTER


#### Hotfix branches

Maintenance or “hotfix” branches are used to quickly patch production releases. Hotfix branches are a lot like release branches and feature branches except they are based on 'master' instead of 'develop'. This is the only branch that should fork directly off of 'master'. As soon as the fix is complete, it should be merged into both 'master' and 'develop' (or the current release branch), and 'master' should be tagged with an updated version number

#### Starting a Hotfix branch
```sh
git flow hotfix start v1
```

#### Finishing a Hotfix branch
```sh
git checkout master 
git merge hotfix/v1 
git flow hotfix finish v1
```
This will send you into the vim text editor 
- Press i to enter insert modeType in your message (e.g. v0.1.0), 
- press ESC to exit insert mode, and 
- type zz to save and exit. Alternatively, you can type in :wq and hit ENTER


## Summary

This guide described a typical Gitflow Workflow. Gitflow is one of many styles of Git workflows you and your team can utilize.

Some key takeaways to know about Gitflow are:
- The workflow is great for a release-based software workflow.
- Gitflow offers a dedicated channel for hotfixes to production.

The overall flow of Gitflow is:
1. A develop branch is created from master
2. A release branch is created from develop
3. Feature branches are created from develop
4. When a feature is complete it is merged into the develop branch
5. When the release branch is done it is merged into develop and master
6. If an issue in master is detected a hotfix branch is created from master
7. Once the hotfix is complete it is merged to both develop and master