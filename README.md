# Real-Time AI Gym Trainer

A real-time computer vision system that tracks body landmarks through a live webcam feed, counts exercise reps automatically, and flags posture errors as they happen.

## Features
- **Pose estimation** with MediaPipe to track body landmarks from a webcam stream
- **Automatic rep counting** so no manual tracking is needed during a workout
- **Rule-based form analysis**: joint angles (knee, hip, shoulder) are computed frame by frame and compared with safe-movement thresholds to flag errors such as shallow squat depth or knee misalignment
- **LLM voice coaching layer** (in progress): converts detected form events into natural-language spoken cues
- **Low-latency pipeline** between camera feed and feedback engine for live corrections

## Tech Stack
Python, OpenCV, MediaPipe, NumPy, OpenAI API

## Project Status
Work in progress. Core pose tracking and form-analysis are being built; the voice coaching layer is being integrated.

## Getting Started
```bash
git clone https://github.com/<your-username>/ai-gym-trainer.git
cd ai-gym-trainer
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # Mac/Linux
pip install -r requirements.txt
python main.py
```

Set your OpenAI key (needed only for the voice coaching layer):
```bash
set OPENAI_API_KEY=your_key_here        # Windows
# export OPENAI_API_KEY=your_key_here   # Mac/Linux
```

## How It Works
1. Webcam frames are read with OpenCV.
2. MediaPipe extracts body landmarks for each frame.
3. Joint angles are calculated and checked against thresholds.
4. Reps are counted from angle transitions (up/down phases).
5. Form errors are passed to the LLM layer, which produces short spoken coaching cues.

## Roadmap
- [ ] Support more exercises (push-ups, lunges, shoulder press)
- [ ] Session summary and progress tracking
- [ ] Optimise latency further

## Author
Rudraksh Charde
