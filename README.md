# PoseLSTM

## 1. Motivation

*(Describe the motivation and purpose of this project here)*

---

## 2. Overview

**PoseLSTM** is a real-time human pose and abnormal behavior detection system designed for the Jetson Nano.  
It utilizes pose estimation, LSTM, and rule-based algorithms to classify human behaviors.  
When abnormal behavior is detected, the corresponding video segment is automatically saved to the `videos/` folder.

---

## 3. How to Run

### 1) Setting up Jetson Nano and Environment

1. **Connect an Ethernet cable and a webcam to your Jetson Nano.**
2. **Install `gdown` to download the Docker image tar file from Google Drive:**
    ```bash
    pip install gdown
    ```
3. **Download the prebuilt Docker image tar file using gdown:**  
   *(Replace `YOUR_FILE_ID` with the actual file ID from Google Drive.)*
    ```bash
    gdown --id 1oY3wA6ZSioKAxCIXp_Yr_CHO1PMNqqRF -O 25_IAP_team6.tar
    ```
4. **Load the Docker image on Jetson Nano:**
    ```bash
    docker load -i 25_IAP_team6.tar
    ```
5. (Optional) Verify the image was loaded successfully:
    ```bash
    docker images
    ```
6. Open a terminal and allow X server access for Docker:
    ```bash
    xhost +local:root
    ```
7. **Enter the Docker container** (example command, modify as needed):
    ```bash
    sudo docker run -it --ipc=host --device=/dev/video0 --runtime nvidia \
      -v /tmp/.X11-unix:/tmp/.X11-unix \
      -e DISPLAY=$DISPLAY \
      my_yolo:latest
    ```
8. Inside the Docker container, run:
    ```bash
    python3 main.py
    ```
9. The system will start.  
   If abnormal behavior is detected, video clips will be saved automatically in the `videos/` folder.

---


## Contact

For questions or issues, please [open an issue](https://github.com/Ohphara/PoseLSTM/issues)  
or contact the maintainer by email.
