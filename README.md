<div align="center">
  <img src="https://raw.githubusercontent.com/MasterPhooey/MicroWakeWord-Trainer-Docker/refs/heads/main/mmw.png" alt="MicroWakeWord Trainer Logo" />
  <h1>MicroWakeWord Trainer Docker</h1>
</div>

# MicroWakeWord Trainer Docker

Easily train wake word detection models with this pre-built Docker image.

## Prerequisites

- Docker installed on your system.
- An NVIDIA GPU with CUDA support (optional but recommended for faster training).

## Quick Start

Follow these steps to get started with the microWakeWord Trainer:

### 1. Pull the Pre-Built Docker Image

Pull the Docker image from Docker Hub:
```bash
docker pull masterphooey/microwakeword-trainer
```

### 2. Run the Docker Container

Start the container with a mapped volume for saving your data and expose the Jupyter Notebook:
```bash
docker run --rm -it \
    --gpus all \ 
    -p 8888:8888 \
    -v $(pwd):/data \
    masterphooey/microwakeword-trainer
```
--gpus all: Enables GPU acceleration (optional, remove if not using a GPU).
-p 8888:8888: Exposes the Jupyter Notebook on port 8888.
-v $(pwd):/data: Maps the current directory to the container's /data directory for saving your files.

### 3. Access Jupyter Notebook

Open your web browser and navigate to:
```bash
http://localhost:8888
```
The notebook interface should appear.

### 4. Edit the Wake Word

Locate and edit the second cell in the notebook to specify your desired wake word:
```bash
target_word = 'khum_puter'  # Phonetic spellings may produce better samples
```
Change 'khum_puter' to your desired wake word.

### 5. Run the Notebook
Run all cells in the notebook. The process will:

Generate wake word samples.
Train a detection model.
Output a quantized .tflite model for on-device use.

### 6. Retrieve the Trained Model
Once the training is complete, the quantized .tflite model will be available for download. Follow the instructions in the last cell of the notebook to download the model.




