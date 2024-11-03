# Parking Spot Detection System

A computer vision project that detects and monitors available parking spots in real-time using OpenCV and machine learning.

## Overview

This system analyzes video feeds from parking lots to determine which parking spots are occupied or empty. It uses a trained SVM (Support Vector Machine) classifier to make predictions based on image data from individual parking spots.

## Features

- Real-time parking spot monitoring
- Visual display of occupied/available spots
- Running counter of available parking spaces
- Processing optimization using frame skipping
- Support for custom parking spot masks

## Requirements

```
opencv-python
numpy
scikit-image
scikit-learn
matplotlib
pickle
```

## Project Structure

- `main.py` - The main script for real-time parking spot detection
- `util.py` - Utility functions for spot detection and classification
- `train_model.py` - Script for training the SVM classifier
- `model.p` - Trained model file (generated after training)
- `mask_1920_1080.png` - Mask file defining parking spot areas

## How It Works

1. The system uses a predefined mask to identify individual parking spots
2. Each spot is processed through a trained SVM classifier
3. The classifier determines if each spot is empty or occupied
4. Results are displayed in real-time with green (empty) or red (occupied) rectangles
5. A counter shows the total number of available spots

## Usage

1. Create a mask for your parking lot video:
   - Define parking spots as white rectangles on a black background
   - Save as 'mask_1920_1080.png' (or update the path in main.py)

2. Train the model:
```bash
python train_model.py
```

3. Run the detection system:
```bash
python main.py
```

## Training the Model

The model is trained on two categories of images:
- `empty`: Images of empty parking spots
- `not_empty`: Images of occupied parking spots

The training script (`train_model.py`):
- Resizes all images to 15x15 pixels
- Performs train/test split (80/20)
- Uses GridSearchCV to find optimal SVM parameters
- Saves the best model to 'model.p'

## Performance Optimization

- Frame skipping is implemented to reduce processing load
- Differential analysis between frames to prioritize spots that need checking
- Connected components analysis for efficient spot detection

## Exit Program

Press 'q' to quit the application while it's running.

## Contributing

Feel free to fork this repository and submit pull requests. You can also open issues for bugs or feature requests.

## License

This project is open source and available under the MIT License.