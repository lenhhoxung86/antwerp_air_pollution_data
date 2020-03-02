# Antwerp Air Pollution Data
Processed air pollution data (NO<sub>2</sub>, PM<sub>10</sub>, PM<sub>2.5</sub>) collected from Antwerp during April, 2019


## Overview
This repository contains the Antwerp's air pollution data collected in April, 2019. Three pollutants are considered including NO<sub>2</sub>, PM<sub>10</sub> and PM<sub>2.5</sub>. The measurements provided by this dataset are the concentration of the considered pollutants in terms of *parts per billion (ppb)* (NO<sub>2</sub>) or *milligram per cubic meter (ugm<sup>-3</sup>)* (PM<sub>10</sub> and PM<sub>2.5</sub>).

There are four folders, namely SSTR, HST, HTR and HSTR. Each folder has the data corresponding to a specific setting as follow.
- SSTR: Standard spatio-temporal resolution
- HSR: High spatial resolution
- HTR: High temporal resolution
- HSTR: High spatio-temporal resolution

Each folder has air quality measurements in sparse matrix format (e.g., `no2_measurements.npz`). 
A row in the air quality measurement matrix corresponds to a location. A column in the air quality measurement matrix corresponds to a time instance (e.g., `60` minutes, `30` minutes). 
In addition, it also contains the geo-coordinates of all the considered locations (`nodes.txt`). 
A row in the file `nodes.txt` has the following format:

`node_id    longitude   latitude`

The underlying graph created by the road network of Antwerp is also provided via the corresponding adjacency matrix (`adj.npz`).
Furthermore, the training and testing masks are provided for result reproduction.

## Air Quality Inference Result
The following table presents the result for air quality inference achieved by using variational graph autoencoder (AVGAE) and multi-input variational graph autoencoder (MAVGAE).

| - | - | <td colspan=2>NO<sub>2</sub> |  <td colspan=2>PM<sub>2.5</sub>    |  <td colspan=2>PM<sub>10</sub> |
| Dataset | Method | MAE | RMSE |  MAE |  RMSE | MAE | RMSE |
