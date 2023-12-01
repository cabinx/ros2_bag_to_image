# ros2_bag_to_image
  Opens, reads, extracts and saves sensor_msgs/msg/Image or sensor_msgs/msg/CompressedImages from Ros2 bag, works on ros2 foxy.
  
  This package is modified from https://github.com/MapIV/ros2_bag_to_image, which works on ros2 rolling.

  How to launch:
  ```
  ros2 launch rosbag2_to_image bag_to_image.xml input/path:=your_bag_path input/topics:=image_topic output/path:=image_saved_path
  ```

  An example:
  ```
  ros2 launch rosbag2_to_image bag_to_image.xml input/path:='/home/pcl-02/yolov5_ros2/bag/car1' input/topics:="['/camera/color/image_raw']" output/path:='/home/pcl-02/yolov5_ros2/bag/car1/image'
  ```
