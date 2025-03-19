#############################
Research
#############################

This page outlines our lab's core focus and expertise in the field of robotics research, arranged based on major **research topics**.

********************************
Learning-based Control
********************************

Legged robots often face challenges due to their high degrees of freedom and the difficulty of accurately modeling complex environments. These factors discourage the development of robust and stable controllers. However, by leveraging reinforcement learning(RL) techniques, we have successfully developed locomotion controllers that enable the quadrupedal robots to adapt and traverse through challenging terrains such as rough, slippery, and deformable surfaces. This learning-based approach not only improves robustness and stability but also reduces dependency on accruate and computationally intensive models, making our controllers well-suited for practical applications in dynamic and unpredictable environments.

.. image:: ../_images/research/VariousTerrains.png
   :width: 100%
   :align: center

.. centered:: Learning-based locomotion on various terrains

Through extensive experimentation, we have demonstrated the effectiveness of our RL-based locomotion controllers. The list of our work is shown below.

----

- Yunho Kim, Hyunsik Oh et al., **Not Only Rewards But Also Constraints: Applications on Legged Robot Locomotion**. IEEE T-RO 2024 `paper_kim24 <https://arxiv.org/abs/2308.12517>`_ `video_kim24 <https://www.youtube.com/watch?v=KAlm3yskhvM>`_

We propose a reinforcement learning framework that maximizes rewards while meeting constraints, applied to train legged robots for challenging terrains.

.. This paper proposes a reinforcement learning framework for complex articulated systems consisting of both rewards and constraints.
.. An efficient policy optimization algorithm is suggested to search for a policy that maximizes the reward while satisfying multiple constraints with a negligible amount of additional computation cost.
.. The proposed learning framework is used to train controllers for legged robot locomotion in challenging terrains.

.. image:: ../_images/research/NotOnlyReward.png
   :width: 100%
   :align: center

.. centered:: Proposed RL Framework

----

- Joon Hyub Lee, Hyunsik Oh et al., **RobotSketch: An Interactive Showcase of Superfast Design of Legged Robots**. SIGGRAPH 2024 `paper_oh24 <https://sketch.kaist.ac.kr/pdf/publications/2024_siggraph_robotsketch.pdf>`_ `video_oh24 <https://www.youtube.com/watch?v=dvTZs6fbZf0>`_

Designing robots with complex, articulated parts is challenging. Our solution streamlines this process through 3D sketching, AI-driven movement generation, and VR-based review, optimizing early-stage development.

.. Robots consisting of many articulated parts performing complex movements are challenging to design.
.. We showcase an interactive system for exploring shapes and structures of robots through 3D sketching, generating plausible movements of robots through AI, and reviewing and refining them in VR. 
.. Such immersive prototyping in the early stages can help reduce the time and cost associated with trial and error in later stages, contributing to shortening and streamlining of the robot development process.


.. image:: ../_images/research/RobotSketch.png
   :width: 100%
   :align: center

.. centered:: The RobotSketch Interface

----

- Seunghun Jeon, Moonkyu Jung et al., **Learning Whole-body Manipulation for Quadrupedal Robot**. IEEE Robotics and Automation Letters 2024 `paper_jeon24 <https://arxiv.org/abs/2308.16820>`_ `video_jeon24 <https://www.youtube.com/watch?v=fO_PVr27QxU>`_

We propose a learning-based system for enabling quadrupedal robots to manipulate large, heavy objects using their whole body. Our method does not require explicit object modeling and offers significant computational efficiency compared to optimization-based methods. 

.. image:: ../_images/research/WholeBody.png
   :width: 100%
   :align: center

.. centered:: Quadrupedal Whole-Body Manipulation Overview

----

- Donghoon Youm, Hyunyoung Jung et al., **Imitating and Finetuning Model Predictive Control for Robust and Symmetric Quadrupedal Locomotion**. IEEE Robotics and Automation Letters 2023 `paper_youm24 <https://ieeexplore.ieee.org/abstract/document/10268037>`_ `supplement_youm24 <https://hyunyoungjung.github.io/projects/ifm/ifm.html>`_

We introduce a novel Imitating and Finetuning Model Predictive Control (IFM) framework that combines model-based control and learning algorithms to improve legged robot performance. The framework trains a controller using imitation learning and refines it with deep reinforcement learning for handling challenging terrains. Simulations and hardware tests show that IFM significantly enhances footstep coordination, gait symmetry, and energy efficiency on rough and slippery surfaces compared to traditional methods.

.. image:: ../_images/research/ImitateFineTune.png
   :width: 100%
   :align: center

.. centered:: IFM Framework Overview

----

- Suyoung Choi et al., **Learning quadrupedal locomotion on deformable terrain**. Sci. Robot. 8, eade2256(2023) `paper_choi23 <https://www.science.org/doi/full/10.1126/scirobotics.ade2256>`_ `video_choi23 <https://www.youtube.com/watch?v=dt1u8zwUMok>`_

.. image:: ../_images/research/DeformableContactModel.png
   :width: 100%
   :align: center

.. centered:: Contact model of deformable terrains

----

