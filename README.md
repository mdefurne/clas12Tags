# clas12Tags


This is a series of tags of the GEMC source code to match the various simulation/calibration/reconstruction software versions.

The tags also contain the geometry files and the gcard to run gemc.

Every tag is installed in /group/clas12/gemc

To use: 

source /group/clas12/gemc/environment.csh <tag>

If no tag is given, the script will currently load 4a.2.0.

Tags
----

- 4a.2.0: Same as 4a.1.0 with:
 
  - use JLAB_VERSION 2.1, with new mlibrary
  - Micromegas: updated  geometry and digitization
  - DC: realistic time to distance function, reading constants from CCDB
  - DC: ministagger for DC region 3: "even closer" SL 1,3,5: +300um, SL 2,4,6: -300um
  - LTCC: Reading CCDB SPE calibration constants
  - LTCC: Smearing ADC based on calibration constants
  - CTOF javacad instead of cad (should be indentical)
  - Fixed smeared infor in generated summary for FASTMC mode
  - CAD modeling of both the beamline and the torus
  - improved/fixed CND digitization routine
  - updated RF timing (mlibrary) 
  - BST+MM: using 3+3 configurations
  

- 4a.1.0: Same as 4a.0.2 with:

  - fixed a bug that affect output file size 
  - fixed bug that affected multiple cad imports
  - added micromegas geometry and hit processes
  - RF output correct frequency in the clas12 gcard
  - updated FT geometry and hit process
  - updated ftof geometry
  - added reading of FTOF reading of tdc conversion constants from the database
  - check if strip_id is not empty in bmt_ and fmt_strip.cc, otherwise fill it.


- 4a.0.2: Same as 4a.0.1 but with full (box, mirrors, pmts shields and WC) LTCC geometry / hit process routine.
- 4a.0.1: Same as 4a.0.0 but with FTOF geometry fix
- 4a.0.0: KPP configuration. Fixes in source and hit process for FTOF, added EC gains. Java geometry uses now coatjava 3. Database fixed for DC geometry. Linear time-to-distance for DC.
  CTOF in the KPP position configuration in the new kpp.gcard.
- 3a.1.0: same as 3a.0.2 but with DC time-to-distance implementation.
- 3a.0.2: same as 3a.0.1 but with CND fix.
- 3a.0.1: same as 3a.0.0 but ctof has status working.
- 3a.0.0: git commit d3a5dc1, Dec 2 2016. Includes FTOF and CTOF paddle delays from CCDB, and CTOF center off-set.



To produce:
-----------

1. create new tag dir
2. change gcard to point to new location
3. change environment.csh to point to the new tag
4. scons -c in $GEMC and cp -r $GEMC then cd source and rm .git*
5. mkdir experiments, copy files from gemcApp/experiments
