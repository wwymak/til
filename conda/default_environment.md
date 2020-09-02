# Creating an environment with 'default' packages
If you installed miniconda, and found yourself needing an environment where all the packages that comes with the full anaconda installation are installed, a simple way of going about it is :

`conda create -n env_full python=x.x`

(obviously, this is not recommended if you need fixed library versions)
