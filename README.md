# The localization package

This package hosts the launch scripts for [robot_localization](http://wiki.ros.org/robot_localization) that work with the CITrack.
There exists one robot_localization node for every marker.
One node fuses all tracking hypotheses for a single maker `/<tracker>/cam/odom/<ID>` and publishes the result to `/odometry/filtered/<ID>`.

Multiple instances for a launch file can be created by the following bash script:

```
prefix='<include file="$(find localization)/launch/generic_ekf.launch"><arg name="id" value="'
sufix='" /><arg name="tracker" value="$(arg tracker)"/></include>'
for i in $(seq 0 63); do echo ${prefix}${i}${sufix};done
```
