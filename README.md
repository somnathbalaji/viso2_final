viso2
==========
ROS Stack containing a wrapper for libviso2, a visual odometry library. 
http://www.ros.org/wiki/viso2 for the list of contained packages.
***

In order to change camera topic, change the arg from default="/sam/perception/camera_down" to preferred camera topic

### Frames

* This launch file currently uses the default frames (base_link). If in case these frames donot work on SAM, try changing the frames to UTM

### Image Transport

* image_transport gives a raw image output which will be used by image_proc. The camera topics that you give initially will get reflected here
* In case of any doubt, refer this page http://wiki.ros.org/image_transport

### How to execute (viso2-mono_odometry)

* To execute omnidirectional Libviso2 make sure you have a camera node publishing over ROS(in this case, there is already image_proc node.To know more, read this page http://wiki.ros.org/image_proc).
* After that you can use the demo launch file that we provide in the following way:
```
roslaunch viso2_ros sam_mono.launch
```

* This launch file contains all the nodes required to run viso2 on SAM.
* This launch file runs only the mono odometry on SAM.
* There's already a default calibration.txt file for SAM configured based on image size of SAM's camera model (1024x1360).
* Make sure that first you set the **file calibration path** correctly by changing the `calib_path` parameter.

## Note

* Also you can edit/add the default parameters that Libviso2 use (don't forget that camera height and pitch are mandatory to scale calculation).


## Omnidirectional version

### How to execute (viso2-omnidirectional version of mono_odometry)

```
roslaunch viso2_ros sam_mono_onmni.launch
```

* This package contains an additional version of the original Libviso2 that works with a **monocular omnidirectional camera system**.

### Dependencies

* The only additional dependency of this version is the camera calibration toolbox [Ocamcalib](https://sites.google.com/site/scarabotix/ocamcalib-toolbox) for Matlab.
  - Instead of using a normal pinhole camera calibration model, the method uses the unified camera model proposed by Davide Scaramuzza.
  - Download the toolbox from [here](https://sites.google.com/site/scarabotix/ocamcalib-toolbox/ocamcalib-toolbox-download-page), put it in your Matlab workspace and execute the `ocam_calib` command to run the application.
  - After calibrating the camera save the generated text file that will be used by the method.

* There's also a rviz configuration file created while testing on stonefish. Need to check whether it'll work in realtime.# viso2_SAM

