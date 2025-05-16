# Traffic Light Detection using YOLOv8

This project demonstrates a custom traffic light detector trained on the **Bosch Small Traffic Lights Dataset**, using **YOLOv8n** for lightweight and fast inference.

### Goal

Develop a real-time detector that can accurately detect **red** and **green** traffic lights, even in challenging real-world conditions (occlusion, blur, small size).

---

## Dataset

Used a **clean subset** (500–800 images) from the Bosch dataset containing:
- Red lights
- Green lights
- Red + Green Multi-class (both in same frame)
- Off lights / Negatives (no light)

> The Bosch dataset is noisy and contains small objects, making it ideal to test robustness.

---

##  Architecture & Training

- YOLOv8n was chosen for its speed and small size.
- Labels were cleaned and converted to YOLO format.
- Dataset was split into `train/val/test` (70/20/10).
- Augmentations were kept minimal due to small dataset size.

Training command:
```bash
yolo detect/train data=data/bosch.yaml model=yolov8n.pt epochs=50 imgsz=640
```
**Validation Results**

YOLOv8n achieved ~65% mAP@0.5 despite using a small and imperfect dataset.

**Inference Examples**

Good Detection
False Positive (Red mistaken for vehicle tail light)
Low Confidence Detection (Small / Distant)

**Deployment-Ready**

Model was exported to ONNX and TensorRT for edge or real-time applications.

**Future Work**

More samples of small & occluded lights
Use augmentations like Mosaic or MixUp
Try YOLOv8s or anchor-free models
Apply Test-Time Augmentation (TTA) or confidence threshold tuning

**Contributions**

Pull requests welcome! If you have label improvements or want to add better augmentations, feel free to contribute.
