# ooi-workflow

Opening project (working for mac and windows):

1. conda env create -f environment.yml
2. conda activate echopype
3. conda run -n echopype jupyter notebook

If you've updated the environment file by modifying dependencies, please run:

1. conda env update -n echopype -f environment.yml

Currently using Dask for optimization and parallel processing.