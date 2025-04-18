# Color-detection-ESP-32-Cam-
Tracking and detecting obstacles and ojects using ESP32-cam and open cv library.
# Folder structure
# Hardware Setup
IR Sensors: 5 TCRT5000 sensors for line detection (calibrated for lighting changes).

ESP32-CAM: Mounted forward-facing to “see” upcoming turns.

Power: Separate batteries for motors/logic to avoid noise.

Motors: L298N drivers with PWM control.

#Data Collection
Manual Driving: Built a Bluetooth joystick app to log IR readings, camera images, and motor actions at 10Hz.

Dataset: 2,000+ labeled samples (straights, turns, intersections).

Key Insight: Diverse data = robust model. Shadows? Sharp turns? Collect them all!

# Preprocessing & Model Training
IR Data: Scaled to 0–1.

Images: Resized to 64x64 grayscale + edge detection (cut training time by 40%!).

Hybrid Model:

CNN for camera edges.

FNN for IR data.

Fused to predict motor speeds (TensorFlow, MSE loss).

Result: The robot learned to slow before sharp turns!
 Deployment on ESP32
TensorFlow Lite: Quantized model to INT8 (fit in 520KB RAM).

Latency: Reduced inference time to 50ms (critical for real-time control).

Code: Used EloquentTinyML for Arduino inference.
