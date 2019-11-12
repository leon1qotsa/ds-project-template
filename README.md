# Project Name

#### -- Project Status: [Active, On-Hold, Completed]

## Project Intro/Objective
The purpose of this project is ________. (Describe the main goals of the project and potential civic impact. Limit to a short paragraph, 3-6 Sentences)

### Collaborators
|Name     |  Github Page   |
|---------|-----------------|
|Joao Amaro | [joaoamaro](https://github.com/leon1qotsa)|

### Methods Used
* Machine Learning
* Data Visualization
* Predictive Modeling
* etc.

### Technologies
* R
* Python
* Pandas, jupyter
* etc.

## Project Description
(Provide more detailed overview of the project.  Talk a bit about your data sources and what questions and hypothesis you are exploring. What specific data analysis/visualization and modelling work are you using to solve the problem? What blockers and challenges are you facing?  Feel free to number or bullet point things here)


_This document is still in a ```WIP``` state, which means its content is still subject to changes_

# Introduction
This project is built in a way that aims to make it easier to new team members to learn and adapt to our project methodology. Here you will learn about:

* Cloning the repository to your PC;
* Project directory structure, and how you should place files in the project;
* Code standards;
* Naming conventions;
* Git workflow;
* Committing your work;

# Cloning the repository to your PC
The first step when you're starting work for a new project is to clone the repository to your PC. This way, you'll be able to collaborate with the remaining team members on the project. In the first place, our repos are based around Git, so assuming your computer is Windows-based, please install [Git for Windows](https://git-scm.com/download/win). Afterwards, navigate to the Azure DevOps project workspace, in the Repos section, as in the following picture:

![Alt](./docs/README/how_to_clone_repo.png)

Finally, clone the repository, either from:

* Git Bash: in File Explorer, open the location where you want to place the repo, right-click inside it, and choose "Open Git Bash here", and run "git clone <url-that-you've-copied>"
* Directly to the IDE: AzureDevOps directly integrates with a myriad of IDEs, so if your favorite IDE is among these (we recommend VS Code), you're in luck, just click "Clone in ..."

And that's it. You now have the repo in your computer, up and running.

# Project directory structure, and how you should place files in the project
Our projects all adhere to the following directory structure:

```bash
|   .gitignore				
|   README.md
|   requirements.txt
|   
+---conf
|       
+---data
|   +---01_raw
|   |       
|   +---02_intermediate
|   |       
|   +---03_processed
|   |       
|   +---04_models
|   |       
|   +---05_model_output
|   |       
|   \---06_reporting
|           
+---docs
|       
+---notebooks
|           
+---references
|       
\---src
    |   __init__.py
    |   
    +---d00_utils
    |       
    +---d01_data
    |       
    +---d02_intermediate
    |       
    +---d03_processing
    |       
    +---d04_modelling
    |       
    +---d05_model_evaluation
    |       
    +---d06_reporting
    |       
    \---d07_visualisation   
```

If you're new, it might seem overwhelming, but it's actually quite simple, as you'll see right now.

```.gitignore``` is the standard Git file that contains which files should not be pushed into the repository. With Azure DevOps, this file is mostly filled automagically, but in case you need and have questions, ask a team member for help.

```README.md``` is the Readme file (written in Markdown language). Guess what? You're reading it right now.

```requirements.txt``` contains all the Python packages you need to run the project code. We'll get into further detail later on.

```conf``` is used for configuration (keys, passwords, etc..) that might need to be used in the code to connect to cloud services, etc. Don't worry, none of its contents will end up online, only in your local copy.

```data``` contains multiple sub-folders, but it's clear to see that the data for our problem will be placed here. However, our repo will only have the raw data. The other folders will only contain data in your local copy. In certain cases, when the dataset is too big to fit in the repo, not even the raw data will be in the repo.

```docs``` contains the documentation for the code.

```notebooks``` is where you'll place the notebooks where you experiment with the code and features you'll be developing.

```references``` is a directory where you'll be placing objects that contain relevant information for the project, such as data dictionaries, manuals, scientific articles, business documentation, etc.

```results``` stores the final analysis documents/reports.

```src``` is where the main source code used in the project is placed. This directory contains ```__init__.py```, which is a file that makes our code into a Python module, and multiple sub-directories, each with a self-explanatory name regarding its purpose.

# Code standards
As a Data Scientist, you might come from many different academic backgrounds, with different levels of programming experience/proficiency. Despite that, you're now working in a **collaborative** project, which means you should strive to adhere to the following code standards, in order to maximize our efficiency and the quality of our work:

* Your code is expected to be properly documented. In your notebooks, you can program however you want, but when you're commiting code to the ```src```, place comments explaining your code;
* Aside from regular comments, **EVERY** class and/or method you create should be accompanied by its corresponding ```docstring```, where the purpose and process of the object is briefly described;
* Indent your code with 4 spaces (don't do it with tabs!);
* Be mindful of your line length. Whenever the line exceeds 79 characters, break the line into multiple lines (you don't need to count how many characters you have, any half-decent IDE nowadays can be configured to do this for you);
* Use spaces before and after operators, as well as after commas. This makes reading your code easier. You'll be grateful when you're asked to review teammate's code;
* Use blank lines (but sparingly) to separate your code into logical sections;
* Package imports are expected to be found at the top of the file, starting with standard library imports, followed by related third party imports, and finally local application/library specific imports. Each group is separated with a blank line;

These are just some of the coding standards that you'll need to follow. If you're interested, you can check out [PEP 8 -- Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/)

# Naming conventions
TODO: Define the naming conventions

# Git workflow
In our projects, we use this [Git branching model](https://nvie.com/posts/a-successful-git-branching-model/). This means there are two branches with an infinite timeline: ```master``` and ```develop```. 

```master``` is the main branch of the repository, and...
> the source code of HEAD always reflects a production-ready state,
```develop``` is the branch where new features ready for integration (but not yet delivered will be). Our CI/CD pipeline will integrate/merge the development branch into the master branch.

However, you won't be working directly in the develop branch. Can you imagine what'd happen if you were working with 5 other team members simultaneously, and everyone was working on the develop branch at the same time?

This is why our branching model uses supporting branches. Unlike ```master``` and ```develop```, supporting branches have a limited lifetime, and some time after being integrated, they are deleted. There are different types of supporting branches.

**Feature branches** are used to develop new features. They are checked out from ```develop```, and are merged back into it. They should be called ```feat-<short feature name/description>```

**Release branches** are used to finalize preparation of the ```develop``` branch for a new production release, including metadata preparation. They should be called ```release-<build number>```

**Hotfix branches** TODO

# Committing your work
When you complete your work/task, you commit and push your work to the remote, but you don't merge the code into the ```develop``` branch directly (let alone the ```master```). Instead, you open a pull request.

![Alt](./docs/README/pull_requests_1.png)

You'll be prompted to specify some information, such as which branch you want to merge, where do you want to merge to (hint: ```develop```), a title, label and description for your pull request, and most importantly, reviewers for your pull request, and which work item is associated with this pull request. Why are these important? The work item association will provide people with context regarding the changes you implemented, and the review process means your code is subjected to a peer reviewal process. This process increases the confidence and quality of the development process.


This file structure is based on the [DSSG machine learning pipeline](https://github.com/dssg/hitchhikers-guide/tree/master/sources/curriculum/0_before_you_start/pipelines-and-project-workflow).
