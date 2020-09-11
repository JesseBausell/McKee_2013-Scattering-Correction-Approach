# McKee_2013-Scattering-Correction-Approach
Unaccounted scattering must be accounted for when using the WETLabs spectral absorption and attenuation meter (ac-s) with a 25 cm optical pathlength. McKee et al. (2013) devise an iterative method for correcting for undetected scattering inside flow tubes. This repository allows users to easily apply McKee et al.'s (2013) iterative approach to correcting undetected scatting signals in ac-s data.

Required files: McKee_Scattering_2013.ipynb & MK13_coefFILE.h5

This repository follows the iterative method put forth in McKee et al. (2008) and updated by McKee et al. (2013) (see biliography). Both articles rely on the same iterative approach; however, McKee et al. (2013) updates the former article by accounting for the reflection efficiency of the ac-s (or ac9) absorption tube. McKee et al. (2013) assume that the highly reflective walls of the ac-s absorption tube degrade over time due to wear and tear. It accounts for different levels of degradation by calculating different relationships between particulate backscattering and undetected scattering inside the absorption tube. McKee et al. (2013) provide such coefficients for 10 levels of 
