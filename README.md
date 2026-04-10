# YoloV5 and Faster-RCNN Comparison

## Overview
This project compares the performance of **YoloV5** and **Faster-RCNN** object detection models. It includes training results, metrics analysis, and model comparisons to help understand the strengths and weaknesses of each approach.

## Project Structure
```
.
├── yolov5-01.ipynb          # Main Jupyter notebook with YoloV5 implementation and analysis
├── yolov5mu.pt              # Pre-trained YoloV5m model weights
├── results.csv              # Training metrics and performance results
└── README.md                # This file
```

## Files Description

### yolov5-01.ipynb
The main Jupyter notebook containing:
- Installation and setup of required libraries (PyTorch, YoloV5, OpenCV)
- Data loading and preprocessing
- Model training and evaluation
- Performance metrics visualization
- Comparison with Faster-RCNN

### yolov5mu.pt
Pre-trained YoloV5m model weights for:
- Fast inference on new images
- Transfer learning capabilities
- Direct predictions without retraining

### results.csv
Training results containing:
- Epoch-wise training metrics
- Loss values (box loss, classification loss, DFL loss)
- Validation metrics
- mAP (mean Average Precision) scores
- Learning rate schedules

## Requirements

```bash
python>=3.7
torch>=1.9.0
torchvision>=0.10.0
yolov5
opencv-python
matplotlib
seaborn
scikit-learn
pillow
tqdm
pandas
numpy
```

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Rakshit-2005/YoloV5-and-Faster-RCNN-comparison.git
cd YoloV5-and-Faster-RCNN-comparison
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

Or install individually:
```bash
pip install torch torchvision
pip install yolov5
pip install opencv-python matplotlib seaborn scikit-learn pillow tqdm pandas numpy
```

## Usage

### Running the Notebook
```bash
jupyter notebook yolov5-01.ipynb
```

The notebook provides step-by-step execution with:
- Environment setup
- Model initialization
- Training pipeline
- Evaluation and visualization
- Performance comparison

### Using Pre-trained Model
```python
import torch
import yolov5

# Load the pre-trained model
model = torch.load('yolov5mu.pt')

# Make predictions
results = model('image.jpg')
results.show()
```

## Training Results

The training results are documented in `results.csv` with the following key metrics:

| Metric | Description |
|--------|-------------|
| epoch | Training epoch number |
| time | Training time (seconds) |
| train/box_loss | Bounding box regression loss |
| train/cls_loss | Classification loss |
| train/dfl_loss | Distribution Focal Loss |
| metrics/precision(B) | Precision at IoU=0.5 |
| metrics/recall(B) | Recall at IoU=0.5 |
| metrics/mAP50(B) | mAP at IoU=0.5 |
| metrics/mAP50-95(B) | mAP from IoU=0.50 to 0.95 |

## Model Comparison

### YoloV5
- **Advantages**: Fast inference, real-time detection, lightweight
- **Architecture**: CSPDarknet backbone with PANet neck
- **Performance**: Good balance between speed and accuracy

### Faster-RCNN
- **Advantages**: Higher accuracy, better for small objects
- **Architecture**: Two-stage detector with RPN
- **Performance**: Slower inference, more compute-intensive

## Results Summary

The trained YoloV5m model achieves:
- **Precision**: ~0.73 (at IoU=0.5)
- **Recall**: ~0.57 (at IoU=0.5)
- **mAP50**: ~0.65 (at IoU=0.5)
- **mAP50-95**: ~0.44 (IoU=0.50 to 0.95)

## Visualizations & Results

The notebook generates comprehensive visualizations of the training and detection results:

### Training Metrics - Loss & mAP Curves

This visualization displays four critical training metrics:

#### 1. Training Loss vs Epochs (Blue Curve)
- Shows steady decrease in box loss from ~0.0095 to ~0.005 over 100 epochs
- Demonstrates model convergence and effective learning progression
- Smooth curve indicates stable training without oscillations

#### 2. Validation Loss vs Epochs (Red Curve)
- Validation loss decreases from ~0.011 to ~0.0055 over training
- Tracks validation performance, ensuring model generalizes well
- Similar trend to training loss indicates good model fit without overfitting

#### 3. mAP@0.5 vs Epochs (Green Curve)
- Mean Average Precision at IoU=0.5 threshold
- Improves from ~0.40 to ~0.75 across epochs
- Shows gradual improvement in object detection accuracy at standard IoU threshold

#### 4. mAP@0.5:0.95 vs Epochs (Orange Curve)
- Stricter mAP metric averaging across IoU thresholds (0.5 to 0.95)
- Increases from ~0.25 to ~0.60 over training period
- Indicates strong performance across multiple IoU thresholds, essential for real-world applications

### Detection Results on Test Set

Sample detections demonstrating YOLOv5's capability on Pascal VOC 2012 dataset:

- **Motorbikes**: Detected with green bounding boxes and high confidence scores (0.6+)
- **Bicycles**: Multiple instances correctly identified with colored bounding boxes
- **Person Detection**: Individuals detected with cyan/blue boxes showing 0.83-0.95 confidence
- **Animal Detection**: Cats, dogs, horses, and birds detected accurately
- **Vehicle Detection**: Cars, buses, and trains identified with class labels and confidence
- **Household Items**: Sofas, dining tables, monitors detected in indoor scenes
- **Street Scenes**: Complex scenes with multiple objects detected simultaneously

Each detection includes:
- **Color-coded bounding box**: Different colors for different object classes
- **Class label**: Name of the detected object
- **Confidence score**: Probability of detection accuracy (0.0-1.0)

### Additional Performance Visualizations

The notebook also generates:
- **Confidence Distribution**: Histogram showing prediction confidence scores distribution
- **Class Distribution**: Bar chart of detected object classes showing frequency of detections
- **Inference Speed Analysis**: Real-time performance metrics including average inference time and FPS

## Future Improvements

- [ ] Implement Faster-RCNN model
- [ ] Add quantization for mobile deployment
- [ ] Include confidence threshold analysis
- [ ] Add inference time comparison
- [ ] Implement model ensemble
- [ ] Add data augmentation experiments

## Contributing

Feel free to fork, modify, and submit pull requests with:
- Bug fixes
- Performance improvements
- New features
- Documentation enhancements

## License

This project is provided as-is for educational and research purposes.

## References

- [YoloV5 GitHub](https://github.com/ultralytics/yolov5)
- [Faster-RCNN Paper](https://arxiv.org/abs/1506.01497)
- [PyTorch Documentation](https://pytorch.org/docs/)

## Author

**Rakshit Modanwal**

## Acknowledgements

- Ultralytics for YoloV5
- PyTorch team for deep learning framework
- OpenCV for computer vision tools
