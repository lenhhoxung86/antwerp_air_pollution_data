# Antwerp Air Pollution Data
Processed air pollution data (NO2, PM10, PM2.5) collected from Antwerp during April, 2019


## Overview
This repository contains the Antwerp's air pollution data collected from Antwerp in April, 2019. Three pollutants are considered including NO<sub>2</sub>, PM<sub>10</sub> and PM<sub>2.5</sub>. The measurements provided by this dataset are the concentration of the considered pollutants in terms of *parts per billion (ppb)* (NO<sub>2</sub>) or *milligram per cubic meter (ugm<sup>-3</sup>)* (PM<sub>10</sub> and PM<sub>2.5</sub>).

There are four folders, namely SSTR, HST, HTR and HSTR. Each folder has the data corresponding to a specific setting as follow.
- SSTR: Standard spatio-temporal resolution
- HSR: High spatial resolution
- HTR: High temporal resolution
- HSTR: High spatio-temporal resolution

Each folder has data in sparse matrix format (`npz`). In addition, it also contains the geo-coordinates of all the considered locations (`file nodes.txt`). The underlying graph created by the road network of Antwerp is also provided via the corresponding adjacency matrix (`adj.npz`).
Furthermore, the training and testing masks are provided for result reproduction.