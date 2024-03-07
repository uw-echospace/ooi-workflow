

# Cloud-Based Ocean Sonar Data Processing and Visualization
Echosounders, which are vital for studying marine life, generate massive amounts of data that go unused due to a lack of adequate processing and visualization tools. Our project expands on the Echopype ecosystem, using Echopype for data processing, Echoshader for visualization, and Echoflow for workflow orchestration. We use cloud computing resources to efficiently manage massive datasets.

## Table of Content
- [Cloud-Based Ocean Sonar Data Processing and Visualization](#cloud-based-ocean-sonar-data-processing-and-visualization)
  * [Overview](#overview)
  * [Open-source tools and libraries](#open-source-tools-and-libraries)
    + [Echopype](#echopype)
      - [Key Features](#key-features)
  * [Performance Improvement](#performance-improvement)
  * [Problems We Faced](#problems-we-faced)
  * [Installation Steps](#installation-steps)

## Overview
This project intends to create a streamlined cloud-based workflow for processing and visualizing ocean sonar data. We use existing open-source tools and libraries (Echopype and Echoshrader) to turn raw sonar data into analysis-ready datasets and provide an interactive visualization.


## Open-source tools and libraries 
### Echopype
Echopype is a software suite designed to improve interoperability and scalability in ocean sonar data processing. These data are commonly used to learn about the distribution and abundance of marine species such as fish and krill. Echopype's collection of vast volumes of sonar data from a variety of maritime sites has increased dramatically during the previous decade. However, the majority of the new data is still underutilized.

Echopype intends to solve the core cause of this problem - a lack of interoperable data formats and scalable analytic workflows that can adapt to increasing data volume - by providing open-source tools that scientists may use to make discoveries with this new data.

#### Key Features
- Interoperable data format support for various sonar manufacturers.
- Scalable analysis workflows suitable for processing large volumes of sonar data.
- Integration with other open-source tools for comprehensive data analysis and visualization.

Echopype GitHub Repo [https://github.com/OSOceanAcoustics/echopype]
Echopype Documentation [https://echopype.readthedocs.io/en/stable/]

## Performance Improvement
To improve processing efficiency, we ran performance tests on our system, which was equipped with a "2.5 GHz Dual-Core Intel Core i7" processor and "16 GB 2133 MHz LPDDR3" RAM. Initially, without parallel processing, we could only handle 16 files at once, which took about 3 hours.

Dask parallel processing was created in order to alleviate this issue. The optimization produced notable gains in efficiency. We processed more than 300 files at once with Dask, finishing the job in an hour. This substantial improvement shows how to use parallel processing techniques to increase computing efficiency.

## Problems We Faced
1. Time-Taking Process
We experienced considerable difficulties throughout the raw data translation procedure, which required significant time and processing resources. Converting raw files to processed files proved time-consuming. To overcome this issue, we implemented Dask parallel processing, which is described in the 'Performance Improvement' section.

2. Lack of Data Consistency
Data consistency became a serious challenge as a result of the many data collection sources and frequent sensor changes. While there was considerable consistency in data between 2016 and 2019, with sensor upgrades occurring twice a year, data consistency deteriorated significantly after 2019. We had difficulty merging Echopype data due to irregularities in sensor channels. In addition, modifications to the raw data format occurred after 2019, complicating the data integration procedure.

3. Scaling Challenges
Scaling the program proved problematic, especially given Dask's compatibility limitations across several operating systems. Dask ran smoothly on macOS, but it had compatibility concerns on Windows and Ubuntu. To address these issues, we designed batch processing and created recursive functions for easier data combining and processing.

4. Conda Environment Creation and Update Issues
We encountered difficulties with generating and updating Conda environments, mainly due to the length of time it required to accomplish these tasks. The construction and update of Conda environments proved time-consuming, reducing the productivity of our development approach. This issue adds complexity to our project management and development duties, necessitating more time and resources to resolve.


## Installation Steps

Please perform the following steps in the order mentioned to get the project running (for both Mac and Windows):
1. If you are running this project/code for the first time, please clone this repository and open command prompt (for Mac) and anaconda command prompt (for Windows)
If you have previously ran the code, and want to update the environment, with the modified dependencies, please run: ```conda env update -n echopype -f environment.yml```.
Otherwise, run the following command to get the required environment setup on your system: ```conda env create -f environment.yml```
2. Next, activate the environment, by running the following command: ```conda activate echopype```
3. Inside the activated environment, check if Jupyter is installed in the environment by running the following command:
```conda list jupyter```
If nothing or an error shows up, it means that Jupyter is not installed. Please install jupyter by executing the following command before proceeding ahead:
```conda install -c conda-forge jupyter```. 
If the Jupyter versions show up upon running the command, it means that Jupyter is already installed in the environment, and you may choose to skip this step.
4. Finally, start the program, by executing the following: ```conda run -n echopype jupyter notebook```

**Notes**:
- Currently using Dask for optimization and parallel processing.
- Figuring out the threshold of the number of files that can be processed locally post optimization and parallel processing
- Working on migration to JetStream by acquiring machine to improve scalability
