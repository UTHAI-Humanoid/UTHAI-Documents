[http://support.robotis.com/en/techsupport\_eng.htm\#product/thormang3\_main.htm](http://support.robotis.com/en/techsupport_eng.htm#product/thormang3_main.htm)

# Joint Name & ID map

##### U2D\_CHANNEL2

| ID | JointName |
| :---: | :---: |
| 1 | l\_leg\_hip\_y |
| 2 | l\_leg\_hip\_r |
| 3 | l\_leg\_hip\_p |
| 4 | l\_leg\_kn\_p |
| 5 | l\_leg\_an\_p |
| 6 | l\_leg\_an\_r |

##### U2D\_CHANNEL3

| ID | JointName |
| :---: | :---: |
| 11 | r\_leg\_hip\_y |
| 12 | r\_leg\_hip\_r |
| 13 | r\_leg\_hip\_p |
| 14 | r\_leg\_kn\_p |
| 15 | r\_leg\_an\_p |
| 16 | r\_leg\_an\_r |

## High Performance and Advanced Features

* Default walking speed: 100.0 cm/sec.
* Management controller: Nucleo
* 20 actuator modules \(6 DoF leg x2 + 3 DoF arm x2 + 2 DoF neck\)
* Actuators with durable metalic gear \(Dynamixel EX-106+\)
* 1Mbps high-speed Dynamixel bus for joint control
* 3-axis gyro, 3-axis accelerometer

## Actuator Spec Specifications

| Description | EX-106+ |
| :---: | :---: |
| Weight | 82g |
| Dimension | 28.5mm x 25mm x 43mm |
| Gear Ratio | 333:1 |
| Stall Torque | 4.5 N.m |
| Stall Current | 2.3 A |
| No Load Speed | 55 RPM |
| Protocol | 1.0,2.0 |

## The Mechanical Design of Uthai Humnaoid

ได้ตัวอย่างการออกแบบมาจากหุ่นยนต์ตัวไหนก็ไม่รู้ หาก่อน

### Design concept

หุ่นยนต์ถูกออกแบบโดย แท้และเบิร์ด ตามคอนเซปด้านล่างนี้

* น้ำหนักเบา แข็งแรง ทนทาน
* ง่ายต่อการพัฒนาต่อยอด

### Specifications of Uthai Humanoid

| Description | Uthai Robot 1-A |
| :---: | :---: |
| Hight | About 1030mm |
| Weight | About 3.5kg |
| Hight of CoM | 800mm |
| Feet size | 150 x 150 mm |
| DOF | 12 xxxx |
| Actuator | Dynamixel EX-106+ |
| Main Controller | Odroid xxxx |
| Sub Controller | Nucleo F411RE 100MHz ARM Cortex xxxx |
|  |  |
| Sensor | 3-Axis Gyroscope 3-Axis Accelerometer 3-Axis Magnetometer |
| Power Source | LIPO or Switching Power Supply |
| Developement Environment | OS: Linux, ROS, Python, C++, MATLAB, Dynamixel SDK |
| Networking | Eternet WiFi |

### DH-Parameter of Uthai Humaoid

| link\(i\) | a\(i\) | al\(i\) | d\(i\) | theta\(i\) |
| :---: | :---: | :---: | :---: | :---: |
| 1 | 0 | pi/2 | 0 | pi+\theta |
| 2 | 0 | pi/2 | 0 | pi+theta\(1\) |
| 3 | 0 | pi/2 | 0 | pi+theta\(1\) |
| 4 | 0 | pi/2 | 0 | pi+theta\(1\) |
| 5 | 0 | pi/2 | 0 | pi+theta\(1\) |
| 6 | 0 | pi/2 | 0 | pi+theta\(1\) |
| 7 | 0 | pi/2 | 0 | pi+theta\(1\) |

## Physical Properties

### Links

1. Measurement overview

![](/assets/measurement overview.png)

| body | x | y | z |
| :--- | :--- | :--- | :--- |
| ground origin | - | - | 807.5 |
| origin | 0 | 0 | 170.5 |

| Left Leg | x | y | z | Right Leg | x | y | z |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| base - 1 | 0 | 93 | -18 | base - 11 | 0 | -93 | -18 |
| 1 - 2 | 57 | 0 | -75 | 11 - 12 | 57 | 0 | -75 |
| 2 - 3 | -57 | 33 | 0 | 12 - 13 | -57 | 33 | 0 |
| 3 - 4 | 0 | 60 | -300 | 13 - 14 | 0 | -60 | -300 |
| 4 - 5 | 0 | -60 | -300 | 14 - 15 | 0 | 60 | -300 |
| 5 - 6 | 57 | -33 | 0 | 15 - 16 | 57 | 33 | 0 |
| 6 - foot | -57 | 0 | -87 | 16 - foot | -57 | 0 | -87 |

### Mass & Inertia

#### Whole robot

Mass = 5.0 \[kg\]

#### Body

|  |  |  |  |  |  |  |  |  |  |  |  |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| ID | JointName | Mass \[kg\] | x | y | z | xx | xy | xz | yy | yz | zz |
|  |  |  |  |  |  |  |  |  |  |  |  |

#### Left Leg

#### Right Leg

### Joint & Angle Limit

![](/assets/joint and angle limit.png)

#### Left Leg Joint

![](/assets/l_leg_joint_limit.png)

| ID | JointName | Range \(degrees\) |
| :--- | :--- | :--- |
| 1 | l\_hip\_yaw | -150 to 150 |
| 2 | l\_hip\_roll | -30 to 45 |
| 3 | l\_hip\_pitch | -40 to 85 |
| 4 | l\_knee\_pitch | -150 to 30 |
| 5 | l\_ankle\_pitch | -85 to 40 |
| 6 | l\_ankle\_roll | -35 to 90 |

#### Right Leg Joint

![](/assets/r_leg_joint_limit.png)

| ID | JointName | Range \(degrees\) |
| :--- | :--- | :--- |
| 11 | r\_hip\_yaw | -150 to 150 |
| 12 | r\_hip\_roll | -30 to 45 |
| 13 | r\_hip\_pitch | -40 to 85 |
| 14 | r\_knee\_pitch | -150 to 30 |
| 15 | r\_ankle\_pitch | -85 to 40 |
| 16 | r\_ankle\_roll | -35 to 90 |



