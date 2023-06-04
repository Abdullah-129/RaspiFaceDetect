# Face-Detection-on-raspberrypi-with-openCV
Setting Up Open-CV and Facial Recognition From Scratch
This will be a long stream of terminal commands forewarning. This will also take a substantial amount of time. I am currently testing out another method to make this process faster

This is an in-depth procedure to follow to get your Raspberry Pi to install Open-CV. Turn on a fresh version of Raspberry Pi running Raspberry Pi 'Buster' OS and connect it to the Internet.

Open up the Terminal by pressing the Terminal Button found on the top left of the button. Copy and paste each command into your Pi’s terminal, press Enter, and allow it to finish before moving onto the next command. If ever prompted, “Do you want to continue? (y/n)” press Y and then the Enter key to continue the process.

* pip install picamera[array]
* Sudo apt-get update
* Sudo apt-get upgrade
* sudo apt install cmake build-essential pkg-config git
* sudo apt install libjpeg-dev libtiff-dev libjasper-dev libpng-dev libwebp-dev libopenexr-dev
* sudo apt install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libxvidcore-dev libx264-dev libdc1394-22-dev libgstreamer-plugins-base1.0-dev libgstreamer1.0-dev
* sudo apt install libgtk-3-dev libqtgui4 libqtwebkit4 libqt4-test python3-pyqt5
* sudo apt install libatlas-base-dev liblapacke-dev gfortran
* sudo apt install libhdf5-dev libhdf5-103
* sudo apt install python3-dev python3-pip python3-numpy


We must now expand the swapfile before running the next set of commands. To do this type and enter into the Terminal the following line.


* sudo nano /etc/dphys-swapfile


 he change the number on CONF_SWAPSIZE = 100 to CONF_SWAPSIZE=2048. Having done this press Ctrl-X, Y, and then Enter Key to save these changes. This change is only temporary and we will be changing it back. To have these changes affect anything we must restart the swapfile by entering the following command to the terminal. Then we will resume Terminal Commands as normal.
 
 
* sudo systemctl restart dphys-swapfile
* git clone https://github.com/opencv/opencv.git
* git clone https://github.com/opencv/opencv_contrib.git
* mkdir ~/opencv/build
* cd ~/opencv/build
* cmake -D CMAKE_BUILD_TYPE=RELEASE \
* -D CMAKE_INSTALL_PREFIX=/usr/local \

-D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \

-D ENABLE_NEON=ON \

-D ENABLE_VFPV3=ON \

-D BUILD_TESTS=OFF \

-D INSTALL_PYTHON_EXAMPLES=OFF \

-D OPENCV_ENABLE_NONFREE=ON \

-D CMAKE_SHARED_LINKER_FLAGS=-latomic \

-D BUILD_EXAMPLES=OFF ..

* make -j$(nproc)

This | make | Command will take over an hour to install and there will be no indication of how much longer it will take. It may also freeze the monitor display. Be ultra patient and it will work. Once complete you are most of the way done. Then we will resume terminal commands.

* sudo make install
* sudo ldconfig
* pip install face-recognition --no-cache-dir

This | pip install face-recognition| Command will take over 40 mins to install and there will be no indication of how much longer it will take. Be ultra patient and it will work. Once complete you are most of the way done. Then we will resume terminal commands.

* pip install imutils

We must now return the swapfile before running the next set of commands. To do this type into Terminal this line.

* sudo nano /etc/dphys-swapfile

The change the number on CONF_SWAPSIZE = 2048 to CONF_SWAPSIZE=100. Having done this press Ctrl-X, Y, and then Enter Key to save these changes. This returns the Swapfile to normal. To have these changes affect anything we must restart the swapfile by entering the following command to the terminal. Then we will resume terminal Commands as normal.

* sudo systemctl restart dphys-swapfile
* git clone {THIS REPO}

# Working of this Repo
Save your photo's folder containing your name and save that folder into dataset folder.
The pictures will be used by the Python code | train_model.py |. Any pictures in the dataset folder location will be analysed by this code when we run it. Open up a new terminal using the black console button on the top left and type the following pressing enter after each line. 

* cd facial_recognition
* python train_model.py

 # Demonstration
 
So, let us give this a go. To run example code that will identify faces and if they find a face trained will write their name next to it. Start by opening a new terminal the same as before. Then type the following and press enter after each step.

* cd facial_recognition
* python facial_req.py

It will take ~5 Secs to boot up and run.

Then you will see a small window pop up with a live stream of the Raspberry Pi Camera. Aim the camera at your face and if it puts a yellow box around your head and names you correctly, you have done it! The Raspberry Pi Camera is searching for faces and when it has been supplied with one it will draw a square box around the face. It will also determine if it is a known face displaying Unknown if it is not a known face and the name of the person if it is.







