---
title: "Installing python"
short_title: "Prelude: installing python"
---

## Installing the miniforge python distribution

There are a number of ways to install python locally on your computer. We recommend using the [miniforge distribution](https://conda-forge.org/download/).

Head to the linked page and download the installer suitable for your OS. Once the installer is downloaded, follow the installation instruction and install the miniforge distribution. Once miniforge is installed, start a terminal (command prompt in Windows, Terminal in MacOS, etc.) with the base mamba environment activated (in Windows there is a separate icon for that, in Mac your Terminal should be configured to activate the base environment automatically). A mamba enabled terminal with the base environment activated should have a prompt that started with the text `(base)`.

![A mamba enabled terminal](img/mamba_base.png)

**Figure**: A mamba enabled terminal.

## Installing third-party packages

The base environment has a very limited number of third-party modules installed. So our next step is to install the third-party packages that are common used in scientific computing (numpy, scipy, pandas, matplotlib, etc.). While we can install these packages in the base environment, we recommend doing so in a new environment. In this appendix we'll call this new environment "osym", but you should feel free to change that name in the subsequent code.

The easiest way to create a new environment with the desired packages installed is to use a requirements.txt file. You can find an example of the requirements.txt file [here](data/requirements.txt).

Download the requirements.txt file to your local computer, then, change directory to the location of the requirements file, and execute the following command:

```
    mamba create -n osym --file requirements.txt
```

(change the name `osym` to whatever way you want to name your environment)

Once the above command is entered, mamba should get to work and figure out what packages you need to install (some of the modules included in requirement.txt have prerequisites that are not listed, and mamba will take care of installing those too). Confirm that the installation plan is correct, and mamba will create the environment and install the packages in it.

Once mamba is finished, follow the instruction it provides to activate the `osym` environment, namely:

```
    mamba activate osym
```

When the `osym` environment is activated, the prompt of the terminal should start with the text `(osym)`.

![A terminal with the "learn" environment activated](img/mamba_activate.png)

**Figure**: A terminal with the "learn" environment activated.

## Starting JupyterLab

Instead of JupyterHub, in a local installation you will view your Jupyter notebooks using JupyterLab. To view your notebook in JupyterLab, first open a mamba-enabled terminal, then activate the `learn` environment (via `mamba activate learn`) and change directory (via `cd`) to the folder containing your notebook in the terminal. Next, in the same terminal, run:

```
    jupyter lab
```

Your browser should automatically open with a JupyterLab page (which has similar interface as the JupyterHub page) that shows your notebook. You can now work on the notebook like you did with JupyterHub.

## Note: installing additional packages

Occasionally, you may find the need to install additional third-party packages. As a concrete example, let's suppose I need the [PyMC](https://www.pymc.io/welcome.html) package to perform Markov chain Monte Carlo.

To install `pymc`, open a mamba-enabled terminal and activate the environment for which you want to add the new package. Now, if your package is available on conda-forge (which you can check via [this page](https://conda-forge.org/packages/)), it is preferable to use `mamba` to install the package. Using our example, it turns out that `pymc` is available on conda-forge, so to install I will need to execute:

```
    mamba install pymc
```

Mamba will then figure out what packages need to be installed, and once you confirm the changes the package will be installed to your environment and available for all future use.

If your package is not available on conda-forge it is likely distributed via pypi. Such packages can be installed using `pip`. For example, if I want to install PyMC via `pip`, I will have to run:

```
pip install -U pymc
```

(Note that if your package is available on conda-forge and you've already run the `mamba install` line then you **do not** need to perform `pip install`. In any case, only one of the two lines are needed).

As with `mamba install`, the new package is now permanently a part of your python environment and you all you need to do to use it in a notebook is to import the package.

To install and use other packages, just replace `pymc` in the above lines with the name of the package you need.