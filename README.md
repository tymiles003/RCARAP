# SP-RCARAP
Supporting Remote Collaboration with Augmented Reality and Architectural Plans (Summer semester 2018)

# Goal
The goal of the study project "Supporting remote collaboration with Augmented Reality and architectural plans" is to use depth cameras (Intel RealSense D435) in combination with a tabletop system to project the hand of a person pointing on a plan to the second tabletop system in a different room/building. This approach supports architects, for example in decision making processes or discussions. It includes depth information which can be useful in different applications, for example indicating the height of a wall.

# Technologies used
* [Node.js](https://github.com/nodejs/node)
* [Electron](https://github.com/electron)
* [Socket.io](https://github.com/socketio)
* [OpenCV4nodejs](https://github.com/justadudewhohacks/opencv4nodejs)
* [librealsense](https://github.com/IntelRealSense/librealsense)

# How to Run
1. Run npm install
2. Run ./node_modules/.bin/electron-rebuild
3. Run npm start

# How to use
Before you start the application make sure that both machines have the same screen resolution.  
The application has to be started on both machines. One machine (Machine A) will create a session, the other one (Machine B) will join the session by typing in the IP address of Machine A. After the connection is established the calibration has to activated by clicking "Calibrate" on Machine A (pleae make sure that the light in the room is turned off). That opens the calibration window in Machine B with a countdown of 20 seconds. Within this time the architectural plan has to be align according to the green calibration squares in a way that the bottom left corner of the plan is covered by the bottom left calibration square. After the time is up the calibrate button of Machine B has to be clicked to repeat the process for table setup at Machine A. Afterwards the application is ready to use (Please turn on the lights again). Now you can point on both plans and the hand will be transmitted to the other tabletop system. Additionally the height of the hand above the plan is displayed as well as the fingertips which are recognized.

# Drawbacks
* Computationally intensive so a good processor (>= i5) is required to run it appropriately (for example logging the coordinates of the hands)
* Calibration is dependend on brightness of the room, it has to be dark so the specific color of the calibration squares can be captured by the cameras correctly
* Hand recognition is dependend on brightness of the room to have a better detection of the hands
* Depth quality of the Intel RealSense D435 is not very good (fluctuation of depth values between 1-3 centimeters)
* Rigidness of the tabletop setup
* Have to recalibrate if the plan gets mis-aligned in between once the calibration is done at the beginning

# Future work
* Audio transmission
* Improvement of calibration so it is independend of light
* Adjustment of tabletop setup (being able to change angle of projector or mirror directly)
* Inclusion of drawing on the plan (annotations) or virutal highlighting of architectural elements
* Recognition of different persons by using gloves with different colors or any other feasible method like wrist bands or QR-code
* Implementation of hand gesture recognition

# Installation issues
* Make sure that the prerequisites of the Intel RealSense SDK wrapper for Node.js are fulfilled. You can find them here: https://github.com/IntelRealSense/librealsense/tree/master/wrappers/nodejs
* Since the installation of the node packages produces long pathnames install it on the desktop or at another location with short paths
* If an error appears concerning missing C++ header files, e.g. ```atlcomcli.h``` or ```atlstr.h``` , please use the developer console  for VS2017 or VS2015, depending on which version of Visual Studio is used.

