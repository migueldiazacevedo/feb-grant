# February Grant Deadline Notebook

## Goals
- Provide a notebook for aligning signals from Tucker Davis Technologies Devices with DeepLabCut data and MoSeq scoring of behavioral events.
- Analyze and average data around 10s windows of behavioral events.
- Plot individual and averaged traces.

## How to Use
- Ensure that you have all requirements & packages installed
- Work through the notebook FebGrantDeadline.ipynb by reading instructions and running cells one at a time 
- change variables to include your own data as needed 
- If facing errors, try restarting the kernel, clearing the outputs, and trying again.
  
## Requirements
- Python 3.10.13 
- Packages: h5py, matplotlib, numpy, pandas, seaborn, tdt, scipy

## Steps
1. Import packages.
2. Define delay between TDT system and video data.
3. Define paths for datasets.
4. Import and align data.
5. Calculate velocity and acceleration.
6. Set movement onset and offset criteria.
7. Clean DLC DataFrame.
8. Extract information from TDT device data.
9. Place GuPPy data in TDT timescale.
10. Merge datasets and clean.
11. Generate interpolation functions.
12. Sample points and frequencies.
13. Analyze movement onset and offset events.
14. Analyze behavioral syllable onset events.


## Notes on Package Imports

You will need to make sure you have the following installed on your computer, either via pip or conda: <br>
      `h5py`, `matplotlib`, `numpy`, `pandas`, `seaborn`, `tdt`, `scipy`. <br>
Here's how you do that! <br>
I recommend making a virtual environment in Anaconda (for instance, one called "feb_grant_env"). This can be done by opening an Anaconda shell and typing in the following: <br>
1. Create a conda environment: <br> `conda create -n feb_grant_env python=3.10.13` <br> Then activate the environment: <br>
2. `conda activate feb_grant_env` <br> Then download the necessary packages: <br>
3. `conda install h5py matplotlib numpy pandas seaborn tdt scipy`
4. if a package is not conda installable then use `pip install package_name` where package_name is the name of the package e.g. tdt

If you are not using Anaconda, then use a Python virtual environment. You can create this in Powershell using the following: <br>
1. Create a Python venv: <br> `python -m venv feb_grant_env` <br>
2. On Windows: <br> `feb_grant_env\Scripts\activate` <br> On Mac: <br> `source feb_grant_env/bin/activate` <br>
3. `python -m pip install h5py matplotlib numpy pandas seaborn tdt scipy`
<br><br>

Assuming that you were able to follow the above steps, then you are ready to use the notebook.