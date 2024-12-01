# yelpdata
Data project using Hadoop and Pyspark
completed for DSE 230 at UC San Diego, 2024


###PROJECT TITLE:
Unlocking Business Potential: Leveraging Clustering for Actionable Insights from Yelp Data


##OVERVIEW: 
In this project we will be gaining insights on the Yelp Dataset. We will be going through the following phases: EDA, Prepare Data, Clustering, and Analysis to find out what businesses with good Yelp ratings have in common. Each phase will have its own Jupyter notebook.


##INSTALLATION:
Before starting the project you must have the following Python packages installed:

- pandas
- numpy
- matplotlib
- pyspark
- json
- PIL
- geopandas 
- gdal

For installing Geopandas on Docker, take the following steps while Docker is running. Start in Terminal (locally, outside the Docker container):
	1. Use the following command to list all running Docker containers

	docker ps

	2. Look for your container in the list under NAMES column.
	3. Now, you can use this name to access the container. 

	docker exec -it <my-container-name> /bin/bash

	4. Inside the container, install the necessary system dependencies for geopandas.

	apt-get update && apt-get install -y \
	gdal-bin \
	libgdal-dev \
	libgeos-dev \
	libproj-dev

	5. Once the system dependencies are installed, you can install geopandas using pip on Treminal inside the container.

	pip install geopandas

	6. Then run the following cell in python to verify the installation.

	import geopandas as gpd
	print(gpd.__version__)

A requirements.txt file is included which can be utilized to install system requirements outside a Docker environment


##DATA SOURCES & FILES:
Download all required data files and store in local folder.

Download Yelp data (main source) using the following link:

https://www.yelp.com/dataset/download

The Yelp dataset contains information about businesses, user reviews, and interactions on the Yelp platform. It includes multiple files such as `business.json`, `review.json`, and `user.json`. We will use business and review in this project.

	Download the following:
	yelp_academic_dataset_business.json
	yelp_academic_dataset_review.json

Supplemental data can be downloaded using the two links below:

https://www.serviceobjects.com/blog/free-zip-code-and-postal-code-database-with-geocoordinates/

	Download the following:
	USZIPCodes202403.csv (if downloaded more recently, change to this filename in local folder)
	CanadianPostalCodes202403.csv (as above, update filename if needed)

https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.html

	Download cb_2018_us_state_500k.zip, unzip in local folder 
	local folder will now contain a folder called “cb_2018_us_state_500k” with 7 files inside it that all start with “cb_2018_us_state_500k”

The supplemental data will be used to help correctly identify and map the latitude and longitude of businesses by using their given zip codes

Copies of data files can also be found in this Google Drive Folder:
https://drive.google.com/drive/folders/18uvcAZUd4xN8FQJJ_QcAjVAANQZ07ZVn?usp=drive_link

## NOTEBOOKS:
Make sure you have downloaded the given notebooks in the same local folder as the data files, and run them from that folder, in numerical sequence:
1-EDA.ipynb
2-Prepare.ipynb
3-Clustering.ipynb
4-Analysis.ipynb

1-EDA: 
Explores the Yelp Dataset Business and review files. This notebook will output display tables, charts, graphs and a US map of locations.

2-PREPARE:
Consolidates and formats business data into a usable dataframe of normalized features.
This notebook will output two csv files that will be saved in new local folders.

Notebooks are saved with open restaurants as the default filtering option. To select a different subset of businesses, update cell #7 under "UPDATE HERE:" before running notebook.

After notebook runs, find the new file named “part-00000-...” in folder named “Features_CSV_Folder”. Rename the “part-...” file as “Features.csv” and move it into local folder. Similarly, find the new file named “part-00000-...” in folder named “Data_CSV_Folder”. Rename the “part-...” file as “Data.csv” and move it into local folder. Then proceed to next notebook.

3-CLUSTERING:
Uses normalized features to identify candidate clusters for analysis.
Notebook will output one csv file that will be saved in new local folder.

After notebook runs, find the new file named “part-00000-...” in folder named “Clusters_CSV_Folder.csv”. Rename the “part-...” file as “Top_Clusters.csv” and move it into local folder. Then proceed to next notebook.

4-ANALYSIS:
Compares Clusters and digs into individual cluster details. Notebook will output display tables to help create recommendations for businesses on Yelp. 


## DOCUMENTATION

Documentation.pdf - this document is provided with step-by-step examples of how to use the notebooks to analyze a different subset of businesses. It includes screenshots - examples of Python code cells where updates are needed, notebook outputs, and folder contents.

## CSV FILES

The folder output_csv_files contains csv output files from restaurant analysis. Csv files can be used to replicate notebook results if needed.

## REFERENCES

This k-means clustering methodology was inspired by:
Misztal-Radecka & Indurkhya, “Bias-Aware Hierarchical Clustering for detecting the discriminated groups of users in recommendation systems” 2021
The paper can by viewed at:
https://ruj.uj.edu.pl/server/api/core/bitstreams/d375518b-cc10-49b2-95fc-3b1a4ab87e0f/content


## SUPPORT
If you have any questions or feedback, please feel free to contact us at zgaeini@ucsd.edu / hstrickland@ucsd.edu / dah023@ucsd.edu


## AUTHORS & ACKNOWLEDGMENT
Zeinab Gaeini, Harper Strickland, and Debbie Hernandez

