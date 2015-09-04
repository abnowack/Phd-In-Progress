# August 31

##### Created a task list for things to get done.

Imaging
- [ ] FBP for arc geometry
- [ ] Get Z value of FBP correct
- [ ] Speed up ray tracing
- [ ] Understand SPECT, Ultrasound

FREYA
- [ ] Make Crye Plots w/ and w/o FREYA
- [ ] Other observables?

Point Kinetics
- [ ] Point Kinetics walkthrough
- [ ] Coupling terms
- [ ] System of terms
- [ ] Geometric Dependence

##### Including TikZ graphs in ipython notebooks

Need to install [ipython magic extension for tikz](https://github.com/mkrphys/ipython-tikzmagic)

For initial setup, open any ipython notebook and enter 

`%install_ext https://github.com/mkrphys/ipython-tikzmagic/blob/master/tikzmagic.py`

Then to use afterwards include

`%load_ext tikzmagic`

On windows with my latex installation I also needed to imgconvert.exe which is provided by imagemagick. So I installed the windows binary distribution [here](http://www.imagemagick.org/script/binary-releases.php#windows)

While this does install the needed program, the python script is a little outdated as the main executable is now called convert.exe

To fix this after installing imagemagick browse to the installation folder (C:\Program Files\ImageMagick-6.9.2-Q16 in my case) and create a copy of convert.exe named imgconvert.exe

# September 4

Working on instead determine how to solve for the object image directly from projection data. Sophisticated image reconstruction algorithms can be applied afterwards.

Roughly, we have S = P T where S is my observation and T is the unknown image. I'm trying to figure out how to create P, the matrix which turns image pixel into counts in the detector. I think I just need to turn each image pixel "on" and project the output.

Need to create a discrete pixel setup of my raytracing programs. Tasks

- [ ] Create a test image
- [ ] Create sinogram of test image
- [ ] Create transformation matrix for single pixel
- [ ] Create transformation matrix for all pixels in image
- [ ] Try to solve directly
