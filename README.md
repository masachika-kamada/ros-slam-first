# ros-slam

## ■ 依存パッケージのインストール

- ubuntu 20.04 で ROS Noetic 使っているのに Melodic の依存パッケージでいいのか疑問だが。

```
sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan ros-melodic-rosserial-arduino ros-melodic-rosserial-python ros-melodic-rosserial-server ros-melodic-rosserial-client ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro ros-melodic-compressed-image-transport ros-melodic-rqt-image-view ros-melodic-navigation
```

## ■ catkin build

```
catkin b
```

- `Could NOT find SDL (missing: SDL_LIBRARY SDL_INCLUDE_DIR) ` のエラーが出たら以下を実行（[参考](https://github.com/ros-planning/navigation/issues/579)）

```
sudo apt-get install libsdl-image1.2-dev libsdl-dev
```

## ■ 環境変数の自動反映のための設定

- [ここ](https://github.com/masachika-kamada/ros-slam-first/blob/main/env_setup.md) を参照して direnv の設定を行う

## ■ Gazebo での動作確認

1. RViz での動作確認
  - ターミナル①
    ```
    roscore
    ```
  - ターミナル②：RViz で Turtlebot3 が出現することを確認
    ```
    roslaunch turtlebot3_fake turtlebot3_fake.launch
    ```
  - ターミナル③：WASDX キーで RViz 上の Turtlebot3 が動くことを確認（ゴール）
    ```
    roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
    ```
  ![rosgraph_fake](https://user-images.githubusercontent.com/63488322/203759396-e913d94b-8de7-496c-9d5b-ecc8830caac7.png)
2. Gazebo での動作確認
  - ターミナル①
    ```
    roscore
    ```
  - ターミナル②：Gazebo で Turtlebot3 が出現することを確認
    ```
    roslaunch turtlebot3_gazebo turtlebot3_world.launch
    ```
  - ターミナル③：WASDX キーで Gazebo 上の Turtlebot3 が動くことを確認（ゴール）
    ```
    roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
    ```
  ![rosgraph_gazebo](https://user-images.githubusercontent.com/63488322/203759402-4849fb04-254b-4864-8fda-caed2bebafc9.png)

## ■ GMapping の動作確認

- ターミナル①
  ```
  roscore
  ```
- ターミナル②：Gazebo で Turtlebot3 を表示
  ```
  roslaunch turtlebot3_gazebo turtlebot3_world.launch
  ```
- ターミナル③：WASDX キーで Gazebo 上の Turtlebot3 が動かせるように
  ```
  roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
  ```
- ターミナル④：GMapping のノードを立ち上げ SLAM で地図が生成されることを確認（ゴール）
  ```
  roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
  ```
![rosgraph_gmapping](https://user-images.githubusercontent.com/63488322/203759405-c54b8c62-5354-4382-a662-eb8c0c890e74.png)

## ■ 参考

- [ROS MelodicでTurtlebot3をGazeboで動かしてついでにSLAMする](https://qiita.com/protocol1964/items/1e63aebddd7d5bfd0d1b)
