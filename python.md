# Python Cheat Sheet

## Python Testing

`pytest` - Run all tests in the current directory

`pytest -k test_name` - Run a specific test

`pytest -v` - Verbose output

`pytest testing/` - Run all tests in a specific directory

`pytest test_module.py` - Run all tests in a specific file

https://docs.pytest.org/en/7.1.x/how-to/usage.html

## Python Environments

`pyenv install -l`

`pyenv install 3.x.x`

`pyenv versions`

`pyenv local 3.x.x`

`pyenv global 3.x.x`

`echo 'eval "$(pyenv init -)"' >> ~/.bash_profile`

## Virtual Environments

`python -m venv /path/to/new/virtual/environment` - Setup a new virtual environment

`python3 -m venv .venv` - Setup a new virtual environmnent in the .venv subfolder

`source .venv/bin/activate` - Activates the virtual environment in the .venv subfolder

`python -m pip install pandas` - Installs pandas in the virtual environment

`python -m pip install --upgrade pip` - Upgrades pip in the virtual environment

## Conda

`conda env create -f conda-environment.yml` - Create a new conda environment from a file

`conda info --envs` - List all conda environments

`conda env list` - List all conda environments

`conda activate` - Activates the base environment

`conda activate myenv` - Activate a conda environment

`conda list` - Lists packages in conda environment

`conda install --name myenv matplotlib` - Installs matplotlib into the conda environment

https://conda.io/projects/conda/en/latest/user-guide/getting-started.html

https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html

https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html

## Poetry

`poetry env use 3.12` - Uses python 3.12 in the current poetry environment

`poetry config list` - Prints the current poetry configuration

`poetry config virtualenvs.path` - Prints the current poetry configuration of the virtualenvs.path setting

`poetry config virtualenvs.path /path/to/cache/directory/virtualenvs` - Updates the virtualenvs.path poetry configuration setting

`poetry config virtualenvs.create false --local` - Uses a local poetry configuration which skips a dedicated virtual environment

https://python-poetry.org/docs/configuration/

## Pip Package Management

`pip install jupyter` - Installs the jupyter package 

## PipX Package Management

`pipx install jupyter` - Installs the jupyter package globally

## Jupyter

`jupyter-lab` - Runs jupyter lab

`jupyter notebook` - Runs jupyter notebook

`jupyter console --kernel myenv`- Runs console with a specific kernel

`jupyter kernelspec list` - Sees available kernels

https://jupyter.org/install

https://docs.jupyter.org/en/stable/projects/kernels.html

https://ipython.readthedocs.io/en/latest/install/kernel_install.html

https://code.visualstudio.com/docs/datascience/jupyter-kernel-management

https://github.com/microsoft/vscode-jupyter/wiki/Kernels-(Architecture)
