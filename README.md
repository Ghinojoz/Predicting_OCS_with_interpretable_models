# Predicting OCS with interpretable models

## Overview
This project seeks to predicy atmospheric Carbonyl Sulfide using interpretable machine learning models. The work is ongoing (as of 6/3/2022)

 ## Data
 Unfortunately the data is too large to host on Github. However, it can be obtained at the following drive link:
https://drive.google.com/drive/folders/1MaQUnTjBzbX4Gu3s0zsYRx38mYWGp9QH?usp=sharing

The entire folder must be downloaded and placed in the root project directory, i.e. './Data'

## Code
This project contains several .ipynb scripts intended to be run in google colab. A description of what each does can be found below. The code is meant to be run in sequence, that is some scripts described later on in this document depend on earlier scripts being successfully run.

### build_feature_frames.ipynb
This script creates a data frame of the ocean features observed at each discrete region. As such it depends on the Data folder, which can be downloaded above. There is quite a large amount of data to process, so the script can take a few hours to execute. The result will be a data frame which is saved as a .pkl in the './Data/Pickles' directory.

### add_ocs_to_feature_frame.ipynb
Generates a separate dataframe for each of 14 OCS observation sites, which includes the OCS observations for that site, along with the entirety of the ocean features described above. 

### sensitivity.ipynb
Uses the site specific dataframes to examine correlation between OCS and ocean features. Produces a .txt document containing the correlation for each feature relative to the site's OCS observations. The features are sorted by correlation, with the top 10 features representing the site's 'shortlist'

### plot_heatmap.ipynb
Produces heatmap plots of absolute pearson correlation for each feature relative to each OCS observation site.
Note that this script produces a lot of images (over 1GB worth) and should not be run lightly.

### make_gifs.ipynb
Aggregates the heatmaps produced above into gif animations for easier viewing. Note that this script only produces animations for the top 10 features.

### Seesaw_GA2M.ipynb
Trains GA2M to predict carbonyl sulfide at a single site. Changing the cos_site string in cell 3 will change which site it trains and tests on. The list of acceptable sites is as follows: alt, brw, cgo, hfm, kum, lef, mhd, mlo, nwr, psa, smo, spo, sum, thd

These site abbreviations correspond to the OCS observation sites measured by NOAA. More information on these sites can be found here: https://gml.noaa.gov/hats/gases/OCS.html

## OCS DCRNN (directory)
This folder contains the code for training and executing DCRNN. Inside several scripts can be found:

## DCRNN_generate_data_and_matrix.ipynb
Produces the pandas array which 
