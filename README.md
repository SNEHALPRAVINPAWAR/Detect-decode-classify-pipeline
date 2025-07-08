# Detect-decode-classify-pipeline
Real-time detection and classification pipeline using Intel DL Streamer and OpenVINO.

Smart Video Analytics Pipeline using Intel DL Streamer & OpenVINO
This project implements a scalable deep learning pipeline using Intel DL Streamer and OpenVINO Toolkit, focused on real-time person/face detection, attribute classification (age, gender, etc.), and hardware-accelerated inference on CPU/GPU.


✅ Key Features :
- Real-time video analytics using GStreamer + OpenVINO plugins
- Modular pipeline for detection, decoding, and classification
- Supports both person and face detection
- Age-gender classification with age-gender-recognition-retail-0013
- Optimized inference using Intel hardware accelerators
  

🔧 Technologies Used :
- Intel DL Streamer Toolkit
- OpenVINO Toolkit (v2025.2.0)
- GStreamer framework
- Docker for containerized deployment
- Ubuntu 22.04 LTS

🚀 Step-by-Step Pipeline Flow :
1. Environment Setup :
   - Installed OpenVINO and DL Streamer from .tgz archives
   - Set up environment variables for OpenVINO and DL Streamer
   - Verified GStreamer plugins using gst-inspect-1.0

2. Model Download :
   - Downloaded pre-trained models using omz_downloader:
     - person-detection-retail-0013
     - face-detection-retail-0004
     - age-gender-recognition-retail-0013
     - person-attributes-recognition-crossroad-0230
   - Converted to IR format using omz_converter (if needed)

3. Input Preparation :
   - Verified test video (sample.mp4) is present
   - Mounted models and video inside Docker container for use in pipeline

4. Pipeline Design :
   - Constructed GStreamer pipeline with: filesrc ! decodebin ! gvadetect ! gvaclassify ! gvawatermark ! fpsdisplaysink
   - Used gvadetect for object detection
   - Used gvaclassify for attribute recognition (age/gender or person attributes)

5. Inference Execution :
    - Ran pipeline on:
        - CPU with optimized inference
        - GPU using VAAPI (via /dev/dri and vainfo check)
    - Real-time inference with visualization using gvawatermark

6. Result Evaluation :
   - Displayed real-time video with bounding boxes and classified attributes
   - Measured FPS and resource usage (with fpsdisplaysink)
