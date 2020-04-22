# reglyman

**Features**

reglyman is a python library developed for the inversion of the Lyman alpha forest flux along single lines of sight at high spectral resolution. It provides tools for the fast creation of synthtetic Lyman-alpha forest flux data and tools for estimating the neutral hydrogen density along the lines of sight from the normalized flux. 

The toolbox has been developed at the Institute for Astrophysics in Göttingen. It contains the source code for the publication Müller, Behrens, Marsh 2020: "An Optimized Ly-alpha Forest Inversion Tool Based on a Quantitative Comparison of Existing Reconstruction Methods" (submiited to MNRAS). This paper provides more detailed descriptions of the inversion tools that are used.

reglyman makes strong use of the existing regpy (regularization methods for inverse problems) and nbodykit (creating mocks of galxies) toolboxes. The Lyman-alpha forest is computed with the use of the lognormal approach also used within nbodykit. The inverse problem of recovering the neutral hydrogen density from the Lyman-alpha forest is implemented with the help of the regpy library.

The two repositories could be found under:

*  nbodykit: https://nbodykit.readthedocs.io/en/latest/index.html . Nbodykit is described in the paper Hand et. al. 2018: "nbodykit: An Open-source, Massively Parallel Toolkit for Large-scale Structure"; AJ, 160, 156
*  regpy: https://num.math.uni-goettingen.de/regpy/

Please note that this repository is under heavy development, so do expect bugs and tiny documentation. Also it depends strongly on the regpy repository which is also under heavy development. Future regpy releases will largely extend the amount on inversion procedures available for Lyman-alpha forest analysis and can be directly incorporated in this repository. The reglyman repository will be extended in future releases. 

**Installation**

We provide a pip install option. Download the files, navigate to the place where you stored the reglyman files and simply type: pip install . .
The library depends on: 
    
*  regpy
*  numpy
*  scipy
*  matplotlib
*  nbodykit
*  multiprocessing

**Description**

The file-structure of the repository is as follows:

Paper: Contains a preprint of the paper which has been sent to MNRAS. In this paper we compare the different inversion schemes and propose a new one. For more details on the inversion methods implemented within this library we refer to this manuscript and the references therein.

Examples: Consists of examples for the inversion along 25 lines of sights, i.e. routines for the creation of synthetic data, for mimicing noise and instrumental effects and for performing the inversion procedure:
*  rl: Richardson-Lucy algorithm
*  irgn: Iterative Gauss-Newton method
*  pc: Probability Conservation approach
*  rpc: Regularized Probability Conservation approach

   The synthetic_data subordner consists of files for the creation of synthetic data (i.e. the density field, the spectrum and initial guesses for inversion procedure):
* generate_density: Generate the overdensity field
* synthetic_spectrum: Calculate the noisy and smoothed spectrum, find proper initial guess for inversion (either from the hydrogen number density or the baryonic overdensity)

   
Reglyman: The modules extending the options available in nbodykit and regpy:
*    The operators subordner consists of the operators describing the forward computation of the Lyman-alpha forest (LymanAlpha) and supporting operators for the inversion procedures.
*    In the solvers subordner we stored the solvers used for this study (see examples). More solver will be available within future releases of the regpy library.
*    In the density subordner we stored routines available from nbodykit to simulate the cosmic overdensity field.
*    The util ordner contains some supporting routines.

   
The repository has a very similar structure as the regpy repository to maximize compatibility with future releases. Thus, for more information on the running example files we refer to their documentation and the documentation within our example files.

