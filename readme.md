# February Grant Deadline Notebook

## Notebook Goals
### Provide a "fill-in-the-blanks" notebook for Nadine to perform the following for data from individual animals:
1. Align the signals from Tucker Davis Technologies Devices (i.e. Photometry measurements + GuPPy z-score) with DeepLabCut data and MoSeq scoring of behavioral events.
2. Average data around a 10s window of behavioral events (movement onset, movement offset, behavioral syllable onset).
3. Plot individual traces.
   Plot averaged traces.

#### How to use this notebook:
- Follow steps & run cells one at a time (run cells by pressing shift+enter, or Triangle button at top).
- For some cells, you will need to enter your own subject information, path, and folder path names, etc. To do so, comment out existing code (with '#' character), uncomment code blocks where you type in your values.
- Run code cells in the sequence of the notebook.
- If an output is confusing or you face errors, try going to the top bar and clicking "Kernel" -> "Restart Kernel and Clear Outputs of all cells" and start over from the top of the notebook.

***

### Step 1: Package Imports

Note: You will need to make sure you have the following installed on your computer, either via pip or conda: <br>
      `h5py`, `matplotlib`, `numpy`, `pandas`, `seaborn`, `tdt`, `scipy`. <br>
Here's how you do that! <br>
I recommend making a virtual environment in Anaconda (for instance, one called "feb_grant_env"). This can be done by opening an Anaconda shell and typing in the following: <br>
1. Create a conda environment: <br> `conda create -n feb_grant_env python=3.10.13` <br> Then activate the environment: <br>
2. `conda activate feb_grant_env` <br> Then download the necessary packages: <br>
3. `conda install h5py matplotlib numpy pandas seaborn tdt scipy`

If you are not using Anaconda, then use a Python virtual environment. You can create this in Powershell using the following: <br>
1. Create a Python venv: <br> `python -m venv feb_grant_env` <br>
2. On Windows: <br> `feb_grant_env\Scripts\activate` <br> On Mac: <br> `source feb_grant_env/bin/activate` <br>
3. `python -m pip install h5py matplotlib numpy pandas seaborn tdt scipy`
<br><br>

Assuming that you were able to follow the above steps, then you are ready to use the notebook.

### Step 2: Define manually measured delay between the TDT system and the video data (i.e. DLC and MoSeq)

***

### Step 3: Define paths for different datasets

- **DLC_path:** Contains movement of animal determined by DeepLabCut in .csv format (1 mouse, 1 session)
- **tdt_path:** Folder that contains the "block" data from the Tucker-Davis Technologies photometry recording in Struct format (1 mouse, 1 session)
- **guppy_path:** Contains the deltaF/F (Z-Score) of the photometry recording as determined by GuPPy protocol in hdf5 format (1 mouse, 1 session)
- **moseq_main_path:** A very large dataset that contains MoSeq data from all animals and all trials in .csv format (all mice, all trials)

### Step 4: Data Imports

***

# Open Field Motion Data 

### Step 5: Calculate Velocity & Acceleration and Align that to TDT device timescale

Measured by DeepLabCut

Notes: 
- Original x, y units are in pixels.
- Convert pixels to meters or centimeters to calculate speed.
- Calculate speed (note need >1 data point to calculate, so start from the second row).
- Convert to the same time axis as photometry data.
- Calculate acceleration (note need >1 velocity data point to calculate, so start from the 3rd row)

*** 

## Step 6: Set movement onset and offset criteria and get the indices/timepoints for all movement onsets and offsets

Note: This still needs refinement, but these criteria should be reasonable for the current grant proposal. <br>
I arrived at these with some trial and error, they produced reasonable results for me.

### Step 7: Clean the DLC DataFrame

***

## Photometry Data: Tucker-Davis Technologies and [GuPPy](https://github.com/LernerLab/GuPPy)

### Step 8: Extract relevant information from tdt device data
### Step 9: Place GuPPy data in the same timescale as TDT

***

## Photometry Data: Tucker-Davis Technologies and [GuPPy](https://github.com/LernerLab/GuPPy)

### Step 8: Extract relevant information from tdt device data
### Step 9: Place GuPPy data in the same timescale as TDT

***

## Step 11: Merge all datasets on the common "time_TDT" column 

#### And clean up the merged DataFrame

#### Perform an "Outer" merge that keeps all data points whether they are in common or not

***

## Step 12: Generate Interpolation Functions for Z-Score and Velocity

Note: `interp1d` function that I use will become deprecated in future versions of SciPy. <br> 
I am currently using version 1.11.4

### Step 13: Generate the time over which you want to sample points and the frequency you want to sample

This tells us a time range and frequency that we want to sample from interpolated points. <br>
That is, in this example, I say that I want every millisecond between 0s and 1870s. <br>
Then I place that into a Pandas Series object for compatibility with existing data.

### Step 14: Place interpolated data into a DataFrame to have it in the same format as raw data

***

# Movement Onset Analysis

## Step 15: Analyze Movement Onset Events & Generate Graphs

***

# Movement Offset

## Step 16: Analyze Movement Offset Events & Generate Graphs

Note: Some variables from onset and offset graph-making and analysis have the same names, so you must run ONSET or OFFSET data, don't try to jump back and forth or you might produce confusing results. I will clean this up in the future.

***

# Behavioral Syllable Onset

## Step 17: Analyze Behavioral Syllable Onset Events & Generate Graphs