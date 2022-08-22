# GPX 3D Mapping

This repo is a collection of methods and scripts to create 3D Map renders
given a GPX track file.

The R scripts r copies or have been inspired by the following repositories:

 - [edeaster/Routes3D](https://github.com/edeaster/Routes3D)
 - [fredderks/3DHikeMap](https://github.com/fredderks/3DHikeMap)
 
 
 ## How to
 
 ### Install
 
 The easiest way to install is to open the repo in `Rstudio` and upon opening
 any of the scripts in the editor, a message to install the missing libraries
 will pop at the top.
 
 Alternatively, for each of the libraries, in the R console:
 
 ```bash
 package.install('<name-of-the-package>')  # e.g.: package.install('elevatr')
 ```
 
 > NOTE: Some system wide dependencies might need to be installed. 
 > See any package installation error to determine if any is missing. 
 
 
 ### Run
 
 To run the selected rendering script:
 
 ```bash
 source('3DMapping.R')  # Will prompt for the GPX file as input
 ```
 
 This script will save a series of renders as pngs in the `Track` directory.
 Then, to compose a GIF from all renders:
 
 ```bash
 cd Track
 convert -delay 2 -loop 0 *.png output.gif
 
 # Alternatively (faster but less quality):
 ffmpeg -framerate 5 -y -i %02d.png output_2.gif
 ```