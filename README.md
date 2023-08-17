# Object Detection Using YOLO with Self-Trained Data

This repository provides a guide on setting up and using YOLO (You Only Look Once) for object detection using self-trained data and a webcam. YOLO is a popular object detection algorithm that can efficiently detect objects in real-time.

## Prerequisites

- Python (>=3.6)
- YOLOv5: This guide uses YOLOv5 for object detection. Install it via:
  ```bash
  pip install yolov5
  ```

## Getting Started

1. **Clone the Repository**:

   Clone this repository to your local machine:

   ```bash
   git clone https://github.com/Hk669/yolov5.git
   cd cap-detection-yolo-webcam
   ```

2. **Prepare Your Custom Dataset**:

   Collect and annotate images for your custom object detection task. You'll need to create annotations in YOLO format.
   Use labelImg for labeling the images

3. **Training**:

   Train the YOLO model on your custom dataset. You can follow the YOLOv5's official training guidelines.

4. **Export Model**:

   After training, export the trained YOLO model.

5. **Webcam Object Detection**:

  Run the webcam:

   ```bash
    cap = cv2.VideoCapture(0)
    for label in labels:
        print('Collecting images for {}'.format(label))
        time.sleep(5)

        # loop through images
        for img_num in range(number_images):
            print('Collecting images for {}, image number {}'.format(label,img_num))
    
            # webcam feed
            ret, frame = cap.read()
    
            # naming out image path
            imgname = os.path.join(IMAGES_PATH, label+'.'+str(uuid.uuid1())+'.jpg')
    
            # writes image to file
            cv2.imwrite(imgname, frame)
            
            # render to the screen
            cv2.imshow('Image collection', frame)
            time.sleep(2)
            if cv2.waitKey(10) & 0xFF == ord('q'):
                break
    cap.release()
    cv2.destroyAllWindows()

   ```


## Project Structure

```
cap-detection-yolo-webcam/
│
├── data/                # Custom dataset and annotations
│   ├── images/
│   └── labels/
│
├── weights/             # Trained model weights
│
├── dataset.yml  # Webcam object detection script
|          
│
└── README.md
```

## Acknowledgments

- This project is built upon the YOLOv5 repository: [YOLOv5 GitHub](https://github.com/ultralytics/yolov5)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---
