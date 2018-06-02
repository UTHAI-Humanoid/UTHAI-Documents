# Introduction

ฮิวมานอยด์เป็นหุ่นยนต์ที่ถูกสร้างให้มีลักษณะคล้ายมนุษย์ เพื่อทำงานทดแทน หรือทำงานร่วมกับมนุษย์ได้อย่างเป็นมิตร ในปัจจุบันงานวิจัยหุ่นยนต์ฮิวมานอยด์เป็นสิ่งที่สถายันทั่วโลกให้ความสนใจในการพัฒนามากขึ้น มีทุนสนับสนุนและงานแข่งขันอย่างต่อเนื่อง เช่น Rescue Robot, DARPA Robotics Challenge, Robocup ในโปรเจคนี้จะเน้นไปในส่วนของงานวิจัยที่เกี่ยวข้องกับการสร้างแพลตฟอร์มขึ้นมาเพื่อเป็นเครื่องมือในการพัฒนาแอพลืเคชั่นต่างๆ ให้มีความสะดวก โดยได้รวบรวมเทคนิคทางวิทยาการหุ่นยนต์ที่มีความซับซ้อน เช่น การคำนวณจลศาสตร์และพลศาสตร์ของหุ่นยนต์ การประมาณค่าสถานะของระบบ การวางแผนการวางเท้าของหุ่นยนต์ และอื่นๆ เอาไว้แล้ว

## What is UTHAI Humanoid?

เนื่องจากการพัฒนาหุ่นยนต์ฮิวมานอยด์ มีความยุ่งยาก และใช้ทรัพยากรณ์ในการเริ่มต้นสูง ดังนั้นเรา นักศึกษา FIBO จึงร่วมกลุ่มกันเพื่อพัฒนาแพลตฟอร์มกลางเพื่อให้ผู้ที่สนใจเริ่มต้นการศึกษาและพัฒนาแอพลิเคชั่นของหุ่นยนต์ฮิวมานอยด์ได้ เช่น การพัฒนาให้เป็นหุ่นยนต์ช่วยเหลือผู้สูงอายุ หุ่นยนต์บริการต้อนรับ หุ่นยนต์ทำอาหาร รวมไปถึงหุ่นยนต์ที่ทำงานในสถานที่อันตราย อีกทั้ง แพลตฟอร์มกลางนี้จะเป็นต้วอย่างที่เหมาะกับการศึกษา ค้นคว้า วิจัย และพัฒนาเทคโนโลยีที่เกี่ยวข้องกับหุ่นยนต์ฮิวมานอยด์ ด้วยจุดประสงค์นี้จึงทำให้เกิด

UTHAI \(Universal Template Humanoid Algorithym Interface\) อุทัยฺวมานอยด์ แพลตฟอร์มฮิวมานอยด์ที่มีราคาถูก มีความเร็วในการประมวลผลสูง มีเซนเซอร์วัดค่าต่างๆ เหมาะสำหรับการศึกษา ค้นคว้า วิจัย และพัฒนาต่อยอด

## Overview

เริ่มต้นจากระบบ Paht planning ซึ่งจะค้นหาเส้นทางการเคลื่อนที่ทั้งการเดินและการขยับของแต่ละข้อต่อ โดยใช้ AI เทคนิค A\* Algorithm จากนั้นจึงส่งต่อข้อมูลไปให้กับส่วนของ ระบบควบคุม ที่ถูกออกแบบด้วยวิธี Model-based design โดยใช้สมการการเคลื่อนที่ของ Newton-Euler และรักษาเสถียรภาพการเดินด้วยการควบคุมตำแหน่งของ Center of Mass สำหรับการเดินแบบสถิต \(Static walking\) และการควบคุมตำแหน่งของ Zero Moment Point สำหรับการเดินแบบพลวัต \(Dynamic walking\)

ในการออกแบบหุ่นยนต์จะใช้เทคนิคการ Simulation บน Gazebo\(ROS\) ซึ่งเป็นเครื่องมือที่ช่วยในการสื่อสารข้อมูลระหว่างระบบต่างๆ เพื่อตรวจสอบความถูกต้อง ก่อนนำไปพัฒนาเป็น Embedded System ที่ใช้ Embedded Computer ซึ่งถูกติดตั้งในหุ่นยนต์ โดยตัวหุ่นยนต์จะถูกออกแบบ และทดสอบการรับแรง ด้วยเทคนิค Finite Element Analysis ด้วยโปรแกรม Solidworks จากนั้นจึงขึ้นรูปด้วยการใช้ Carbon fiber และ ABS\(3D printer\)

สำหรับการควบคุมแบบ Realtime เราได้ติดเซนเซอร์หลายชนิดไว้ภายในตัวหุ่นยนต์ เช่น IMU, Force sensor, Encoder, Temperature, Torque ซึ่งจะช่วยให้สามารถนำค่าของเซนเซอร์หลายๆ ชนิดมารวมกันสำหรับ การประมาณค่าสถานะของระบบโดยใช้เทคนิคของ Extended Kalman Filter\(EKF\) จะทำให้ได้ตำแหน่งของหุ่นยนต์ที่มีความแม่นยำมากยิ่งขึ้น เพื่อนำมาเป็นข้อมูลป้อนกลับในระบบควบคุมที่ได้ออกแบบไว้

## UTHAI Humanoid Team

* Jirad  Sreerattana-aporn   \[Hardware designer\]
* Chulaphat  Jirachai        \[System state estimater\]
* Jadsadakon  Tachaiwong     \[Hardware designer\]
* Peeraya  Pongpanyaporn     \[Control and Dynamic modeling\]
* Wuttipat  Chokanantasab    \[Robot Firmware\]
* Sirawat  Soksawatmakin     \[Motion and Path planing\]

