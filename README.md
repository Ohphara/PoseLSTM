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
2. Open a terminal and allow X server access for Docker:
    ```bash
    xhost local:root
    ```
3. **Download the prebuilt Docker image tar file from [Google Drive](https://drive.google.com/uc?id=YOUR_FILE_ID).**  
   *(Replace `YOUR_FILE_ID` with the actual file ID.)*

4. **Load the Docker image on Jetson Nano:**
    ```bash
    docker load -i 25_IAP_team6.tar
    ```
5. (Optional) Verify the image was loaded successfully:
    ```bash
    docker images
    ```

6. **Enter the Docker container** (example command, modify as needed):
    ```bash
    sudo docker run -it --rm --runtime nvidia --network host \
      -v /tmp/.X11-unix:/tmp/.X11-unix \
      -e DISPLAY=$DISPLAY \
      -v $(pwd):/workspace \
      --device /dev/video0:/dev/video0 \
      --name pose_lstm_container \
      my_yolo:latest
    ```

7. Inside the Docker container, run:
    ```bash
    python3 main.py
    ```

8. The system will start.  
   If abnormal behavior is detected, video clips will be saved automatically in the `videos/` folder.

---
