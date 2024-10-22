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

## Conda

`conda env create -f conda-environment.yml` - Create a new conda environment from a file

`conda info --envs` - List all conda environments

`conda env list` - List all conda environments

`conda activate` - Activates the base environment

`conda activate myenv` - Activate a conda environment

`conda install --name myenv matplotlib` - Installs matplotlib into the conda environment

https://conda.io/projects/conda/en/latest/user-guide/getting-started.html

https://docs.conda.io/projects/conda/en/latest/user-guide/cheatsheet.html

## Pip Package Management

`pip install jupyter` - Installs the jupyter package 

## PipX Package Management

`pipx install jupyter` - Installs the jupyter package globally

## Jupyter

`jupyter-lab` - Runs jupyter lab

`jupyter notebook` - Runs jupyter notebook

https://jupyter.org/install
