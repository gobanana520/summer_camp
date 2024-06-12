# Summer Camp

**Contents**

- [Summer Camp](#summer-camp)
  - [Introduction](#introduction)
  - [Environment Setup](#environment-setup)
    - [Install Git](#install-git)
    - [Install the Code Editor (VSCode for example)](#install-the-code-editor-vscode-for-example)
    - [Clone the Repository](#clone-the-repository)
    - [Python Environment Setup](#python-environment-setup)
  - [Project Schedule](#project-schedule)
    - [Week 1](#week-1)
    - [Week 2](#week-2)
    - [Week 3](#week-3)
  - [Data Collection](#data-collection)

## Introduction

This is the repository for the Summer Camp project. The project aims to estimate the hand and object poses from the recordings captured by the Multi-Camera System. 

## Environment Setup

  ### Install Git

  - Linux

    ```bash
    sudo apt-get install git
    ```

  - Windows

    I suguest to use [Github Desktop](https://desktop.github.com/), which is more user-friendly. Otherwise, you could install git via [Git for Windows](https://gitforwindows.org/).

  - MacOS

    You can install git either via [Homebrew](https://brew.sh/), or [Github Desktop](https://desktop.github.com/).

    - Homebrew
      ```bash
      /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
      ```

  ### Install the Code Editor (VSCode for example)

  - You could install the Visual Studio Code (VSCode) from the [official website](https://code.visualstudio.com/).
  - Once you have installed the VSCode, you could install below extensions:
    - [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
    - [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
    - [Python Debugger](https://marketplace.visualstudio.com/items?itemName=ms-python.debugpy)
    - [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)
    - [Black Formatter](https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter)


  ### Clone the Repository
  
  ```bash
  git clone https://github.com/gobanana520/summer_camp.git summer_camp
  ```

  ### Python Environment Setup

  Follow steps in the [Python Environment Setup](./docs/Python_Environment_Setup.md) document to setup your Python environment.

---

## Project Schedule

### Week 1
- :white_check_mark: [Pythion Basics](./notebooks/01_Python_Basics.ipynb)
  Try to understand basics in Python, such as list, tuple, set, dictionary, class, function, loop, etc.

- :white_check_mark: [Numpy Basics](./notebooks/02_Python_Numpy.ipynb)
  Try to understand basics in Numpy, such as array, matrix, operation, etc.

- :white_check_mark: [Pytorch Basics](./notebooks/06-1_Pytorch_Basics.ipynb)
  Try to understand basics in Pytorch, such as tensor, operation, etc.
- :white_check_mark: [ComputerVisionBasics](./docs/slides/01_ComputerVisionBasics.pdf)
  - Practice 1: [Transformation](./notebooks/03-3_CV_Transformation.ipynb)
    How to apply the transformation to 3D points.
  - Practice 2: [Deprojection](./notebooks/03-1_CV_Deprojection.ipynb)
    How to depreject the 2D image points to 3D camera points.
  - Practice 3: [Triangulation](./notebooks/03-2_CV_Triangulation.ipynb)
    How to calculate the 3D world points from 2D image points.
  - Homework 1: [SequenceLoader](./notebooks/hw1_SequenceLoader.ipynb)
    Write a class to load the data from sequence recording.
- :white_check_mark: [Introduction_to_ROS](./docs/slides/02_Introduction_to_ROS.pdf)
  Understand the basic concepts and useful commands in ROS.
- :white_check_mark: [Introduction_to_MANO](./docs/slides/03_Introduction_to_MANO.pdf)
  Understand the basic concepts of parametric hand model MANO. And introduce the Pytorch implementation of MANO ([Manopth](https://github.com/hassony2/manopth)).
  - Practice 4: [MANO_Hand](./notebooks/05_MANO_Hand.ipynb)
    Understand how to initialize the MANO layer and run the forward process.
- :white_check_mark: [Introduction_to_Optimization](./docs/slides/04_Introduction_to_Optimization.pdf)
  Understand the basic concepts of optimization and the optimization algorithms.
  - Practice 5: [Optimization](./notebooks/06-2_MANO_Pose_Optimization.ipynb)
    Implement the optimization algorithm to optimize the MANO hand pose parameters to fit the target 3D keypoints.
- :books: Readings
  - :point_right: Highlights
    - [RANSAC Algorithm](https://en.wikipedia.org/wiki/Random_sample_consensus)
      - Practice: [RANSAC](./notebooks/04_RANSAC_Algorithm.ipynb)
        A simple implementation of RANSAC algorithm.
    - [SDF (Signed Distance Function)](https://en.wikipedia.org/wiki/Signed_distance_function)
        Understand the basic concept of SDF. We will use SDF loss to optimize the Hand/Object pose.
    - ROS message synchronization & extraction
      - [Export image from rosbag](https://gist.github.com/zxf8665905/2d09d25da823b0f7390cab83c64d631a)
        Understand how to synchronize the messages from different topics, and extract the images. We will write a RosbagExtractor to extract the images from the rosbag recordings.
    - [MediaPipe Handmarks Detection](https://ai.google.dev/edge/mediapipe/solutions/vision/hand_landmarker)
      Understand the MediaPipe Handmarks Detection. We will write the HandmarksDetector to detect the handmarks from the images.
  - Papers (Optional)
    - [SMPL Body Model](./docs/papers/SMPL.pdf)
    - [SMPL-H Body Model](./docs/papers/SMPL-H.pdf)
    - [SMPL-X Body Model](./docs/papers/SMPL-X.pdf)
  - Methods will be used in the project
    - Object Pose Estimation
      - [FoundationPose](https://nvlabs.github.io/FoundationPose)
    - Image Segmentation
      - [Segment Anything](https://github.com/facebookresearch/segment-anything)
    - Video Object Segmentation
      - [XMem](https://hkchengrex.com/XMem)

### Week 2

- Overview of FoundationPose and Segment Anything
  - [FoundationPose](./docs/papers/FoundationPose.pdf)
  - [Segment Anything](./docs/papers/SegmentAnything.pdf)
- :white_check_mark: Camera Calibration for the latest Canera Extrinsics
  ![camera_calibration](./docs/resources/camera_calibration_vicalib.gif)
- :white_check_mark: Hand Calibration for each team members.
- Record data with ROS
  - Select the Objects
  - Design the tasks (e.g., pick and place, handover, etc.)
- Extract the images from the rosbag recordings
- **Homeworks**
  - HW1: Rosbag_Extraction
    - Try to write the class `RosbagExtractor` 
      - to extract the images from the rosbag recordings for all the camera image topics.
      - the extracted images should be saved in the `./data/recordings` folder following below structure
        ```
        20231022_193630           # the rosbag name
        ├── 037522251142          # the camera serial number
        │   ├── color_000000.jpg  # the color image color_xxxxxx.jpg
        │   └── depth_000000.png  # the depth image depth_xxxxxx.png
        │   └── ...  
        ├── 043422252387
        │   ├── color_000000.jpg
        │   ├── depth_000000.png
        │   ├── ...
        ├── ...
        ├── 117222250549
        │   ├── color_000000.jpg
        │   ├── depth_000000.png
        │   ├── ...
        ```
    - The recorded rosbag files could be downloaded from [box](https://utdallas.box.com/s/inkzi3td9sfhe4efd9uso5orxolcv03g).
    - If you plan to run the ROS locally, you could follow the [ROS Environment Setup](./docs/ROS_Environment_Setup.md) document to setup the ROS environment with conda. Then you could run the `roscore` to start the ROS master, and debug your code under the ROS environment.
    - References:
      - [Export image from rosbag](https://gist.github.com/zxf8665905/2d09d25da823b0f7390cab83c64d631a)
  - HW2: metadata generation
    - For each extracted recording, the metadata should be generated under the sequence folder named `meta.json`. The metadata should contain the following information:
      ```json
      {
        "serials": [    // the camera serial numbers
          "037522251142",
          "043422252387",
          "046122250168",
          "105322251225",
          "105322251564",
          "108222250342",
          "115422250549",
          "117222250549"
        ],
        "width": 640,
        "height": 480,
        "extrinsics": "extrinsics_20240611",
        "mano_calib": "subject_7",  // the person name
        "object_ids": [ // the object ids in the recording
          "G01_1",
          "G01_2",
          "G01_3"
        ],
        // the hand sides in the recording, if there are two 
        // hands, the right hand should be the first one.
        "mano_sides": [
          "right",
          "left"
        ],
        "num_frames": 100 // the number of frames in the recording
      }
      ```
  - HW3: Handmarks_Detection
    - Try to write the class `HandDetector` to detect the handmarks from the extracted images using the [MediaPipe Handmarks Detection](https://ai.google.dev/edge/mediapipe/solutions/vision/hand_landmarker).
    - The detected handmarks should be saved in the `./data/recordings/<sequence_name>/processed/hand_detection` folder following below structure
      ```
      <sequence_name>/processed/hand_detection
      ├── 037522251142          # the camera serial number
      │   ├── handmarks_000000.npy  # the handmarks file handmarks_xxxxxx.npy
      │   ├── vis_000000.png  # the visualization of the handmarks vis_xxxxxx.png
      │   └── ...  
      ├── 043422252387
      │   ├── handmarks_000000.npy
      │   ├── vis_000000.npy
      │   ├── ...
      ├── ...
      ├── 117222250549
      │   ├── handmarks_000000.npy
      │   ├── vis_000000.npy
      │   ├── ...
      ```
    - The detected handmarks should be saved as the numpy array with the shape of `(num_hands, num_joints, 2)`.
    - The detected handmarks should be saved in the image coordinate system.
    - The detected handmarks should be saved in the order of the right hand first, and then the left hand.


### Week 3

**TBD**


---

## Data Collection

1. Objects Used in the Dataset
   - The dataset contains the following objects:
     ![Object List](./docs/resources/objects_info.png)
   - The object models are saved under the `./data/models` folder. You could use [Meshlab](https://www.meshlab.net/) to view the object models.

2. Calibration Information
   - Camera Intrinsics
     The camera intrinsics files are saved under the `./data/calibration/intrinsics` folder.
   - Camera Extrinsics
     The camera extrinsics files are saved under the `./data/calibration/extrinsics` folder.
   - MANO Hand Shapes
     The MANO hand shapes are saved under the `./data/calibration/mano` folder.

3. Rosbag Recordings

   You coud download the rosbag recordings from the [Box](https://utdallas.box.com/s/inkzi3td9sfhe4efd9uso5orxolcv03g).