- Gwanghyeon Ji et al., **Concurrent Training of a Control Policy and a State Estimator for Dynamic and Robust Legged Locomotion**. IEEE Robotics and Automation Letters, vol. 7, no. 2, pp. 4630-4637, April 2022 `paper_ji22 <https://ieeexplore.ieee.org/abstract/document/9714001>`_ `video_ji22 <https://www.youtube.com/watch?v=9QV0Nnm80tU>`_

.. image:: ../_images/research/ConcurrentControlDiagram.png
   :width: 100%
   :align: center

.. centered:: Concurrent training architeture

----

- Blind locomotion through the natural environment characterized by steep slopes and scattered debris (ongoing) `video_compiled <https://www.youtube.com/watch?v=f696z7Mx6Ls>`_ `video_hiking <https://www.youtube.com/watch?v=yV-tP3DHXes>`_

- Dynamic locomotion for traversing stepping stones (ongoing)

----

*****************************
Autonomous Navigation
*****************************

Legged robots have great potential for exploring a diverse range of environments accessible to both humans and animals. 
These encompass urban settings as well as natural landscapes like forests and mountains.
However, navigating autonomously in these environments is challenging as it requires the integration of semantic and geometric reasoning for path planning, 
and the consideration of the robot's physical constraints and controller characteristics for path tracking.

.. image:: ../_images/research/AutonomousNavigationFramework.png
   :width: 100%
   :align: center

.. centered:: Autonomous navigation framework (Top), Testing in the physics simulation (Bottom)

In our lab, we're actively combining learning-based approaches with classical methods to build an autonomous navigation framework.
The framework includes traversibility estimation, efficient path and motion planning, and precise path tracking algorithms.
Our ultimate goal is to develop a navigation system that can be applied to various tasks, including autonomous indoor and outdoor inspections.
The list of our work is shown below.

----

- Jeong Hyun Lee, Jinhyeok Choi, et al., **Learning Vehicle Dynamics from Cropped Image Patches for Robot Navigation in Unpaved Outdoor Terrains**. IEEE Robotics and Automation Letters (RA-L) 2024 `paper_lee24 <https://arxiv.org/abs/2309.02745>`_ `video_lee24 <https://youtu.be/iIGNZ8ignk0?si=39CIstwSsdVhPPZq>`_
   
Building on our work in autonomous navigation, we address the challenges of unpaved outdoor environments with high-dimensional sensor data by developing Crop-LSTM. This novel approach enhances local feature extraction from cropped image patches, improving predictions of the robot’s future position and orientation. We validated Crop-LSTM on our Raicart platform, successfully navigating challenging terrains using RGBD images.

.. image:: ../_images/research/VehicleDynamicsCropped.png
   :width: 100%
   :align: center

.. centered:: Dynamics Learning Framework

----

- Yunho Kim et al., **Learning Forward Dynamics Model and Informed Trajectory Sampler for Safe Quadruped Navigation**. Robotics: Science and Systems 2022. `paper_kim22 <https://arxiv.org/abs/2204.08647>`_ `video_kim22 <https://youtu.be/-UTEL6zHNv4>`_

.. image:: ../_images/research/ForwardDynamicsModel.png
   :width: 100%
   :align: center

.. centered:: Forward dynamics model training pipeline

----

*****************************
Hardware Platform
*****************************


+++++++++++++++++++++++++++++
Mechanical Design
+++++++++++++++++++++++++++++

Our Lab directly creates all the components to experiment with a controller to which the learning algorithm is applied.
 
.. image:: ../_images/robot_design/raibo_6.png
   :width: 100%
   :align: center
		
.. centered:: Raibo

	  


Raibo, made by Railab, has hardware that can withstand shocks under various conditions and operate robustly regardless of the environment. 
We also design its own driving units, which are key components consisting of motors, motor reducers, encoders, and motor drivers. 
With its own form factor, it plays a major role in achieving high efficiency during operation.
 
 
.. image:: ../_images/robot_design/raibo_5.png
   :width: 100%
   :align: center
  
.. centered:: Raibo driving units



.. image:: ../_images/robot_design/raibo_3.png
   :width: 100%
   :align: center
  
.. centered:: Raibo Leg Design 

Through various simulations, we demonstrate that we can operate robustly and efficiently in various situations.
The list of our work is shown below.

- J. Hwangbo, et al. **Cable-driven actuation for highly dynamic robotic systems**. 2018 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS) 2018. `Paper3 <https://arxiv.org/pdf/1806.10632.pdf>`_

+++++++++++++++++++++++++++++
Electrical Design
+++++++++++++++++++++++++++++

We are rigorously pursuing research in the electronics sector for pushing hardware utilization to the extreme. Our research extends from designing power circuit, crucial for handling inrush currents and regenerative braking during impacts, to high-power, high-bandwidth motor drivers. The circuit design, artwork, SMT, and testing are all performed in-house.

.. image:: ../_images/robot_design/schematic_artwork.png
	:align: center
.. centered:: Circuit drawing (Left), Component layout (Right) [Blurred image for security]

.. image:: ../_images/robot_design/smt_testing.png
	:align: center
.. centered:: SMT assembly (Left), Testing (Right)

Leveraging our deep understanding of power electronics and robotic systems, we are not just enabling robots to utilize the extreme area of motor capabilities, but also contributing to bridging the sim-to-real gap. Furthermore, taking into account the characteristics of each electronics component, we can build high power and low noise motor driver in a small form factor and facilitate it into efficient locomotion.
