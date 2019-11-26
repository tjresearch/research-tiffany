Title: Visual Identification of Handicap Parking Passes in Video Footage of Cars

Project Overview: I am creating a program that uses the “You Only Look Once” (YOLO) object detection system to visually identify handicap
parking placards in video footage of cars parking in a handicap parking space. This program can hopefully help prevent the illegal use of
handicap parking spaces by individuals who do not display a handicap parking placard in their car.

Requirements/Dependencies (with links for installation instructions):
1. darknet (requirement for YOLO): https://pjreddie.com/darknet/install/
2. CUDA (allows you to run YOLO with GPU): https://developer.nvidia.com/cuda-downloads
3. OpenCV (allows you to run YOLO on video footage): https://docs.opencv.org/master/d7/d9f/tutorial_linux_install.html
4. Approximately 50 images of handicap parking passes in cars to use to make the training and test set
4. Using a Linux system is recommended, but this process is still possible on a Windows system

Specific Steps:
1. Use OpenCV Python libraries to change the images to black and white using Gaussian Thresholding. This will allow the final program
to identify handicap parking placards of multiple different colors.
2. Use the BBox Label Tool to draw a box around a handicap parking pass in images of cars.
3. Convert the coordinates returned by the BBox Label Tool to the correct YOLO format. 
4. Separate these files into a training set and a test set.
5. Create two configuration files for YOLO: obj.data and obj.names. Adjust yolo-obj.cfg (the third configuration file) to match your
settings and number of classes.
6. Use these 3 configuration files and the training set to train YOLO to identify handicap parking passes. Do this by typing the following
command into the terminal: darknet.exe detector train cfg/obj.data cfg/yolo-obj.cfg darknet19_448.conv.23
7. Test the accuracy of your program with the test set.
8. Use the pre-trained version of YOLO to identify cars in video footage. If a car is present in the video footage for an extended amount
of time, assume it is a parked car. Only look for handicap parking passes in parked cars.
9. Code methods that record statistics such as the percentage of cars that park illegally in a specific handicap parking space each day.
