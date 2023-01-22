# Repository.  

BeatBox monodomain cardiac simulator.

# Background.  

I was the lead developer of BeatBox software during 2013-2014. It is a modular environment primed for
customization and development. As such, it is suitable for low dimensional cell models (e.g. FitzHugh Nagumo, Fenton Karma)
using which rich phenomena (e.g. spiral wave filament dynamics) have been studied by others.

I have used this package for the following representative outputs:  
* Mario Antonioletti, Vadim N. Biktashev, Adrian Jackson, Sanjay R. Kharche, Tomas Stary, Irina Biktasheva. BeatBox — HPC Simulation Environment for Biophysically and Anatomically Realistic Cardiac Electrophysiology. PLoS ONE 12(5): e0172292. (Authorship in alphabetical order).
* Sanjay R. Kharche, Irina V. Biktasheva, Gunnar Seemann, Henggui Zhang, Vadim N. Biktashev. A Computer Simulation Study of Anatomy Induced Drift of Spiral Waves in the Human Atrium BioMed Research International (2015). 2015: 731386.
* Sanjay R. Kharche, Biktasheva IV, Zhang H, Biktashev VN. Simulating the role of anisotropy in human atrial cardioversion. Conf Proc IEEE Eng Med Biol Soc. (2013). 2013: 6838-41.
* Sanjay R. Kharche et al. Computer Simulation of the Role of Fibre Orientation in Cardioversion of Chronic Atrial Fibrillation. (2013). J Electrocardiology 46(4): e6-e7.

# Dependencies.

The package is provided in two flavours. All flavours are tested to compile and run in Uni. Exter computer (Zen),
UK HPC service (Archer), Compute Canada machines, and on personal Mac computers. In addition,
a non-X11 flavour is also provided to assist in production runs.

## BeatBox  

The standard version of BeatBox uses X11 for graphics/graphics forwarding. It is compiled using
a standard mpi compiler for C language. 

## BeatBox using Sundials dependency.  

The Sundials based version of BeatBox requires availability of the Sundials library in addition to mpich.
Sundials may not work as expected/desired on MacOS.

# Install.  

Suitable cmake and makefiles are provided, in addition to install instructions for each flavour.
openmpi is not recommended, use mpich.

# Sources description.

The BeatBox code is modular and uses operator splitting to provide the numerical solution for the 
mono-domain reaction-diffusion equations. The documentation found in this repo at beatbox_sources/BeatBox/manuals/
provides a starting point for developers.

# Use.  

Untar everything in a directory using:
tar -xvf *.tar

The program requires an input script accompanied by description of the heart's geometry. Example scripts (extension: bbs) are 
provided throughout the sources. The geometry is an ASCII text file that provides coordinates, finite difference node number, 
and material properties. An example of how the geometry is generated is provided in the sources: beatbox_sources/BeatBox/atrium2bbg/*.c
In addition, an optional initial conditions file, termed rec file or record file, can also be provided in cases when abnormal electrical 
waves are desired at the onset.  

The parallelization uses mpich in any one of the 3 spatial axes, e.g. in 3D, it will parallelize along the Z axis. Once the simulation script, the input geometry, cell models, and optional initial conditions are provided, the simulation can be performed on any suitable computer. An example of the submission script 
for a computer that uses PBS scheduling can be found here: beatbox_sources/BeatBox/crn2d_feedback/simple.pbs .

The output is in a proprietry format called ppm format. Post-processing utilities are provided that convert ppm to the more widely used
VTK format. Post-processing utilities also simulate ECG, track spiral wave tips and filaments, among other functionality.

# Maintainer.  

BeatBox is an excellent teaching and training tool for scientific programmers and can be developed to suit graduate thesis/research projects.
As such, I am now using my VCPL package rather than BeatBox. It is unsupported. 

# Acknowledements.

This project was generously funded by the UK EPSRC led by Prof. VN Biktashev (CEMPS, Exeter; 2013-2014). 

# Licence.

BeatBox package has its own GNU licence. Please see the source code directories for the licence.

## Dr. Sanjay R. Kharche, Ph.D. (App. Maths).  
January 23rd, 2023.  
Email: Sanjay.Kharche@lhsc.on.ca , skharche@uwo.ca , srk.london@yahoo.com .  
Phone: +15198780685 (mobile).  
Website: https://kcru.lawsonresearch.ca/research/srk/index.html  

