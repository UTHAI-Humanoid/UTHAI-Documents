## UTHAI Humanoid ROS workflow

### Dynamixel Controllers

ให้สร้าง package ขึ้นมาก่อน

```
$ cd ~/catkin_ws/src/UTHAI-Humanoid
$ catkin_create_pkg uthai_bringup
```

#### Contents

1. Step1 : Specify controller parameters
2. Step2 : Cteate a launch file
3. Step3 : Start the controller
4. Step4 : Moving the motor

หลังจากที่เราได้สร้าง package uthai\_bringup ขึ้นมาแล้ว

```
$ roscd uthai_bringup
```

#### Step1 : Specify controller parameters

tilt.ymal

```
tilt_controller:
    controller:
        package: dynamixel_controllers
        module: joint_position_controller
        type: JointPositionController
    joint_name: tilt_joint
    joint_speed: 1.17
    motor:
        id: 2
        init: 512
        min: 0
        max: 4095
```

** Note : **ต้องเช็คในแน่ใจก่อนว่า motor id ที่ตั้งไปตรงกับ motor จริงๆ ที่ต่ออยู่

ในส่วนของไฟล์ .ymal เราจะสนใจตรงส่วนของ "motor" ที่มีทั้งหมด 4 parameters: `id`, `init`,`min`,`max`

* id : เป็นค่าที่เราจะตั้งขึ้นมาเป็นเลขอะไรก็ได้ ที่ตรงกับมอเตอร์ที่เราใส่เข้าไป โดยห้ามซ้ำกัน
* init : เป็นค่า initial position สำหรับมอเตอร์โดยมีค่าตั้งแต่ 0 - 4095 โดยหมุนได้ 360 องศา ตัวอย่างเช่นค่า 1365 จะเท่ากับ 120 องศา
* min : เป็นค่าลิมิตมุมน้อย ที่มอเตอร์สามารถเคลื่อนที่ได้ ค่าอยู่ในช่วงเดียวกับ init
* max : เป็นค่าลิมิตมุมมาก ที่มอเตอร์สามารถเคลื่อนที่ได้ ค่าอยู่ในช่วงเดียวกับ init

#### Step2 : Create a launch file

ต่อไปเราจะต้อง load parameter เข้าไปใน controller

start\_tilt\_controller.launch

```
<launch>
    <!-- Start tilt joint controller -->
    <rosparam file="$(find uthai_bringup)/config/tilt.ymal" command="load"/>
    <node name="tilt_controller_spawner" pkg="dynamixel_controllers" type="controller_spawner.py" 
    args="--manager=dxl_manager 
    --port pan_tilt_port 
    tilt_controller" output="screen"/>
</launch>
```

#### Step3 : Start the controller

ก่อนจะรันไฟล์ start\_tilt controller.launch ที่เพิ่งสร้างขึ้นมาให้เรารันไฟล์ controller manager d่อน

```
$ roslaunch uthai_bringup controller_manager.launch
```

หลังจากนั้นก็รันไฟล์ที่เราเพิ่งสร้างขึ้นมา

```
$ roslaunch uthai_bringup start_tilt_controller.launch
```

เมื่อรันแล้ว node ตัวนี้จะโหลด controller แล้วก็ปิดตัวเองลง

```
process[tilt_controller_spawner-1]: started with pid [7877]
[INFO] [1518003778.863921]: pan_tilt_port controller_spawner: waiting for controller_manager dxl_manager to startup in global namespace...
[INFO] [1518003778.874709]: pan_tilt_port controller_spawner: All services are up, spawning controllers...
[INFO] [1518003778.971237]: Controller tilt_controller successfully started.
[tilt_controller_spawner-1] process has finished cleanly
log file: /home/sweilz/.ros/log/03d8727e-0bfc-11e8-8f0a-4851b7c68fd6/tilt_controller_spawner-1*.log
all processes on machine have died, roslaunch will exit
shutting down processing monitor...
... shutting down processing monitor complete
done
```

ถ้าทุกอย่างถูกต้องจะเห็นคำว่า "Controller tilt\_controller successfully started." ใน Terminal

ต่อไป เราก็ลอง list topic ออกมาดู

```
$ rostopic list
```

จะเห็นประมาณนี้

```
/motor_states/pan_tilt_port
/tilt_controller/command
/tilt_controller/state
```

`/tilt_controller/command` topic นี้จะเป็นการเซทมุมของมอเตอร์ มี msg\_type เป็น std\_msgs/Float64  
`/tilt_controller/state` topic นี้จะให้ค่าสถานะปัจจุบันของมอเตอร์ออกมาโดยมี msg\_type เป็น dynamixel\_msgs/JointState

ต่อไป เราก็ลอง list service ออกมาดู

```
$ rosservice list
```

จะเห็นประมาณนี้

```
/dxl_manager/pan_tilt_port/restart_controller
/dxl_manager/pan_tilt_port/start_controller
/dxl_manager/pan_tilt_port/stop_controller
/tilt_controller/set_compliance_margin
/tilt_controller/set_compliance_punch
/tilt_controller/set_compliance_slope
/tilt_controller/set_speed
/tilt_controller/set_torque_limit
/tilt_controller/torque_enable
```

จะใช้สำหรับในการแก้ไขปรับแต่ง paremeters ต่างๆ เช่น ความเร็ว ลิมิตแรงบิด

#### Step4 : Moving the motor

ต่อไปจะเป็นการขับเคลื่อนมอเตอร์เราจะใช้การ publish angle ไปยัง /tilt_controlle_/command topic

```
$ rostopic pub -1 /tilt_controller/command std_msgs/Float64 -- 1.5
```

จากนั้นจะเห็นว่ามอเตอร์ขยับได้แล้ว