## Speacial Thanks To

* Aj.Pi



## Package Contents

ส่วนประกอบสำคัญ

#### SOFTWARE :

1. Software Architecture `Chulaphat`

   * Version Control
     * Setting up Github
   * Network Protocol
     * Connecting SSH
   * System Environment
     * Operating System Set-up
       * Linux Tutorial
     * Software Set-up
       * MATLAB or other simulation software
       * Instruction for installing
   * Robot Operating System
     * Set up ROS Workspace
     * Background studies in using ROS
     * Background studies in simulation in ROS
     * Setting up Robot Class

2. Sensor `Wuttipat`

   * Encoders 
     * Background research on typical specs for encoders for humanoid
     * Background research on typical characteristics i.e. bandwidth, limits, resolution
     * Background studies in Encoders’ sensor model with humanoid’s dynamics
   * Inertial Measurement Unit \(IMU\)
     * Background research on the use of IMU in humanoid’s state estimators
     * Background studies in IMU’s sensor model with humanoid’s dynamics
   * Ground Contact Sensors
     * Background research on bipedal robot’s ground contact sensors
     * Selection of Sensors based on characteristics \(limit switches/ force sensors\)

3. State Estimators `Chulaphat`

   * Background research on humanoid’s state estimators
   * Background studies in Kalman Filter and Extended Kalman Filter
   * Integration between Encoders and IMU

4. Dynamics `Peeraya`

   * Background research in humanoid’s dynamics model
     * Studies hybrid nature of the dynamics
     * Studies the Poincare map
   * Review Serial Manipulator Dynamics
     * Compute Forward Kinematics of each frames
     * Compute Jacobian Matrices of each frames
     * Compute Dynamic Matrices of the manipulator
     * Obtain the dynamics equation of the manipulator
   * Background studies in Open Kinematics Chain
     * Studies Structure of Parameters
     * Compute Forward Kinematics of each frames
     * Compute Jacobian Matrices of each frames
     * Compute Dynamics Matrices of the chain
     * Obtain the dynamics equation of the chain
   * Background studies in Hybrid System Dynamics
     * Study and implement bouncing ball
     * Study and implement Compass Gait
     * Study and implement Passive Dynamics Walker
   * Background studies in Poincare Map
     * Simulate simple discreate Poincare Map
   * Background studies in CoM and CoP calculation
     * Implement calculation for CoM and CoP
   * Background studies in ZMP calculation
     * Implement calculation for ZMP

5. Control `Peeraya`

   * Background studies in Biped with point feet
   * Background studies in Biped with feet
   * Parameter Identification of Biped
     * Rough Estimation using CAD Model
   * Design and simulate controller
   * Implement and test the controller
     * Parameter tuning or using System Identification Toolbox

6. Motion Planning `Sirawat`

   * Background research on motion planning for humanoid
   * Optimization
     * Background studies in Linear and Nonlinear Programming \(optimization\)
     * Background studies in Integer Programming
     * Background studies in Mixed-Integer Programming
   * Discrete Path Planning
     * Review A\*
     * Review value iteration
     * Review forward search, backward search, and bidirectional search
   * Motion Planning Background
     * Background studies in polygonal, polyhedral and semi-algebraic model
     * Background studies of topological spaces, manifolds, path, and C-space of rigid bodies + obstacle
   * Sampling-based motion planning
     * Background studies in Metric space, random sampling, grid, lattices, collision detection
     * Background studies in Rapidly-exploring Random Trees
     * Background studies in Probabilistic Roadmaps
   * Background studies in motion planning for Walking Gait Generation

#### HARDWARE :

1. Literature Review `Jirad, Jadsadakon`
   * Background research on Overall Structure of Humanoid
   * Background research on Overall System Architecture of Humanoid
   * Background research on Feet and Ground Contact Sensors
   * Background research on Motor Sizing and Drivers
   * Background research on Joint’s Transmission System
   * Background research on Power Source
2. Mechanical System Design `Jirad, Jadsadakon`
   * Skeleton Design
     * Checking Kinematics Feasibility
   * Motor Sizing
   * Motor Mount Design
   * Robot Structure Design
   * Full CAD Assembly
     * How-to-build Assembly instruction
     * BOM
   * Simulation Test and refine
   * Structure Optimization
3. Electrical System Design `Wuttipat`
   * Overall System Architecture
     * Thorough Block Diagram
   * Power Source
     * Finalize Specs
   * Mainboard
     * Schematics
   * Motor Drivers
   * Sensors
     * Encoders
     * IMU
     * Ground Contact Sensors
4. Fabrication `Jirad, Jadsadakon`
   * Order and Receive Mechanical Equipment
     * Motors
     * Screws
     * Etc
   * Order and Receive Electrical Components
     * Mainboard
     * Sensors
   * Order and Receive Part
     * Customized 3d-printed parts
     * Customized machined parts
     * Customized printed circuit boards
   * Assemble all components
     * Assemble all mechanical components
     * Include all electrical components
5. Testing `All`
   * Test Robot Movement
     * Checking for joints’ limits and kinematic feasibility
   * Test Actuation
     * Checking for power consumption
   * Test Sensing
     * Checking for accuracy and signal-to-noise ratio

#### INTEGRATION : `All`

1. Parameter Estimation for hardware
   * Log data from sensors
   * Perform parameter estimation
2. State Estimation & Control Integration \(SC\)
   * Simulate close-loop controlled humanoid and sensors with uncertainty
3. Motion Planning & SC Integration \(MSC\)
   * Combine Motion Planning with close-loop control and estimation system
4. Hardware & Control Integration
   * Calibrate for controlling actual hardware
5. Hardware & SC Integration
   * Adding state estimation to the controlled system
6. Hardware & MSC Integration
   * Full integration



