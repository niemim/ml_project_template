# Helsinki Machine Learning Project Template
> Template for open source ML and analytics projects.


[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![GitHub version](https://badge.fury.io/gh/City-of-Helsinki%2Fml_project_template.svg)](https://badge.fury.io/gh/City-of-Helsinki%2Fml_project_template)
![GitHub issues](https://img.shields.io/github/issues/City-of-Helsinki/ml_project_template)
![GitHub forks](https://img.shields.io/github/forks/City-of-Helsinki/ml_project_template)
![GitHub stars](https://img.shields.io/github/stars/City-of-Helsinki/ml_project_template)
![GitHub license](https://img.shields.io/github/license/City-of-Helsinki/ml_project_template)


{% include note.html content='Once you begin your work, rewrite this notebook (index.ipynb) so that it describes your project, and regenerate README by calling `nbdev_build_docs`' %}

## About

This is a git repository template for Python-based open source ML and analytics projects.

The template assumes the concept of Notebook Development.
This means, that you do all the data science work inside notebooks.
There is no copy-pasting! We use the [nbdev](https://nbdev.fast.ai/) tool to build python modules and doc pages from the notebooks, automatically.
This way you always have your code, results and documentation as one.
Notebooks can be executed with the [papermill](https://papermill.readthedocs.io/) tool for an automatic, well documented model update workflow. Handy, isn't it?

The template assumes that you divide your machine learning project into 5 parts:

0. Data - loading & preprocessing
1. Model - Python class code & algorithm development with small sample of data (N = 10-1000)
2. Loss - model training & evaluation with full dataset
3. Workflow - automatic model update (reproduce steps 0.-2.)
4. API - an interface to utilize your trained model

Each part has their own notebook template, that you can follow to plan and do your development.

In addition, the template comes with a working Dockerfile and .devcontainer for doing your development easily with any device.
You can extend these for your needs and for building a runtime container for your machine learning app.

The template is completely open source and environment agnostic.
Follow the installation instructions to create a new, 
independent repository with clean commit history, 
but with a copy of all the files and folders presented.
The authors of this template will not be contributors to your project,
although we are more hear what you have achieved with it!
Also, if you don't like something or know an improvement, your contribution is very welcome!

Note, that updates to the template can not be automatically pulled to child projects.

The template is developed and maintained by the data and analytics team of the city of Helsinki.
The template is published under the Apache-2.0 licence and open source utilization is encouraged!


## Contents

The core structure of the repository is the following:

    ## EDITABLE:
    data/               # Folder for storing data files. Ignored by git by default.
    |- raw_data/        # To store raw data files
    |- preprocessed_data/   # To store cleaned data
    results/            # Save results here. Ignored by git by default.
    |- notebooks/       # Save automatically executed notebooks here
    00_data.ipynb       # Extract, transfer, load data here & define related functions.
    01_model.ipynb      # Create and code test your ML model
    02_loss.ipynb       # Train and evaluate ML model, deploy or save for later use
    03_workflow.ipynb   # Define ML workflow and parameterization
    04_api.ipynb        # Define runtime API for using trained ML model
    project.in    # Add here the Python packages you want to install
    update_install_dev_reqs.sh  # run this script to install new python packages
    settings.ini        # Project specific settings. Build instructions for lib and docs.
    Dockerfile          # Define docker image build instructions
    .devcontainer       # Codespaces / VSC dev environment instructions

    ## AUTOMATICALLY GENERATED: (Do not edit unless otherwise specified!)
    docs/               # Project documentation (html)
    [your_module]/      # Python module built from the notebooks (follow the installation instructions).
    README.md           # The frontpage of your project, generated from index.ipynb
    requirements.txt    # dev / default requirements. automatically generated by pip-tools
    min-requirements.txt # lighter requirements without dev tools. automatically generated by pip-tools

    ## STATIC NON-EDITABLE: (Edit only if you know what you're doing!)
    base-requirements.in    # core tools that every project built based on the template always requires
    requirements.in    # development tools + project spesific requirements
    LISENCE                 # lisence information
    MANIFEST.in             # metadata for building python distributable
    setup.py                # settings for the python module of your project
                                         

## How to install
{% include note.html content='if you are doing a project on personal data for the City of Helsinki, contact the data and analytics team of the city before proceeding any further!' %}
### 1. On your GitHub homepage:

0. (Create [GitHub account](https://github.com/) if you do not have one already. 
1. Sign into your GitHub homepage
2. Go to [github.com/City-of-Helsinki/ml_project_template](https://github.com/City-of-Helsinki/ml_project_template) and click the green button that says 'Use this template'.
3. Give your project a name. Do not use the dash symbol '-', but rather the underscore '_', because the name of the repo will become the name of your Python module.
4. If you are creating a project for your organization, change the owner of the repo. From the drop down bar, select your organization GitHub account (e.g. City-of-Helsinki). You need to be included as a team member to the GitHub of the organization.
5. Define your project publicity (you can change this later, but most likely you want to begin with a private repo).
6. Click 'Create repository from template'

This will create a new repository for you copying everything from this template, but with clean commit history.

### 2. Setting up your development environment

#### a) Recommended: Codespaces

If your organization has [Codespaces](https://github.com/features/codespaces) enabled (requires Enterprise GitHub & Azure subscription), you are now ready to begin development. Just launch the repository in a codespace, and a dev container is automatically set up!

#### b) Can't use Codespaces: Local installation with Docker

You can build a development environment locally with docker.
The recommended way is to use VSC in a container development mode ([link to instructions](https://code.visualstudio.com/docs/remote/containers)).

#### c) Can't use Docker: Local manual installation

You can also do your development 'the good old way':

0. Create an SSH key and add it to your github profile ([instructions](https://docs.github.com/en/authentication/connecting-to-github-with-ssh))
1. Configure your git user name and email adress if you haven't done it already: `git config --global user.name "Firstname Lastname" && git config --global user.email "your@email.com"`
2. Clone your new repository: `git clone git@github.com:[repository_owner]/[your_repository]`.
3. Go inside the repository folder: `cd [your_repository]`
4. Create and activate virtual environment of your choice. Remember to define the Python version to 3.8! (Instructions: [conda](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html), [venv](https://packaging.python.org/en/latest/guides/installing-using-pip-and-virtual-environments/))
5. Install requirements: `pip-sync requirements.txt`
6. Create an ipython kernel for running the notebooks: `python -m ipykernel install --user --name python38myenv`

#### d) Installing to an offline device

Sometimes you have to work in an environment that can not be connected to the internet, for example for privacy or cybersecurity reasons. In this case, first install the template and all packages that you assume you will require to an environment with internet, and build the docker image as in 2c). Then, save the docker image and transfer it to your offline environment following [these instructions](https://stackoverflow.com/questions/48125169/how-run-docker-images-without-connect-to-internet/48125632#48125632).

### 3. Initializing your project

Few last tweaks before you are good to go:

1. Edit `LICENCE`, `Makefile`, `settings.ini`, `docs/_config.yml` and `docs/_data/topnav.yml` according to your project details. Don't worry - you can continue editing them in the future.
2. Remove the folder `ml_project_template` with the command `git rm -r ml_project_template`. A new folder with the name of your repository will be created automatically when calling `nbdev_build_lib`.
3. Recreate the python module: `nbdev_build_lib`. In the future, repeat this step every time you move between notebooks to ensure your python modules are up to date.
4. Recreate the html doc pages & README: `nbdev_build_docs`. In the future, repeat this step every time you push code to ensure your documentation is up to date.
5. Make initial commit: `git add . && git commit -m "initialized repository from City-of-Helsinki/ml_project_template"`
6. Push changes `git push -u origin master`

You are now ready to begin your ML project development! Remember to track your changes with git!


## How to use

1. Install this template as basis of your new project (see above).

2. If you are not working inside a container, remember to activate your virtual environment every time you begin work: `conda activate [environment name]` with anaconda or `source [environment name]/bin/activate` with virtualenv.

3. Develop your ML solution! (Follow the notebooks!)

4. Save your notebooks and call `nbdev_build_lib` to build python modules of your notebooks - needed if you want to share code between notebooks or create a modules.
This will export all notebook cells with `# export` tag to corresponding .py files under the module (the folder inside your repository named after your repository).
Do this every time you make changes to any exportable parts of the code.

5. Save your notebooks and call `nbdev_build_docs` to create doc pages based on your notebooks (see below).
This will convert the notebooks into HTML files under `docs/` and update README based on the `index.ipynb`.
If you want to host your project pages on GitHub (like [the doc pages of this template](https://city-of-helsinki.github.io/ml_project_template/)), you will have to make your project public and enable github pages in repo > Settings > Pages : set Source to `docs/`.
Alternatively you can build the pages locally with jekyll.


## Installing & updating project libraries

Python has a rich and wide ecosystem of libraries to help with machine learning tasks among other things.
Pandas, Matplotlib, Scipy, PyTorch to name a few.
If base libraries in this template aren't sufficient you can add more with `pip install library`.
However, `pip` command installs libraries into your local Python environment. 
To achieve consistent reproducibility we need to gather information about requirements into project repository. 
New libraries are added to **`project.in`** file. When you change this file remember to run:

```bash
pip-compile --generate-hashes --allow-unsafe -o requirements.txt base-requirements.in requirements.in project.in
pip-compile --generate-hashes --allow-unsafe -o min-requirements.txt base-requirements.in project.in
```

These update full requirements for development environments and lighter, more focused requirements for server usage.

After requirements are updated you should run:

```bash
pip-sync requirements.txt
```

This way libraries you and other users will have the same Python environment.
{% include note.html content='run `./update_install_dev_reqs.sh` for short - it contains the three above pip commands for updating and installing the requirements!' %}
Warning: if you don't update package names and versions next time you or anybody else tries to use this project in another environment its code might not work. Worse, it might *seem to* work, but does so incorrectly.


## Ethical aspects

Please involve ethical consideration in the documentation ML application!

For example:
* Can you recognize ethical issues with your ML project?
* Is there a risk for bias, discrimination, violation of privacy or conflict with the local or global laws?
* Could your results or algorithms be misused for malicious acts?
* Can data or model updates include bias in your model?
* How have you tackled these issues in your implementation?
* You most certainly make ethical choises in your code. Do you document & highlight them?
* If you build an actual application, how can contribute if they notice an unresolved ethical issue?

## How to cite (optional)

If you are doing a research project, you can add bibtex and other citation templates here.
You can also get a doi for your code by adding it to a code archive,
so your code can be cited directly! Most archives also provide repository badges.

To cite this work, use:

    @misc{sten2022helsinki,
    title = {Helsinki Machine Learning Project Template},
    author = {Nuutti A Sten and Jussi Arpalahti},
    year = {2022},
    howpublished = {City of Helsinki. Available at: \url{https://github.com/City-of-Helsinki/ml_project_template}}
    }

## Contributing

See [CONTRIBUTING.md](https://github.com/City-of-Helsinki/ml_project_template/blob/master/CONTRIBUTING.md) on how to contribute to the development of this template.


## Copyright

Copyright 2022 City-of-Helsinki. Licensed under the Apache License, Version 2.0 (the "License");
you may not use this project's files except in compliance with the License.
A copy of the License is provided in the LICENSE file in this repository.

The Helsinki logo is a registered trademark, and may only be used by the city of Helsinki.
{% include note.html content='If you are using this template for other than city of Helsinki projects, remove the files `favicon.ico` and `company_logo.png` from `docs/assets/images/`.' %}
    # to remove remove helsinki logo and favicon:
    git rm docs/assets/images/favicon.ico docs/assets/images/company_logo.png
    git commit -m "removed Helsinki logo and favicon"

This template was built using [nbdev](https://nbdev.fast.ai/) on top of the fast.ai [nbdev_template](https://github.com/fastai/nbdev_template).
