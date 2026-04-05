# Engineering Portfolio
 
Real systems work on autonomous rovers: dataset design, model deployment on constrained hardware, distributed systems architecture, and real-time networking.
 
## Overview
 
This portfolio documents technical ownership of key subsystems on **ASU ROAR**, an autonomous Mars rover competing in the [European Rover Challenge](https://roverchallenge.eu/) (ERC). The competition takes place in Krakow, Poland at AGH University. The work spans two years of active development and represents the full cycle from problem definition through validation on live hardware.
 
I can't share proprietary team code, but these case studies show how I approach hard problems:
- End-to-end ownership (not isolated contributions)
- Design under constraints (hardware, power, latency)
- Evidence-based decisions (metrics, not assumptions)
- Iteration when things break (and debugging at multiple system levels)
 
---
## Projects
 
### 1. Perception Pipeline: Custom Rock Detection Model (2024)
 
**Problem:** ROAR's rover needs autonomous rock/soil/anomaly classification for scientific sampling. Off-the-shelf datasets don't match Mars-like terrain under rover camera conditions.
 
**Scope:** Dataset design → model selection → embedded deployment → validation
 
**What I owned:**
- Designed and executed custom dataset curation: 1,886 hand-annotated images via Roboflow
- Recognized dataset imbalance → implemented synthetic image generation using Gemini to boost underrepresented classes (anomaly objects)
- Evaluated and selected YOLOv8 (inference speed vs. accuracy tradeoff for Jetson Xavier deployment)
- Solved Jetson deployment pain: CUDA version mismatches, cuDNN incompatibilities, PyTorch wheel availability, thermal throttling under sustained inference
- Measured and optimized: latency per inference, throughput across dual cameras, GPU utilization, accuracy on holdout test set
**Evidence:**
- Custom dataset: 1,886 manually annotated images (rocks, regolith, anomalies) in Roboflow
- Synthetic augmentation: Used Gemini image generation to address class imbalance (anomaly objects underrepresented in original dataset)
- Live rover deployment: YOLOv8 inference running on Jetson Xavier with dual ZED2i cameras
- Real-time pose estimation: Centroid detection + 6DOF pose calculation (xyz position + axis rotation) via point cloud processing
- Lab validation: Detection and pose estimation on live rover imagery (3 test images showing rock and anomaly detection)
- Dataset validation: Training/validation/test splits with per-class accuracy metrics
## About ROAR
 
[ASU ROAR](https://asurobotics.org/roar/) competes in the [European Rover Challenge](https://roverchallenge.eu/) (ERC), an international space robotics competition held annually in Krakow, Poland. The team designs and builds an autonomous rover to explore and sample a mock Mars environment. This requires real-time perception, planning, control, and teleoperation under Earth-to-Mars latency constraints.
 
I joined ROAR in 2024 and have been contributing across perception, systems architecture, supervisor and logging and networking. The work shown here represents two years of active development and is ongoing through the 2026 competition season.
 
---
 
## Get in Touch
 
Questions about the work? Found an error? Open an issue or reach out—I'm happy to discuss the technical details, tradeoffs, or lessons learned.
 
