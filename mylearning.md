# プログラムを把握する

## 環境とロボットの配置

- [`src/turtlebot3_simulations/turtlebot3_gazebo/launch/turtlebot3_world.launch`](https://github.com/masachika-kamada/ros-slam-first/blob/main/src/turtlebot3_simulations/turtlebot3_gazebo/launch/turtlebot3_world.launch) で配置
- `empty_world.launch` に対してパラメータを `world_name="$(find turtlebot3_gazebo)/worlds/turtlebot3_world.world"` と設定
- 以下のプログラムで環境の確認が可能
  ```
  roscd turtlebot3_gazebo/worlds
  export GAZEBO_RESOURCE_PATH=$GAZEBO_RESOURCE_PATH:`pwd`
  roslaunch gazebo_ros empty_world.launch world_name:=turtlebot3_world.world
  ```
- モデル（Turtlrbot3）の配置に関してはイマイチわかっていない

## Turtlebot3 の制御

- [`src/turtlebot3/turtlebot3_teleop/launch/turtlebot3_teleop_key.launch`](https://github.com/masachika-kamada/ros-slam-first/blob/main/src/turtlebot3/turtlebot3_teleop/launch/turtlebot3_teleop_key.launch) の内容はこんな
  ```
  <node pkg="turtlebot3_teleop" type="turtlebot3_teleop_key" name="turtlebot3_teleop_keyboard" output="screen"></node>
  ```
- [turtlebot3_teleop_keyboard](http://wiki.ros.org/turtlebot3_teleop) という ROS API があってそれで動かしているっぽい
> ノードについての理解が浅い

## GMapping で SLAM

- [`src/turtlebot3/turtlebot3_slam/launch/turtlebot3_slam.launch`](https://github.com/masachika-kamada/ros-slam-first/blob/main/src/turtlebot3/turtlebot3_slam/launch/turtlebot3_slam.launch) に対して `slam_methods:=gmapping` とパラメータを与えている

> [このディレクトリ](https://github.com/masachika-kamada/ros-slam-first/tree/main/src/turtlebot3/turtlebot3_slam/launch) に川嶋修論の手法がすべて揃っているし、cartographerも入っているじゃん。
