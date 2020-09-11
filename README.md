# McKee_2013-Scattering-Correction-Approach
Unaccounted scattering must be accounted for when using the WETLabs spectral absorption and attenuation meter (ac-s) with a 25 cm optical pathlength. McKee et al. (2013) devise an iterative method for correcting for undetected scattering inside flow tubes. This repository allows users to easily apply McKee et al.'s (2013) iterative approach to correcting undetected scatting signals in ac-s data.

Required files: 
    McKee_Scattering_2013.ipynb - Jupyter Notebook containing code
    MK13_coefFILE.h5 - hdf5 file containing the McKee et al. (2013) coefficients prescribed for the ten r_w values ranging from 1 to 0.95. McKee_Scattering_2013.ipynb calls         upon MK13_coefFILE.h5 in the script.

This repository follows the iterative method put forth in McKee et al. (2008) and updated by McKee et al. (2013) (see biliography). Both articles rely on the same iterative approach; however, McKee et al. (2013) updates the former article by accounting for the reflection efficiency of the ac-s (or ac9) absorption tube. McKee et al. (2013) assume that the highly reflective walls of the ac-s absorption tube degrade over time due to wear and tear. It accounts for different levels of degradation by calculating different relationships between particulate backscattering and undetected scattering inside the absorption tube. McKee et al. (2013) provide teb sets of coefficients which characterize  different relationships between backscttering and undetected scattering inside ac-s absorption tube. These relationships are based on the reflection efficiency of the absorption tube. They range from r_w = 1 (100 reflection efficiency) to r_w = 0.95 (95% reflection efficiency). As such, McKee_2013-Scattering-Correction-Approach corrects ac-s performs 10 corrections for ac-s data, one for each r_w value proposed by McKee et al. (2013). 

McKee_Scattering_2013.ipynb is compartmentalized into multiple functions, each one annotated. These functions can be re-aranged independently or repurposed to another task.

Directions for use:
    1. Specify a "depth bin" and a "station name" where prompted in "McKee_Scattering_2013". Then run the entire script. 
    2. Select ac-s data file when prompted to do so. 
    3. Select a particulate backscattering data file when prompted to do so.
    4. Binned McKee-corrected, Hydrolight-compatible ascii files will be output into a folder titled "McKee_2013"

Requirements:
    1. user-selected ac-s file should be a hdf5 file consisting of the following variables:   
        a. A_CORR - matrix of single absorption spectra (m x n): m indicates the number of spectra; n indicates the number of ac-s channels, or wavelengths.
        b. C_CORR - matrix of single attenuation spectra (m x n), m indicates the number of spectra and n indicating the number of ac-s channels, or wavelengths.
            *A_CORR and C_CORR should be the same size. Except for undetected scatter, all other corrections should already be applied (e.g. temperature, salinity, pure                    water calibration, etc.)
            *My respository "acsPROCESS_INTERACTIVE" outputs data in the above-described format
        c. deptH - array of depths corresponding to the depths each individual ac-s spectrum
        d. a_wv - array of central wavelengths of each ac-s channel. Attenuation channels are slightly offset from absorption channels, however, this repository assumes that           attenuation data has been interpolated for centered wavelengths of absorption channels prior to use.
     2. user-selected particulate backscattering file should exist in a Hydrolight-compatible ascii (.txt) format. This mean sigma-corrected and depth-binned.

Outputs:
McKee_2013-Scattering-Correction-Approach will create a new folder titled "McKee_2013" inside the folder that contained the ac-s file selected by the user. The repository will place 10 hydrolight-compatible ac-s ascii files inside this folder. Filenames will mimick the name of the user-selected asii file (see step 1), except that they will be identifiable by their endings, which correspond to the r_w used to correct data. For example, "_Mc13_0950" corresponds to r_w being set equal to 0.95, where "_Mc13_1000" corresponds to r_w being equal to 1.
