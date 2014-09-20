TIMELAPSE
Use Python to create timelapse images

RASPISTILL
Python time lapse & image processing

Create a time-lapse video with the Raspberry Pi camera

On December 27th, 2013, a pair of Raspberry Pis with Raspberry Pi cameras were placed in a cottage in Ontario overlooking Georgian Bay. About four months later, they were found to have performed wonderfully, capturing over 40,000 photos at two minute increments. Although the shoot was planned for a few months, it was not expected to be as successful as it was. When the cameras were setup, the windows were quite frosted over. Therefore, the expected outcome was to see the back of an icy window. However, the windows stayed clear during the entire winter. The photographs taken captured ice forming and dissolving on the lake, deer passing like ghosts, magnificent storms and amazing sunrises. The images were compiled together to form the resulting time-lapse video given at: http://inventingsituations.net/winter-on-georgian-bay

In this article, there are some code snippets that can be used to make a time-lapse video using Python and command line tools. In particular, the raspisti ll program is used to capture the images and the Python Image Library (PIL) and mencoder are used to create the final movie.

Setting up Raspberry Pi and camera

Follow http://www.raspberrypi.org/help/cameramodule-setup/ to connect a Raspberry Pi camera to a Raspberry Pi. Then install the latest Raspbian image and type:

Select

This will enable the camera, use all of the SD card for the Linux installation, turn off the boot to X and allow the ARM processor to use the maximum amount of memory. Next, make sure that Raspbian is up to date and install the libraries and programs needed for this project:

Taking photos with raspistill

The easiest way to use the Raspberry Pi camera is via the raspisti ll command. It has a time-lapse option, which many people have used to good effect. For an extremely long time lapse, finer control over the images taken proved to be better than the automatic settings. As a result, a Python script was written to take photographs at regular intervals. Calculations were used to make sure that the images were of consistent quality. Image quality consistency was maintained by the manipulation of shutter speed, ISO and post capture alteration.

The two options that control the brightness of an image are the shutter speed and the ISO (International Standards Organization) setting. The shutter speed controls how long the camera collects light to create an image, where a longer shutter speed will create brighter images but will be more likely to have motion blur if there is movement in the frame. On the Raspberry Pi, the slowest shutter speed available is about 2.5 seconds; longer speeds will cause the camera to hang and not take pictures until the Raspberry Pi is rebooted. To be safe, the maximum shutter speed was set to two seconds. Shutter speeds in raspisti ll are measured in microseconds. Therefore, a shutter speed of 1000000 implies one second.

ISO setting controls the sensitivity of the sensor, within a range of 100 (low sensitivity) to 800 (high sensitivity). When the ISO setting is high, brighter images are taken, but they will also tend to be much more noisy.

The command raspisti ll can be used to take a photograph with a set shutter speed and ISO setting. The automatic settings should be avoided, apart from AWB (auto white balancing):

Python can be used to run raspisti ll by using a subprocess call:

The goal for the project was to keep images at about the same brightness over the course of a day. The brightness of each image was measured. Then the shutter speed and ISO setting were adjusted. Since fast movements are not important for time lapse pictures, the ISO was kept at 100 as much as possible to ensure high quality images.

Calculating the average brightness

The Python Imaging Library (PIL) is great for manipulating images in Python:

This example opens an image and uses the image's histogram to compute the average brightness of the image. For a greyscale image, there are 256 possible pixel values. The histogram counts how many pixels there are for each value. The average brightness of the images is calculated by adding up all of the pixel brightness values and dividing by the number of pixels.

Adjusting the shutter speed

To retain the same image brightness, as the light increases or decreases, either the shutter speed or the ISO setting should be adjusted. The brightness from the previous image can be used to adjust the shutter speed:

where 128 is the target brightness and ss is the shutter speed in the previous Python example. To reduce flicker in the time lapse video, the average brightness from the last ten or twenty images was used.

Since the camera used had an infrared filter and the light level was low during the night, a brightness threshold was used to avoid storing images in very dark conditions.

Installing the scripts

To install the scripts, type:

The time lapse program can be run with the default settings:

or the available options can be listed:

When the time lapse program runs, it writes the pictures into the ~/pictures directory.

To start the time lapse program when the Raspberry Pi boots type:

and add

Then save the file and exit nano.

Making the movie File

After running the time lapse program for a long time, the photographs should be assembled into a movie.

This can be done very easily with mencoder:

This command uses all of the jpg files in the present working directory and assembles them into a movie. A sound track can be added to the movie, using an existing audio file:

Post-processing

The movie can look a bit too grey. To create more contrast, PIL's image manipulation capabilities can be used. The greyscale histogram of a single image can be plotted using Python and matplotlib:

The matplotlib package can also be used to plot the histograms of many images at once:

This example reads all of the .jpg files in the present working directory. In the resulting image each horizontal line of pixels is one image in the time lapse. The brightness of a pixel indicates how many pixels in the original image have a given intensity.

Some of the images captured were slightly grey. This implies that there is not very much contrast, because most of the pixel values are clustered in the middle of the histogram. In these cases, there were no completely black pixels and only a few completely white pixels. The image at the bottom left of this page illustrates is an example grey image.

To improve the balance, the image histogram can be used histogram and stretched out to fill the whole range (from 0 to 256). The first step is to find the bounds a and b:

where a and b defined such that 97% of the pixels are brighter than a and 97% are darker than b. Now a and b can be used to stretch the histogram:

where the eval function applies the function given within the parentheses to each pixel in the image and lambda is an easy way to make a simple function. For example, the following code snippet prints 12.

The histograms above are for the original (green) and levelled image (blue). The histogram for the levelled image is quite spread out. It is also very jagged, because the stretching removes many possible pixel values. Fortunately, this is not very visible in the levelled image. In practice, the bounds `a` and `b` were based on a rolling average from nearby pictures, such that there were no dramatic changes. The final levelled image is shown at the bottom right of this page.

The techniques discussed in this section can be found in the deflicker. py script. Type:  

for a list of available options. The script reads images that are in the present working directory.