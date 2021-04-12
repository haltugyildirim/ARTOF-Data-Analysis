# Angle-resolved Time-of-Flight Data   & Analysis Module

<p align="center">
<img src="https://github.com/haltugyildirim/ARTOF-Data-Analysis/blob/main/images/drawing_plain_blue.svg" width="500" class="center" alt="logo"/>
    <br/>
</p>

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
![Last Commit](https://img.shields.io/github/last-commit/haltugyildirim/ARTOF-Data-Analysis)
![Python](https://img.shields.io/badge/python-v3.7+-blue.svg)
[![Github All Releases](https://img.shields.io/github/downloads/haltugyildirim/ARTOF-Data-Analysis/total.svg)]()


This project is focused on reading, plotting and analyzing data from Angle-Resolved Time of Flight(ARTOF) experiments. ARTOF is an offshoot of [ARPES](https://en.wikipedia.org/wiki/Angle-resolved_photoemission_spectroscopy) systems where instead of using [hemispherical analyzers](https://en.wikipedia.org/wiki/Hemispherical_electron_energy_analyzer), a [time-of-flight](https://en.wikipedia.org/wiki/Time_of_flight) tube coupled with a [delay line detector](https://en.wikipedia.org/wiki/Microchannel_plate_detector#Delay_line_detector) is used. This gives an advantage to map [band structure](https://en.wikipedia.org/wiki/Electronic_band_structure) on both dimensions without any need to change the angle of the sample.

Data is binned as a hdf5 file, common in ARPES experiments. The character of data is mostly 4 dimensional; delaypoints(time), energy(time-of-flight), y(angle perpendicular to plane of incidence), x(angle parallel to plane of incidence). An incredible package; [xarray](https://github.com/pydata/xarray) is used for labeling this 4 dimensional matrix. Selection, addition and algebraic manipulation of data is done using the functions from xarray package.

Cross-correlation fitting; a method to find the length of ultrashort laser-pulses from delaypoints, is done with curve_fit from [SciPy](https://www.scipy.org/) using a convoluted version of an exponential decay and a gaussian.

All the plotting is either done with build-in function from [xarray](https://github.com/pydata/xarray) or [Matplotlib](https://matplotlib.org/).

Dependencies
---
 Install the dependent packages with requirements. As the examples are with Jupyter Notebook, I recommend to use the package with [Anaconda](https://www.continuum.io/downloads).
 
 ```console
 $ pip install -U -r requirements
 ```
  * [NumPy](https://www.numpy.org/)
  * [math](https://docs.python.org/3/library/math.html)
  * [SciPy](https://www.scipy.org/)
  * [Matplotlib](https://matplotlib.org/)
  * [h5py](https://pypi.org/project/h5py/)
  * [xarray](https://github.com/pydata/xarray)
  * [pytexit](https://github.com/erwanp/pytexit) -optional, used for double checking the formulas
  * [OpenCV on Wheels](https://pypi.org/project/opencv-python/) -only needed for polar coordinates fourier analysis -reconstructing images
  * [PyAbel](https://github.com/PyAbel/PyAbel) -only needed for polar coordinates fourier analysis
  * [scikit-image](pip install scikit-image) -only needed for (experimental) 3d voxel plotting
  * 
# Important!
PyAbel package should be installed directly from [project's GitHub page](https://github.com/PyAbel/PyAbel), following the guide. The version in Python Package Index (PyPI) do not contain the module \*.tools, which is used for polar coordinates reprojection.

Future directions;
---

    * Deprecating the dataimport function for angle and combining both the momentum data import and angle data import in one single function
    * Rewrite the plotting functions for better readability
    * Import the angle to momentum conversion program to Python from C++
    * Possible inclusion of ARPES / HHG data and/or Momentum Microscope data

Disclaimer
---

As the data acquisition software is very problematic and old, many error comes during the experiment; crashing of the software, data omitting during saving etc. So this code in here also deals with this system specific problems. So if you want to use this piece of code in here, please consider asking me beforehand.


