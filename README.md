# NVIDIA AI Workbench: Introduction
This is an [NVIDIA AI Workbench](https://developer.nvidia.com/blog/develop-and-deploy-scalable-generative-ai-models-seamlessly-with-nvidia-ai-workbench/) example Project that provides a short introduction of the cuDF library, a Python GPU-accelerated DataFrame library (built on the Apache Arrow columnar memory format) for loading, joining, aggregating, filtering, and otherwise manipulating data. cuDF also provides a pandas-like API that will be familiar to data engineers & data scientists, so they can use it to easily accelerate their workflows without going into the details of CUDA programming. Users in the [AI Workbench Early Access Program](https://developer.nvidia.com/ai-workbench-early-access) can get up and running with this Project in minutes.

## Project Description
Included in this project are four tutorial notebooks. The first three are relatively easy to run; the fourth (*) may require a laptop user to push the project to heavier hardware to run all of the performance benchmarks. Good news: Workbench makes this easy!  

* ```10min.ipynb```: This is a short introduction to cuDF and Dask-cuDF, geared mainly towards new users.

   _cuDF_ is a Python GPU DataFrame library (built on the Apache Arrow columnar memory format) for loading, joining, aggregating, filtering, and otherwise manipulating tabular data using a DataFrame style API in the style of pandas.

   _Dask_ is a flexible library for parallel computing in Python that makes scaling out your workflow smooth and simple. On the CPU, Dask uses Pandas to execute operations in parallel on DataFrame partitions.

   _Dask-cuDF_ extends Dask where necessary to allow its DataFrame partitions to be processed using cuDF GPU DataFrames instead of Pandas DataFrames. For instance, when you call dask_cudf.read_csv(...), your cluster’s GPUs do the work of parsing the CSV file(s) by calling cudf.read_csv().

   Which libraries do I use? If your workflow is fast enough on a single GPU or your data comfortably fits in memory on a single GPU, you would want to use cuDF. If you want to distribute your workflow across multiple GPUs, have more data than you can fit in memory on a single GPU, or want to analyze data spread across many files at once, you would want to use Dask-cuDF. 
  
* ```cupy-interop.ipynb```: This notebook provides introductory examples of how you can use cuDF and CuPy together to take advantage of CuPy array functionality (such as advanced linear algebra operations). 
  
* ```missing-data.ipynb```: In this section, we will discuss missing (also referred to as NA) values in cudf. cudf supports having missing values in all dtypes. These missing values are represented by <NA>. These values are also referenced as “null values”.
  
* ```performance-comparisons.ipynb*```: This notebook compares the performance of cuDF and pandas. The comparisons performed are on identical data sizes. This notebook primarily showcases the factor of speedups users can have when the similar pandas APIs are run on GPUs using cudf. This notebook is written to measure performance on NVIDIA GPUs with _large_ memory. Performance results may vary by data size, as well as the CPU and GPU used.

---
**Important Considerations:**
* The notebook titled ```performance-comparisons.ipynb``` may take a long time to execute on laptop and/or workstation hardware. This is because we are running benchmarks and conducting dataframe operations on massive datasets using both Pandas and cuDF. Feel free to adjust the ```num_rows``` variable as needed. 

* If working locally on a laptop or workstation, also consider pushing this project to heavier hardware (original notebook authors used 2x H100 GPUs) to run this notebook. Good news: NVIDIA AI Workbench makes this push easy! 

---

## System Requirements:
* Operating System: Ubuntu 22.04
* CPU requirements: None, tested with Intel&reg; Xeon&reg; Gold 6240R CPU @ 2.40GHz
* GPU requirements: Any NVIDIA training GPU, tested with NVIDIA A100-40GB
* NVIDIA driver requirements: Latest driver version
* Storage requirements: 40GB

# Quickstart
The notebook(s) in this project were adapted from the RAPIDS cuDF Github repository, which can be found [here](https://github.com/rapidsai/cudf/tree/branch-23.12/notebooks).

If you have NVIDIA AI Workbench already installed, you can use this Project in AI Workbench on your choice of machine by:
1. Forking this Project to your own GitHub namespace and copying the clone link

   ```https://github.com/[your_namespace]/<project_name>.git```
   
2. Opening a shell and activating the Context you want to clone into by

   ```
   $ nvwb list contexts
   
   $ nvwb activate <desired_context>
   ```
   
3. Cloning this Project onto your desired machine by running

   ```
   $ nvwb clone project <your_project_url>
   ```
   
4. Opening the Project by

   ```
   $ nvwb list projects
   
   $ nvwb open <project_name>
   ```
   
5. Starting JupyterLab by

   ```
   $ nvwb start jupyterlab
   ```

6. Navigate to the code directory of the project. Then, open the notebooks provided and begin working through them at your own pace. Happy coding!

---
**Tip:** Use ```nvwb help``` to see a full list of commands. 

---

## Tested On
This notebook has been tested with an NVIDIA A100-40gb GPU and an Intel(R) Xeon(R) Gold 6240R CPU (2.40GHz) on the following version of NVIDIA AI Workbench: ```nvwb 0.2.66 (internal; linux; amd64; go1.18.10; Tue Sep 12 18:50:21 UTC 2023)```

## License
This NVIDIA AI Workbench example project is under the [Apache 2.0 License](https://github.com/NVIDIA/rapids-cudf/blob/main/LICENSE.txt)
