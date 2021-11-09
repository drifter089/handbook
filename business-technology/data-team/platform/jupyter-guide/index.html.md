---
layout: handbook-page-toc
title: "Jupyter Guide"
description: "Guidance on interacting with SnowFlake internally using JupyterLab"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .toc-list-icons .hidden-md .hidden-lg}

---
See related [repository](https://gitlab.com/gitlab-data/data-science)

### Features

- Common python DS/ML libraries (pandas, scikit-learn, sci-py, etc.)
- Natively connected to Snowflake using your dbt credentials. No login required!
- Git functionality: push and pull to Gitlab repos natively within JupyterLab ([requires ssh credentials](https://docs.gitlab.com/ee/ssh/index.html))
- Run any python file or notebook on your computer or in a Gitlab repo; the files do not have to be in the docker container
- Need a feature you use but don't see? Let us know on [#bt-data-science](https://gitlab.slack.com/archives/C027285JQ4E) and we can add it!

### Getting Started

You have two options when setting up jupyter via the data-science project. Choose from one of the following:
- **Full install (Recommended)**: Installs all libraries defined by the [Pipfile](https://gitlab.com/gitlab-data/data-science/-/blob/main/Pipfile), **_plus_** a complete anaconda install.
- **Lightweight install**: installs **_only_** the libraries defined by the [Pipfile](https://gitlab.com/gitlab-data/data-science/-/blob/main/Pipfile) and should be used if you already have a python environment on your local machine that you would like to use as the base image.

### Installation Instructions

1. Clone the repo to your local machine `git clone git@gitlab.com:gitlab-data/data-science.git`
2. Run `cd data-science`
3. Based on which version you would like to install, run one of the following:
    - **_For full install_**: run `make setup-jupyter-local`
    - **_For lightweight install_**: run `make setup-jupyter-local-no-conda` 
4. Run `make jupyter-local`
5. Jupyter should launch automatically. If it does not: 
   1. First make sure that Google Chrome is your default browser (go to "System Preferences", click "General" and choose Google Chrome from dropdown menu in section "Default web browser"). 
   2. Then, in Chrome, copy paste the url and token found in terminal once the docker image creates. It should look something like `http://127.0.0.1:8888/lab?token=5c7f7da79f4a0968501f087f3c79ee4dd8bd7a63e0f088a8`. The token will change each time you spin up the docker container.

#### Validation of installation

Before you proceed further, validate if your Python and pip (package installer for Python) are in correct paths. If these are not in correct locations you may not be able to work with the most up to date packages.

To check if everything is correct open terminal and run command 

``which python`` 

It lists location of your default Python. It should be in ``/Users/your_user_name/anaconda3/bin``

And command 

``which pip``

It lists location of your default pip. It should be in ``/Users/your_user_name/anaconda3/bin/pip``

#### Connecting to Snowflake

1. Make sure you have setup a `{User}/.dbt/profiles.yml` file which **does not** include your password. You can use the example provide [here](https://gitlab.com/gitlab-data/analytics/-/blob/master/admin/sample_profiles.yml) as reference
1. Run through the [auth_example notebook](https://gitlab.com/gitlab-data/data-science/-/blob/main/templates/auth_example.ipynb) in the repo to confirm that you have configured everything successfully. The first time you run it you will get a browser redirect to authenticate your snowflake credientials via Okta. After that, if you run the notebook again you should be able to query data from Snowflake.  
1. If you get an error then likely Snowflake is not properly configured on your machine. Please refer to the Snowflake and dbt sections of the [Data Onboarding Issue](https://gitlab.com/gitlab-data/analytics/-/blob/master/.gitlab/issue_templates/Data%20Onboarding.md). It is likely that your .dbt/profiles.yml is not setup correctly.


#### Mounting a local directory

By default, the local install will use the data-science folder as the root directory for jupyter. This is not terribly useful when all your code, data, and notebooks are in other locations on your computer. To change, this you will need to create and modify a jupyter notebook config file:
1. Run `jupyter-lab --generate-config`. This creates the file `/Users/{user}/.jupyter/jupyter_lab_config.py`
1. Browse to the file location and open it in an Editor
1. Search for the following line in the file: `#c.ServerApp.root_dir = ''` and replace with `c.ServerApp.root_dir = '/the/path/to/other/folder/'`. If unsure, set the value to your repo directory (i.e. `c.ServerApp.root_dir = '/Users/{user}/repos'`). Make sure you remove the `#` at the beginning of the line.
1. Make sure you use forward slashes in your path. Backslashes could be used if placed in double quotes, even if folder name contains spaces as such as `\yourUserName\Any Folder\More Folders\`
1. Rerun `make jupyter-local` from the data-science directory and your root directory should now be changed to what you specified above. 

#### Increasing Docker Memory Allocation

By default, docker will allocate 2GB of memory to run containers. This is likely not enough RAM to work with jupyter and python, as data is held in-memory. It is recommended you increase the docker memory allocation to avoid out-of-memory errors.
1. Open Docker dashboard.
1. Click on the gear icon in the upper right to show settings.
1. Under "Resources" allocate additional memory to be used by Docker. 8GB is recommended but you may have to increase it futher if working with large datasets.
1. Restart Docker. 

#### Setting Up Jupyter Extensions

- The data-science repo comes with many useful Jupyter Lab extensions pre-installed, including [git](https://github.com/jupyterlab/jupyterlab-git), [variable inspector](https://github.com/lckr/jupyterlab-variableInspector), [collapsible headings](https://github.com/aquirdTurtle/Collapsible_Headings), [execute time](https://github.com/deshaw/jupyterlab-execute-time), and [system monitor](https://github.com/jtpio/jupyterlab-system-monitor). 
- To get the most out of these (and to avoid having to configure them every time you run the container), create the following file: `/Users/{user}/.jupyter/lab/user-settings/@jupyterlab/notebook-extension/tracker.jupyterlab-settings`
- Within that file, paste the following and save: 

```
{
    "codeCellConfig": {
        "codeFolding": true,
        "lineNumbers": true,
    },
    
    "recordTiming": true,
    
}
```

### Interesting libraries included

#### Data/Model Analysis

* [ELI5](https://eli5.readthedocs.io/en/latest/overview.html#installation)
* [QuickDA](https://pypi.org/project/quickda/)
  
#### Visualisation tools: 

* [Plotly](https://plotly.com/python/)
* [Seaborn](https://seaborn.pydata.org/)

#### ML libraries

* [SKlearn](https://scikit-learn.org/stable/index.html)
* [Tensorflow](https://www.tensorflow.org/api_docs/python/tf)
* [Torch](https://pytorch.org/)
* [Py-earth](https://contrib.scikit-learn.org/py-earth/content.html) (linear and logistic regression) 
* [Prophet](https://facebook.github.io/prophet/docs/quick_start.html#python-api) (time series)
* [Autots](https://pypi.org/project/AutoTS/) (time series)
* [XGBoost](https://xgboost.readthedocs.io/en/latest/python/python_intro.html) (powerful black-box method) 

#### Easy concurrency

* [Modin](https://modin.readthedocs.io/en/latest/#)
* [Dask](https://dask.org/) (must be self-installed)

#### GPU speedup

* [PlainML](https://github.com/plaidml/plaidml)
