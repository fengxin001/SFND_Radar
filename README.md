# Radar Target Generation and Detection

[//]: # (Image References)
[image0]: ./graphs/projectLayout.png "layout"
[image1]: ./graphs/FFT.jpg "FFT"
[image2]: ./graphs/RawAmplitude.jpg "RawAmplitude"
[image3]: ./graphs/CFAR_OUT.jpg "CFAR_OUT"
[image4]: ./graphs/FiltedAmplitude.jpg "FiltedAmplitude"


This project is to use frequency modulated continuous-wave (FMCW) radar and related post-processing techniques to detect the location and speed of object (e.g. car). The following is an overview of the project.

![alt text][image0]

* Configure the FMCW waveform based on the system requirements. 
* Define the range and velocity of target and simulate its displacement.
* For the same simulation loop process the transmit and receive signal to determine the beat signal
* Perform Range FFT on the received signal to determine the Range
* Towards the end, perform the CFAR processing on the output of 2nd FFT to display the target.
## project rubric 

#### FMCW Waveform Design
**Using the given system requirements, design a FMCW waveform. Find its Bandwidth (B), chirp time (Tchirp) and slope of the chirp.**   

Below is Radar speicification given by the project
  
%% Radar Specifications   
%%%%%%%%%%%%%%%%%%%%%%%%%%%  
% Frequency of operation = 77GHz  
% Max Range = 200m  
% Range Resolution = 1 m  
% Max Velocity = 100 m/s  
%%%%%%%%%%%%%%%%%%%%%%%%%%%  

In a README file, write brief explanations for the following:
0.   There are couple steps before 2D CFAR process.
<<<<<<< HEAD
	a. Run range FFT for beat signal. 
	b. Reshape the vector into Nr*Nd array.
	c. Run the FFT on the beat signal along the range bins dimension.
	d. Normalize the FFT output.
	e. Take the absolute value of that output.
	f. Keep one half of the signal.
=======
a. Run range FFT for beat signal. 
b. Reshape the vector into Nr*Nd array.
c. Run the FFT on the beat signal along the range bins dimension.
d. Normalize the FFT output.
e. Take the absolute value of that output.
f. Keep one half of the signal.

>>>>>>> 3d39303... type: Udacity SFND Radar project with git commit message style
Following plot is a FFT output from the steps mentioned above.
	![alt text][image1]

Raw signal before 2D CRAR process is showing below.
	![alt text][image2]

1. Implementation steps for the 2D CFAR process.
	Please refer to line 181 to 270.
	First, Set the training boundary, Guard boundary and offset
	Second, Create a vector to store noise_level for each iteration on training cells
	Third, Loop through the target area, calculating mean value of training cell, and utilizing it during comparison with CUT.
	Finally, plot the CFAR after filtering the background noise. 

2. Selection of Training, Guard cells and offset.
	Tr = 8;
	Td = 6; 
	Gr = 3;
	Gd = 3;
	offset = 5;

3. Steps taken to suppress the non-thresholded cells at the edges.
	Flat the edges to zero by checking if matrix value is either zero or 1.
	
4. The output by applying threshold in this CFAR process is showing below.
     ![alt text][image3]
5. The final fileded results is showing below.
     ![alt text][image4]
