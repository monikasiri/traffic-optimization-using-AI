# Traffic Flow Optimization 

## 📄 Project Summary
This project is a Streamlit-based application that detects emergency and non-emergency vehicles from up to four uploaded video files using YOLO models. It tracks these vehicles and estimates road clearance time.

## 🧠 Abstract
The system uses YOLOv8 to detect emergency vehicles and YOLOv5 for non-emergency vehicles. Each frame of the uploaded videos is processed, vehicles are tracked using Norfair, and unique IDs are assigned to avoid double counting. If an emergency vehicle is detected, a warning is displayed. The road clearance time is estimated using the difference between non-emergency and emergency vehicle counts.

## 💻 Software Used
- Python
- Streamlit
- OpenCV
- PyTorch
- tempfile
- NumPy

## 📚 Libraries Used
- `ultralytics` (YOLOv8)
- `torch.hub` (YOLOv5s)
- `cv2` (OpenCV)
- `streamlit`
- `norfair`
- `numpy`
- `tempfile`

## ⚙️ Algorithm
1. Upload up to 4 video files using Streamlit.
2. For each video:
   - Read frames using OpenCV.
   - Run YOLOv8 for emergency vehicle detection.
   - Run YOLOv5 for non-emergency vehicle detection.
   - Convert detections to Norfair `Detection` objects.
   - Track using Norfair with Euclidean distance.
   - Assign and store unique IDs for each vehicle type.
3. Display detection bounding boxes:
   - Red for emergency vehicles.
   - Green for non-emergency vehicles.
4. Display warning if any emergency vehicle is detected.
5. Calculate and display:
   - Number of non-emergency vehicles.
   - Estimated clearance time:  
     `clearance_time = max(0, (non_emergency_count - emergency_count) * 3)`

## 🚀 How It Works
- Emergency vehicles are detected using `best_emergency_vehicle_model.pt` (YOLOv8).
- Non-emergency vehicles are detected using YOLOv5s.
- Both detection outputs are passed through a Norfair tracker.
- Emergency vehicle presence triggers a warning message.
- Frame is displayed in Streamlit.
- At the end of each video, it displays:
  - Total non-emergency vehicles detected.
  - Estimated road clearance time.
