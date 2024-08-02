# Water Classification and Quantification

##### A Jupyter notebook to download Sentinel-2 L2A imagery over the AOI and analyze the presence of water.

 

This repository contains a Jupyter notebook with the main objective to classify whether the provided AOIs contain water using satellite optical imagery, and if they do, to quantify the area occupied by water. In the end, a CSV file is to be generated summarizing this analysis.

The optical satellite imagery is obtained from the [Copernicus Data Space Ecosystem](https://dataspace.copernicus.eu) and the tools used for the project are QGIS (to covert the CSV file to GeoJSON) and [Processing API](https://documentation.dataspace.copernicus.eu/APIs/SentinelHub/Process.html) which is part of the suite of APIs provided by the Copernicus Data Space Ecosystem. Using the Green band (B03) and NIR band (B08) of Sentinel-2 L2A, the Normalised Difference Water Index (NDWI) index is used to identify the water pixels, create a binary mask (`waterMask`) over the AOIs, and then calculate the total area covered by water using the `waterMask` and the spatial resolution of each pixel.

### How to run the notebook

The repository includes a `requirements.txt`. Please make sure that the dependencies have been installed by running the following in the terminal.

```console

$pip install -r /path/to/requirements.txt

```

To use the tools of the Copernicus Dataspace Ecosystem, you would also need an account on this platform, which can be created for free [here](https://identity.dataspace.copernicus.eu/auth/realms/CDSE/login-actions/registration?client_id=cdse-public&tab_id=TgNoebMYzZ4). The Sentinel Hub APIs use OAuth Clients to let users access the data and services. This can be obtained by following the steps below:

* Go to the [Sentinel Hub Dashboard](https://shapps.dataspace.copernicus.eu/dashboard/#/) on CDSE after logging in.

* Go to [User Settings](shapps.dataspace.copernicus.eu/dashboard/#/account/settings) which can be found in the bottom left corner of the dashboard.

* Click on the `+ Create` button under the OAuth Clients. This prompts you to put in the name of the Client and once you click on Create, the `Client ID` and `Client Password` will be generated for you that will be valid for 90 days. 

* Make sure to save this locally or follow the steps mentioned in the notebook to save the credentials for future use. Official Documentation on this can be found [here](https://documentation.dataspace.copernicus.eu/APIs/SentinelHub/Overview/Authentication.html). 

Also make sure the `data` folder containing the AOI in GeoJSON format is also present in the local folder where you are running the notebook. This will not be an issue if you clone this repo and run the notebook.

Once you have this, you are ready to run the notebook. 
