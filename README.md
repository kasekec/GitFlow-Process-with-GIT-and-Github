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
