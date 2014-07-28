<center>
<img src="./index_files/hybrid_image.jpg" width="410" height="361">
<br>
(Look at image on right from very close, then from far away.)
</center>

# Project 1: Image Filtering and Hybrid Images

## Brief
* Due: TBA
* Required files: results/index.md, and code/

##Overview

<p>The goal of this assignment is to write an image filtering function and use it to create <a href="http://cvcl.mit.edu/hybridimage.htm">hybrid images</a> using a simplified version of the SIGGRAPH 2006 <a href="http://cvcl.mit.edu/publications/OlivaTorralb_Hybrid_Siggraph06.pdf">paper</a> by Oliva, Torralba, and Schyns.
<i>Hybrid images</i> are static images that change in interpretation as a function of the viewing distance.
The basic idea is that high frequency tends to dominate perception when it is available, but, at a distance, only the low frequency (smooth) part of the signal can be seen.
By blending the high frequency portion of one image with the low-frequency portion of another, you get a hybrid image that leads to different interpretations at different distances.
</p>
<br>

##Details

<p>
This project is intended to familiarize you with MATLAB and image filtering. Once you have created an image filtering function, it is relatively straightforward to construct hybrid images. If you don't already know MATLAB, you will find this <a href="http://cs.brown.edu/courses/csci1430/docs/matlab-tutorial/">tutorial on MATLAB</a> helpful.
</p><p>
<b>Image Filtering.</b> Image filtering (or convolution) is a fundamental image processing tool. See chapter 3.2 of Szeliski and the lecture materials to learn about image filtering (specifically linear filtering). MATLAB has numerous built in and efficient functions to perform image filtering, but you will be writing your own such function from scratch for this assignment. More specifically, you will implement <code>my_imfilter()</code> which imitates the default behavior of the build in <code>imfilter()</code> function. As specified in <code>my_imfilter.m</code>, your filtering algorithm must (1) support grayscale and color images (2) support arbitrary shaped filters, as long as both dimensions are odd (e.g. 7x9 filters but not 4x5 filters) (3) pad the input image with zeros or reflected image content and (4) return a filtered image which is the same resolution as the input image. We have provided a script, <code>proj1_test_filtering.m</code>, to help you debug your image filtering algorithm. 

</p><p>
<b>Hybrid Images.</b> A hybrid image is the sum of a low-pass filtered version of the one image and a high-pass filtered version of a second image. There is a free parameter, which can be tuned for each image pair, which controls <i>how much</i> high frequency to remove from the first image and how much low frequency to leave in the second image. This is called the "cutoff-frequency". In the paper it is suggested to use two cutoff frequencies (one tuned for each image) and you are free to try that, as well. In the starter code (`proj1.m`), the cutoff frequency is controlled by changing the standard deviation of the Gausian filter used in constructing the hybrid images.
</p><p>
We provide you with 5 pairs of aligned images which can be merged reasonably well into hybrid images. The alignment is important because it affects the perceptual grouping (read the paper for details). We encourage you to create additional examples (e.g. change of expression, morph between different objects, change over time, etc.). See the <a href="http://cvcl.mit.edu/hybridimage.htm">hybrid images project page</a> for some inspiration. 
</p><p>
For the example shown at the top of the page, the two original images look like this:
</p><p>
</p><center><img src="./index_files/dog.jpg"><img src="./index_files/cat.jpg"></center>
<p></p><p>
The low-pass (blurred) and high-pass versions of these images look like this:
</p><p>
</p><center><img src="./index_files/low_frequencies.jpg"><img src="./index_files/high_frequencies.jpg"></center>
<p></p><p>
The high frequency image is actually zero-mean with negative values so it is visualized by adding 0.5. In the resulting visualization, bright values are positive and dark values are negative.
</p><p>
Adding the high and low frequencies together gives you the image at the top of this page. If you're having trouble seeing the multiple interpretations of the image, a useful way to visualize the effect is by progressively downsampling the hybrid image as is done below:
</p><p>
</p><center><img src="./index_files/cat_hybrid_image_scales.jpg"></center>
<p></p><p>
The starter code provides a function <code>vis_hybrid_image.m</code> to save and display such visualizations.

</p><p>
<b>Potentially useful MATLAB functions</b>: <code>fspecial()</code> and the operators in the <a href="http://cs.brown.edu/courses/csci1430/docs/matlab-tutorial/">MATLAB tutorial</a> which make it efficient to cut out image subwindows and do the convolution (dot product) between them. <code>padarray()</code>. 
<br>
<b>Forbidden functions</b> you can use for testing, but not in your final code: <code>imfilter()</code>, <code>filter2()</code>, <code>conv2()</code>, <code>nlfilter()</code>, <code>colfilt()</code>.
</p><br>

## Extra Points
* +2 pts: If you make your code publicly available.
* +2 pts: If you comment on other public codes by creating a new issue. Make sure you send me a screenshot of the comments.
* Other things that impress me.

## Writeup
For this project, and all other projects, you must do a project report in results folder using [Markdown](https://help.github.com/articles/markdown-basics). We provide you with a placeholder [index.md](./results/index.md) document which you can edit. In the report you will describe your algorithm and any decisions you made to write your algorithm a particular way. Then, you will describe how to run your code and if your code depended on other packages. Finally, you will show and discuss the results of your algorithm. In the case of this project, show the results of your filtering algorithm (the test script saves such images already) and show some of the intermediate images in the hybrid image pipeline (e.g. the low and high frequency images, which the starter code already saves for you). Also, discuss anything extra you did. Feel free to add any other information you feel is relevant.

## Rubric
* +50 pts: Working implementation of image filtering in my_imfilter.m
* +30 pts: Working hybrid image generation
* +20 pts: Writeup with several examples of hybrid images
* +10 pts: Extra credit (up to ten points)
* -5*n pts: Lose 5 points for every time (after the first) you do not follow the instructions for the hand in format

## Handing in
* Publicly fork version

* Privately duplicated version

## Credits
	Assignment modified by Min Sun based on James Hays and Derek Hoiem's previous developed projects
