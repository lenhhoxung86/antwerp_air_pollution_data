# Antwerp Air Pollution Data
Processed air pollution data (NO<sub>2</sub>, PM<sub>10</sub>, PM<sub>2.5</sub>) collected from Antwerp in April, 2019


## Overview
This repository contains the Antwerp's air pollution data collected in April, 2019. Three pollutants are considered including NO<sub>2</sub>, PM<sub>10</sub> and PM<sub>2.5</sub>. The measurements provided by this dataset are the concentration of the considered pollutants in terms of *parts per billion (ppb)* (NO<sub>2</sub>) or *microgram per cubic meter (μgm<sup>-3</sup>)* (PM<sub>10</sub> and PM<sub>2.5</sub>).

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

<escape>
<table class="tg">
  <tr>
    <th class="tg-wo29"></th>
    <th class="tg-fzdr"></th>
    <th class="tg-vt7q" colspan="2">NO<sub>2</sub></th>
    <th class="tg-0lax" colspan="2">PM<sub>2.5</sub></th>
    <th class="tg-0lax" colspan="2">PM<sub>10</sub></th>
  </tr>
  <tr>
    <td class="tg-wo29">Dataset</td>
    <td class="tg-fzdr">Method</td>
    <td class="tg-fzdr">MAE</td>
    <td class="tg-baqh">RMSE</td>
    <td class="tg-baqh">MAE</td>
    <td class="tg-baqh">RMSE</td>
    <td class="tg-baqh">MAE</td>
    <td class="tg-baqh">RMSE</td>
  </tr>
  <tr>
    <td class="tg-wman" rowspan="3">SSTR</td>
    <td class="tg-fzdr">Krigging exponential</td>
    <td class="tg-vt7q">7.21</td>
    <td class="tg-0lax">10.73</td>
    <td class="tg-0lax">3.26</td>
    <td class="tg-0lax">4.92</td>
    <td class="tg-0lax">6.34</td>
    <td class="tg-0lax">8.57</td>
  </tr>
  <tr>
    <td class="tg-fzdr">AVGAE</td>
    <td class="tg-wo29">6.27</td>
    <td class="tg-0lax">9.25</td>
    <td class="tg-0lax">2.55</td>
    <td class="tg-0lax">3.65</td>
    <td class="tg-0lax">5.04</td>
    <td class="tg-0lax">6.87</td>
  </tr>
  <tr>
    <td class="tg-fzdr">MAVGAE</td>
    <td class="tg-vt7q">6.03</td>
    <td class="tg-0lax">8.86</td>
    <td class="tg-0lax">2.45</td>
    <td class="tg-0lax">3.61</td>
    <td class="tg-0lax">4.3</td>
    <td class="tg-0lax">5.7</td>
  </tr>
  <tr>
    <td class="tg-ve35" rowspan="3">HSR</td>
    <td class="tg-fzdr">Krigging exponential</td>
    <td class="tg-wo29">6.80</td>
    <td class="tg-0lax">10.15</td>
    <td class="tg-0lax">3.08</td>
    <td class="tg-0lax">4.76</td>
    <td class="tg-0lax">5.08</td>
    <td class="tg-0lax">7.13</td>
  </tr>
  <tr>
    <td class="tg-baqh">AVGAE</td>
    <td class="tg-0lax">6.25</td>
    <td class="tg-0lax">9.26</td>
    <td class="tg-0lax">2.62</td>
    <td class="tg-0lax">4.08</td>
    <td class="tg-0lax">4.59</td>
    <td class="tg-0lax">6.08</td>
  </tr>
  <tr>
    <td class="tg-baqh">MAVGAE</td>
    <td class="tg-0lax">5.97</td>
    <td class="tg-0lax">8.92</td>
    <td class="tg-0lax">2.51</td>
    <td class="tg-0lax">3.95</td>
    <td class="tg-0lax">4.29</td>
    <td class="tg-0lax">5.66</td>
  </tr>
  <tr>
    <td class="tg-cly1" rowspan="3">HTR</td>
    <td class="tg-baqh">Krigging exponential</td>
    <td class="tg-0lax">7.04</td>
    <td class="tg-0lax">10.35</td>
    <td class="tg-0lax">3.23</td>
    <td class="tg-0lax">4.92</td>
    <td class="tg-0lax">7.11</td>
    <td class="tg-0lax">9.70</td>
  </tr>
  <tr>
    <td class="tg-baqh">AVGAE</td>
    <td class="tg-0lax">6.46</td>
    <td class="tg-0lax">9.37</td>
    <td class="tg-0lax">2.79</td>
    <td class="tg-0lax">4.03</td>
    <td class="tg-0lax">5.55</td>
    <td class="tg-0lax">7.34</td>
  </tr>
  <tr>
    <td class="tg-baqh">MAVGAE</td>
    <td class="tg-0lax">6.11</td>
    <td class="tg-0lax">9.01</td>
    <td class="tg-0lax">2.59</td>
    <td class="tg-0lax">3.83</td>
    <td class="tg-0lax">4.62</td>
    <td class="tg-0lax">5.98</td>
  </tr>
  <tr>
    <td class="tg-cly1" rowspan="3">HSTR</td>
    <td class="tg-baqh">Krigging exponential</td>
    <td class="tg-0lax">6.95</td>
    <td class="tg-0lax">10.35</td>
    <td class="tg-0lax">3.13</td>
    <td class="tg-0lax">4.86</td>
    <td class="tg-0lax">5.04</td>
    <td class="tg-0lax">7.12</td>
  </tr>
  <tr>
    <td class="tg-baqh">AVGAE</td>
    <td class="tg-0lax">6.72</td>
    <td class="tg-0lax">10.07</td>
    <td class="tg-0lax">2.74</td>
    <td class="tg-0lax">4.12</td>
    <td class="tg-0lax">4.59</td>
    <td class="tg-0lax">6.06</td>
  </tr>
  <tr>
    <td class="tg-baqh">MAVGAE</td>
    <td class="tg-0lax">6.32</td>
    <td class="tg-0lax">9.48</td>
    <td class="tg-0lax">2.61</td>
    <td class="tg-0lax">3.98</td>
    <td class="tg-0lax">4.34</td>
    <td class="tg-0lax">5.66</td>
  </tr>
</table>
</escape>

## Citation
If you find the dataset useful, please consider citing the following works:
    
    @article{do2020graph,
      title={Graph-Deep-Learning-Based Inference of Fine-Grained Air Quality from Mobile IoT Sensors},
      author={Do, Tien Huu and Tsiligianni, Evaggelia and Qin, Xuening and Hofman, Jelle and La Manna, Valerio Panzica and Philips, Wilfried and Deligiannis, Nikos},
      journal={IEEE Internet of Things Journal},
      year={2020},
      publisher={IEEE}
}


    @inproceedings{do2019matrix,
      title={Matrix completion with variational graph autoencoders: Application in hyperlocal air quality inference},
      author={Do, Tien Huu and Nguyen, Duc Minh and Tsiligianni, Evaggelia and Aguirre, Angel Lopez and La Manna, Valerio Panzica and Pasveer, Frank and Philips, Wilfried and Deligiannis, Nikos},
      booktitle={ICASSP 2019-2019 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)},
      pages={7535--7539},
      year={2019},
      organization={IEEE}
    }
