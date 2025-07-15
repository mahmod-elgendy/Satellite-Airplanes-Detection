# 🛰️ Satellite Plane Detection using CNN

This project uses a Convolutional Neural Network (CNN) to detect airplanes from satellite imagery. It is trained on the [PlanesNet Dataset](https://www.kaggle.com/datasets/rhammell/planesnet) and applied to full-scene satellite images to locate airplanes using a sliding window approach.

---

## 📂 Dataset

- **Source**: Kaggle – [PlanesNet](https://www.kaggle.com/datasets/rhammell/planesnet)
- **Content**:
  - 32,000 labeled 20×20 RGB image tiles
  - Each image labeled `1` (plane) or `0` (no plane)
  - Filename format: `{label}_{scene_id}_{longitude}_{latitude}.png`

---

## 🧠 Model

A lightweight Convolutional Neural Network (CNN) is trained to classify each 20×20 image as containing a plane or not.

### Architecture Highlights:
- 3 Convolutional blocks with Batch Normalization
- Global Average Pooling for compact representation
- Dropout and L2 regularization to prevent overfitting
- Binary output via sigmoid activation

---

## 🛠️ Detection Pipeline

Once the CNN is trained:

1. **Load a full satellite scene** (`scene_1.png`)
2. **Apply a sliding window** (20×20) over the image with a stride of 2–5 pixels
3. **Batch predict** all patches using the trained CNN
4. **Filter by confidence threshold** (e.g., 0.75)
5. **Apply Non-Max Suppression (NMS)** to remove overlapping boxes
6. **Draw green bounding boxes** around detected planes

---

## 📈 Performance Improvements

- Used data augmentation and batch normalization for better generalization
- Switched to batched inference for fast scene scanning
- Added non-max suppression to reduce duplicate detections
- Tuned detection threshold and stride for better accuracy

---

## 📊 Example Output

A full scene image with green bounding boxes drawn on airplane locations as detected by the model:

<img width="768" height="737" alt="image" src="https://github.com/user-attachments/assets/baf8a257-f358-4958-b86a-72a2caede0e7" />


---

## 🧪 Requirements

- Python 3.7+
- TensorFlow or Keras
- OpenCV
- NumPy
- Matplotlib
- kagglehub

✍️ Author
Mahmoud Elgendy


📄 License
MIT License — use freely with credit.
