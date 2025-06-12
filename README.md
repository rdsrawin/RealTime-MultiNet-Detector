# RealTime-MultiNet-Detector

Real-time multi-class object detection using OpenCV and pre-trained deep neural networks (MobileNet-SSD, YOLO, Faster R-CNN, and more).

## Features

* **Real-Time Detection**: Processes live video streams with minimal latency.
* **Multi-Architecture Support**: Easily swap base networks and detectors, including:

  * MobileNet-SSD
  * YOLO (v3, v4, v5)
  * Faster R-CNN
  * GoogleLeNet
  * SqueezeNet
  * ResNet
* **Multi-Class**: Detects and labels multiple object categories.
* **Configurable Confidence Threshold**: Filter detections by confidence score.

## Repository Structure

```
RealTime-MultiNet-Detector/
├── models/                 # Pre-trained model files (.prototxt, .caffemodel, .weights, etc.)
├── real_time_object_detection.py
├── requirements.txt        # Python dependencies
└── README.md               # This file
```

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/rdsrawin/RealTime-MultiNet-Detector.git
   cd RealTime-MultiNet-Detector
   ```

2. **Create and activate a Python virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate    # On Windows use `venv\\Scripts\\activate`
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Download Pre-trained Models**

   * Place your model files (e.g., `MobileNetSSD_deploy.prototxt`, `MobileNetSSD_deploy.caffemodel`, `yolov3.weights`, etc.) into the `models/` directory.

## Usage

```bash
python src/real_time_object_detection.py \
  --architecture mobile_ssd \
  --prototxt models/MobileNetSSD_deploy.prototxt \
  --model models/MobileNetSSD_deploy.caffemodel \
  --labels data/labels.txt \
  --threshold 0.5
```

### Arguments

* `--architecture` : Base network and detection head (e.g., `mobile_ssd`, `yolov3`, `faster_rcnn`).
* `--prototxt`     : Path to Caffe `.prototxt` file (for SSD-based models).
* `--model`        : Path to model weights (`.caffemodel`, `.pb`, `.weights`, etc.).
* `--labels`       : Path to text file containing class labels (one per line).
* `--source`       : Video source (default: `0` for webcam, or path to video file).
* `--threshold`    : Minimum confidence threshold to filter weak detections (default: `0.5`).

## Adding New Architectures

1. Add model loader and preprocessing in `real_time_object_detection.py`.
2. Update the argument parser to accept the new `--architecture` option.
3. Implement the inference and postprocessing logic for your model.

## Performance

SSD300 on VOC: \~59 FPS @ 74.3% mAP (Single Shot Multibox Detector)
Faster R-CNN on VOC: \~7 FPS @ 73.2% mAP
YOLOv3 on COCO: \~30 FPS @ 33% mAP

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

* [OpenCV](https://opencv.org/)
* [Caffe](http://caffe.berkeleyvision.org/)
* [YOLO](https://pjreddie.com/darknet/yolo/)
* [TensorFlow Object Detection API](https://github.com/tensorflow/models/tree/master/research/object_detection)
* Inspired by Abhishek Kr's Real-Time-Object-Detection repository

## 📫 Contact

Feel free to reach out for questions or support:

- **Name**: Rishabh Rajpurohit
- **Email**: [rsarjp17@gmail.com](mailto:rsrajp17@gmail.com)
- **GitHub**: [rdsrawin](https://github.com/rdsrawin)

Happy recommending! 🌟
