# CT_tools
collection of scripts for processing and working with CT data

Described in order of addition

### CT_extract-settings.py, or CT metadata extraction.

#### This script now lives in the Morphosource Batch Convert project folder and has been renamed user_extract_CT.py  
A python script designed to extract and organize metadata for a scan. It is designed to work with pca files that are produced by GE Phoenix line CT scanners, with xtekct files that are produced by Nikon CT scanners, and log files that are produced by SkyScan scanners. 

If you want to extract CT scan metadata without running the entire morphosource batch convert script, you will need two files in the Morphosource Batch Convert folder: `user_extract_CT.py` and `ct_metadata.py`. To use:

1. Open `user_extract_CT.py` in a text editor and change the variables in ALL CAPS to the correct settings for your job.
2. Open a terminal window on a machine with Python installed (for more on installing Python, see guide [here](https://realpython.com/installing-python/) or, if on Windows, consider the [Anaconda distribution](https://docs.anaconda.com/anaconda/install/windows)).
3. Navigate to the location of the code by typing `cd C:\Path\to\morphosource_batch_convert`
4. Type `python user_extract_CT.py`

**Input:** The script takes a small amount of user input (you will have to specify the file path of your choice, then you will have to specify the name of the output table), and either (a) a single pca file, or (b) the location of a folder that contains multiple pca files. If drawing metadata from multiple files, those pca files can be nested in various subfolders within the folder you specify. The idea is that you don't have to change your file structure in order to extract data from multiple scans. 

**Output:** The script will write a .csv file of a set of settings commonly used in processing scans or in sharing scan data. If some parameters of interest to you are not included in the output, please contact me and I'll see what I can do. 

### make_file_set.py

A python script to make a bunch of empty folders with the same name as entries in a list in a column. Useful when, for example, you need to make a folder for every single specimen in a long list and don't want to copy and paste all of those names one by one into new folder names. 

**Input:** a csv file with column names. You'll specify the file path, you will have to choose from a list of column names generated by the csv file, and you will specify an output path where you want all of these new folders to be created. 

**Output:** one folder per unique entry in your column of choice.

### zipallname.py

A python script to zip up folders full of tiff images (likely from a bunch of CT scans). 

The script calls the 'zipfile' package in the Python Standard Library (https://docs.python.org/2/library/zipfile.html),which can handle ZIP64 extension (the thing that lets you zip files >4gb), and thus should satisfy the concerns raised by the Morphosource best practice guidelines (see https://www.researchgate.net/publication/316669746_Morphosource_Archiving_and_sharing_3-d_digital_specimen_data). 

### morphosource_batch_convert

A collection of python scripts that streamlines the batch uploading process in Morphosource.
An updated versin of the CT_extract-settings.py script now lives in this folder!