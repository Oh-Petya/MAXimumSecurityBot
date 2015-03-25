MAXimumSecurityBot
==================

<a href="http://people.cornellcollege.edu/smikell15/MAX/">Here is a website we created for this package!</a>

Our package comes with five different scripts that need to be running: bark.py, fire.py, follow.py, move.py, and tracking.py. move.py allows the robot to autonomously navigate an area it is placed in, tracking.py uses kinect sensor data coupled with openni software to detect persons. If it detects a person, it will publish to move.py to get the robot to stop autonomously navigating, and begin following. follow.py will then begin to follow the person detected by tracking.py and will then publish to bark.py. bark.py will then continue to play barking noises in attempt to ward off the person, then it will publish to fire.py. fire.py will then continously fire at the person while follower.py is still running.

Currently the code does not work properly. We have not gotten openni_tracker to publish info correctly. It does not correctly connect to tf to subscribe to its frames. In other words, the info always publishes that a person is not being tracked, even when tf frames are correctly being published. move.py has not been finished to only run if tracker.py publishes False. fire.py does not work yet, since it needs to be run as root, but also requires you to rosrun it. As of right now, we can't do both. It is assumed that you can do this by having the entire packge installed in root. This is still an ongoing project as of this moment.

Resources you will need for this code to work is: sound_play package, openii_tracker package. You will also need a usb missile launcher, and you will need to install a few things for it from https://www.cs.hmc.edu/twiki/bin/view/Robotics/SettingUpTheSystem just scroll down to the section mentioning the missile launcher.

In order to run the code, you must bring up the TurtleBot first. This is best accomplished by launcher the 3dsensor located in turtlebot_brinup. With the 3dsensor running, run openni_tracker in the openni_tracker package. Then, run tracking.py in the central package to begin the tracking node which publishes a true/false base on if a person is currently being tracked. Then you must launch soundplay_node.launch.

Then you can run the python scripts in any order. Though move.py would be preferred to be run last, since it will cause the robot to begin moving.
