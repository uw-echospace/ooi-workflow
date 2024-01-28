# ooi-workflow

Please perform the following steps in the order mentioned to get the project running (for both Mac and Windows):
1. If you are running this project/code for the first time, please clone this repository and open command prompt (for Mac) and anaconda command prompt (for Windows)
If you have previously ran the code, and want to update the environment, with the modified dependencies, please run: ```conda env update -n echopype -f environment.yml```
2. Next, run the following command to get the required environment setup on your system: ```conda env create -f environment.yml```
3. Next, activate the environment, by running the following command: ```conda activate echopype```
4. Inside the activated environment, check if Jupyter is installed in the environment by running the following command:
```conda list jupyter```
If nothing or an error shows up, it means that Jupyter is not installed. Please install jupyter by executing the following command before proceeding ahead:
```conda install -c conda-forge jupyter```. 
If the Jupyter versions show up upon running the command, it means that Jupyter is already installed in the environment, and you may choose to skip this step.
4. Finally, start the program, by executing the following: ```conda run -n echopype jupyter notebook```

**Notes**:
- Currently using Dask for optimization and parallel processing.