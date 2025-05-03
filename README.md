# License Plate Detection System


This project develops a computer vision system that detects vehicle license plates from dashcam video footage using YOLO object detection models. It explores real-world constraints like motion blur, varying distances, and manual labeling limitations to create a robust detection pipeline.

---

## Project Scope

This system was built through the following phases:

1. **Create Dataset**  
   Captured dashcam video in various driving environments.

2. **Extract Frames**  
   Processed video into individual still images for annotation.

3. **Annotate Images**  
   Manually labeled all license plates due to limitations in pretrained YOLO classes.

4. **Train Detection Model**  
   Compared and trained several YOLO models to determine optimal performance.

---

## Data Collection Scenarios

| Scenario           | Description                            |
|-------------------|----------------------------------------|
| Parking Lot        | Stationary vehicles with clear plates  |
| Neighborhood       | Slow traffic with frequent stops       |
| Intersections      | Vehicles in close proximity            |
| Rush Hour Highway  | High-density, multi-lane traffic       |
| High-Speed Driving | Speeds up to 70mph with motion blur    |

---

## Frame Extraction

- **Source FPS**: 29.99  
- **Video Duration**: 12 minutes, 16 seconds  
- **Total Frames**: 21,630  
- **Frame Sampling**: Every 10th frame  
- **Final Dataset**: 2,163 frames extracted  

---

## Annotation Process

### Attempted Automated Labeling

- **Challenge:** Pretrained YOLO models do not contain a license plate class.  
- **Result:** Misclassifications (e.g., dashboards incorrectly labeled).  

### Manual Labeling

- **Tool Used**: Roboflow  
- **Total Images Labeled**: 2,163  
- **Details**: Bounding boxes were drawn around every visible plate; multiple plates in one image were all captured.  
- **Quality Assurance**: Low-quality and ambiguous frames were removed.

---

## Model Training and Evaluation

### Models Tested

- **YOLOv8 Variants**: nano (v8n), small (v8s), medium (v8m)  
- **YOLOv11 Variants**: nano (v11n), medium (v11m)

### Evaluation Metrics

- **Precision**: 83%  
- **Recall**: 72%  
- **mAP Scores**: Used to assess accuracy across IoU thresholds

### Performance Trade-offs

- YOLOv11 models offered slight improvements in detection at longer distances and under motion.

---

## Detection Performance by Distance

| Distance       | Observations                             |
|----------------|------------------------------------------|
| **10 ft**      | ~91% confidence – very high accuracy     |
| **15 ft**      | Slightly reduced, still strong           |
| **20 ft**      | Good confidence and clarity              |
| **25 ft**      | Confidence drop, detection still accurate|
| **30 ft+**     | Reliability drops significantly          |

- **Operational Range**: Most effective within 25 feet  
- **Limiting Factors**: Motion blur, distance, and resolution

---

## Summary of Results

- Built a **fully custom dataset** of 2,163 manually annotated images  
- **Trained and compared** YOLOv8 and YOLOv11 model variants  
- **Achieved high-precision detection** within 25 feet  
- Identified performance limitations due to **distance** and **motion blur**

---

## Next Steps

- Expand the dataset to include more diverse driving conditions  
- Explore image enhancement techniques to improve detection at long range  
- Integrate **OCR** (Optical Character Recognition) to read plate numbers  
- Evaluate performance of **YOLOv8-Large** for further accuracy gains

---
