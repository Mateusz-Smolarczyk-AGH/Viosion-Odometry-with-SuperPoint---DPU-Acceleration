# 🧭  Viosion Odometry with SuperPoint - DPU Acceleration

This project demonstrates real-time visual odometry using the **SuperPoint** neural network accelerated on a **DPU** (e.g., on the Kria KV260 platform).

The system estimates the camera trajectory by matching keypoints between consecutive frames.

---

## 📁 Repository Contents

- **DPU Files**:
  - `dpu.bit`, `dpu.hwh`, `dpu.xclbin` – bitstream and accelerator configuration (DPUCZDX8G ISA0 B4096 MAX BG)
- **Models**:
  - `SuperPointNet_soft_240` – optimized model for 320×240 input  
  - `SuperPointNet_soft_480` – model version for 640×480 input
- **Notebook**:
  - `Camera_run.ipynb` – main script for running the visual odometry pipeline

---

## 🚀 How to Run

1. Transfer the repository files to the target device (via `scp` or Jupyter file upload).
2. Open and run the `Camera_run.ipynb` notebook.

The notebook contains two main cells:

- **Cell 1** – loads libraries, the SuperPoint model, and helper functions.
- **Cell 2** – starts the odometry loop:
  - a frame is captured from the camera at each iteration,
  - keypoints are detected using SuperPoint,
  - matches are shown live.

🔴 **To stop the execution**, interrupt the cell (e.g., using the ■ button in Jupyter).  
📈 After stopping, a trajectory plot will be automatically displayed.

---

## 📦 Required Python Packages

The notebook uses the following Python libraries:

- `numpy`, `scipy`, `matplotlib`, `opencv-python`, `ipython`
- `pynq_dpu` – specific to Xilinx DPU environments

> ✅ Tested on the official Xilinx system image for Kria, with Jupyter Notebook and DPU support pre-installed.

A `requirements.txt` file is also included for reference.

---

## 🧠 Additional Notes

- The default model used is `SuperPointNet_soft_240` with 320×240 input.
- To use higher resolution, load the `SuperPointNet_soft_480` model and adjust input parameters accordingly.
- The entire pipeline runs in real time and can be extended for further trajectory analysis or SLAM applications.

---
## Contributors

- Mateusz Smolarczyk, Email: mtsmolar@student.agh.edu.pl
- Mateusz Wąsala, Email: wasala@agh.edu.pl

**Coordinator:**  
- Dr Tomasz Kryjak, Email: kryjak@agh.edu.pl

