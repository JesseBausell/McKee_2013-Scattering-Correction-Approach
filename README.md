# McKee_2013-Scattering-Correction-Approach
Unaccounted scattering must be accounted for when using the WETLabs spectral absorption and attenuation meter (ac-s) with a 25 cm optical pathlength. McKee et al. (2013) devise an iterative method for correcting for undetected scattering inside flow tubes. This repository allows users to easily apply McKee et al.'s (2013) iterative approach to correcting undetected scatting signals in ac-s data.

Required files: 
    McKee_Scattering_2013.ipynb - Jupyter Notebook containing code
    MK13_coefFILE.h5 - hdf5 file containing the McKee et al. (2013) coefficients prescribed for the ten r_w values ranging from 1 to 0.95. McKee_Scattering_2013.ipynb calls upon MK13_coefFILE.h5 in the script.

This repository follows the iterative method put forth in McKee et al. (2008) and updated by McKee et al. (2013) (see biliography). Both articles rely on the same iterative approach; however, McKee et al. (2013) updates the former article by accounting for the reflection efficiency of the ac-s (or ac9) absorption tube. McKee et al. (2013) assume that the highly reflective walls of the ac-s absorption tube degrade over time due to wear and tear. It accounts for different levels of degradation by calculating different relationships between particulate backscattering and undetected scattering inside the absorption tube. McKee et al. (2013) provide teb sets of coefficients which characterize  different relationships between backscttering and undetected scattering inside ac-s absorption tube. These relationships are based on the reflection efficiency of the absorption tube. They range from r_w = 1 (100 reflection efficiency) to r_w = 0.95 (95% reflection efficiency). As such, McKee_2013-Scattering-Correction-Approach corrects ac-s performs 10 corrections for ac-s data, one for each r_w value proposed by McKee et al. (2013). 

The

Directions:
    1. Specify a "depth bin" and a "station name" where prompted in "McKee_Scattering_2013". Then run the entire script. 
    2. Select ac-s data file when prompted to do so. 
    3. Select a particulate backscattering data file when prompted to do so.
    4. Binned McKee-corrected, Hydrolight-compatible ascii files will be output into a folder titled "McKee_2013"

