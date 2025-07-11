# Get base image
FROM python:3.10.17-slim-bookworm

# Install system wide software
RUN apt-get update \
     && apt-get install -y \
        libgl1-mesa-glx \
        libx11-xcb1 \
        git \
        gcc \
        cmake \
        libavcodec-extra \
        ffmpeg \
        curl \
        wget \
        libhdf5-dev \
        gpg \
        gpg-agent \
     && apt-get clean all \
     && rm -r /var/lib/apt/lists/*

RUN pip install --ignore-installed torch==1.12.1 --index-url https://download.pytorch.org/whl/cpu
RUN pip install pytorchyolo==1.8.0 tensorflow==2.14.1 scikit-learn==1.4.2 pytest-cov~=4.1.0

RUN cd /tmp/ && git clone https://github.com/eriklindernoren/PyTorch-YOLOv3.git && cd ./PyTorch-YOLOv3/weights && ./download_weights.sh

RUN mkdir /tmp/yolo_v8.3.0 && cd /tmp/yolo_v8.3.0 && wget https://github.com/ultralytics/assets/releases/download/v8.3.0/yolov8n.pt && wget https://github.com/ultralytics/assets/releases/download/v8.3.0/yolov10n.pt

CMD ["/bin/bash"]
