Software
========

이곳은 Software 컨텐츠에 대한 설명입니다.

이 문서는 **ROS2 Workspace for Robot Arm**에 대한 정보를 포함하며, 로봇팔 제어를 위한 각 패키지의 구성과 주요 명령어들을 정리합니다.

ROS2 Workspace for Robot Arm
----------------------------

이 ROS2 작업공간은 로봇팔을 제어하기 위한 패키지들을 포함합니다.

패키지 종류 요약
~~~~~~~~~~~~~~~~

+----------------------------+-------------------------------------------------------------+
| **패키지명**               | **설명**                                                  |
+============================+=============================================================+
| **rover_arm_description**  | 로봇 URDF 모델을 포함한 패키지                              |
+----------------------------+-------------------------------------------------------------+
| **rover_arm**              | 원통형 URDF 모델 포함 (사용되지 않음)                        |
+----------------------------+-------------------------------------------------------------+
| **rover_arm_moveit_config**| MoveIt 설정을 위한 패키지                                  |
+----------------------------+-------------------------------------------------------------+
| **rover_arm_moveit_cpp**   | MoveIt 관련 C++ 노드 포함                                  |
+----------------------------+-------------------------------------------------------------+

ROS 패키지 리스트
~~~~~~~~~~~~~~~~~

1. **rover_arm_description**

   로봇의 URDF 모델을 포함하는 패키지로, Fusion 360을 사용하여 생성되었습니다.
   STL 파일과 충돌 모델(Collision body)이 포함되어 있습니다.

   원래 사용되던 *fusion2urdf-ros2* ( [fusion2urdf-ros2](https://github.com/dheena2k2/fusion2urdf-ros2) )는 동작하지 않아,
   [Robotizer-be의 fork](https://github.com/Robotizer-be/fusion2urdf-ros2)를 사용합니다.

   **설정 전 필수 작업:**

   1. **STL 파일 이름 수정**  
      `meshes/` 디렉토리 내의 STL 파일에서 자동 추가된 `(1)` 등의 문구를 제거합니다.  
      예: ``link1 (1).stl`` → ``link1.stl``

   2. **Launch 파일 수정**  
      `launch/display.launch.py` 파일에서 모델 경로를 아래와 같이 수정합니다:

      .. code-block:: python

         default_model_path = os.path.join(pkg_share, 'urdf/rover_arm_macro.urdf.xacro')

   3. **Xacro 매크로 호출 위치 확인**  
      `urdf/rover_arm_macro.urdf.xacro` 파일의 마지막 부분(두 번째 줄 전)에 아래 코드를 추가합니다:

      .. code-block:: xml

         <xacro:rover_arm prefix=""/>

   4. **base_link Visual 미표시 문제 해결**  
      `urdf/rover_arm_macro.urdf.xacro` 파일에서 `base_link` 정의를 아래와 같이 수정합니다:

      .. code-block:: xml

         <link name="${prefix}base_link">
           <visual>
             <origin xyz="0 0 0" rpy="0 0 0"/>
             <geometry>
               <mesh filename="package://rover_arm_description/meshes/base_link.stl" scale="0.001 0.001 0.001"/>
             </geometry>
             <material name="rover_arm_silver"/>
           </visual>
           <collision>
             <origin xyz="0 0 0" rpy="0 0 0"/>
             <geometry>
               <mesh filename="package://rover_arm_description/meshes/base_link.stl" scale="0.001 0.001 0.001"/>
             </geometry>
           </collision>
         </link>

   **주요 명령어:**

   - URDF 모델 확인:

     .. code-block:: bash

        ros2 launch rover_arm_description display.launch.py

2. **rover_arm**

   원통형 URDF 모델을 포함한 패키지이나, 현재는 사용되지 않습니다.

   **주요 명령어:**

   - URDF를 RViz에서 확인:

     .. code-block:: bash

        ros2 launch rover_arm display.launch.py

     *(현재 실행되지 않음)*

   - Joint 별 각도 설정 슬라이더 실행:

     .. code-block:: bash

        ros2 run joint_state_publisher_gui joint_state_publisher_gui

3. **rover_arm_moveit_config**

   `rover_arm`의 URDF를 기반으로 MoveIt 설정을 위한 패키지입니다.

   **주요 명령어:**

   - MoveIt 설정 실행:

     .. code-block:: bash

        ros2 launch moveit_setup_assistant setup_assistant.launch.py

     - 설정 전에 다음 명령어를 먼저 실행합니다:

       .. code-block:: bash

          source install/setup.bash

   - MoveIt 및 RViz 실행:

     .. code-block:: bash

        ros2 launch rover_arm_moveit_config demo.launch.py

   **알려진 버그:**

   1. 새로 설정 후 ``rover_arm_moveit_config/config/joint_limits.yaml`` 파일에서 limit 값을 소수점 형식으로 수정해야 합니다.  
      예시: ``1`` → ``1.0``

4. **rover_arm_moveit_cpp**

   MoveIt 관련 C++ 노드를 포함한 패키지입니다.

   **주요 명령어:**

   - C++ 노드 실행:

     .. code-block:: bash

        ros2 run rover_arm_moveit_cpp hello_moveit

추가 상세 내용
----------------

필요에 따라 각 패키지에 대한 추가 설명과 설정 방법을 보다 상세히 문서화할 수 있습니다.
