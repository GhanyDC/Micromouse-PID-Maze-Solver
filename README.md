# Micromouse PID Maze Solver 🐭

An Arduino Nano–based Micromouse robot that uses PID motor control, encoders, and ultrasonic sensors to explore and solve a 6×6 maze (1 ft cells).  
Built with GA12-N20 motors, TB6612FNG motor driver, and three HC-SR04 sensors.

---

## Features
- ⚙️ **PID wheel control** for smooth and accurate motion
- 🔄 **Pivot routines** (90° / 180° turns) using encoder counts
- 📡 **Ultrasonic wall detection** (front, left, right)
- 🗺️ **Flood-fill pathfinding** to explore and compute optimal routes
- 🚀 **Speed-run mode** for fast maze completion after exploration

---

## Hardware
- Arduino Nano
- GA12-N20 300 RPM motors with encoders (CPR = 720)
- TB6612FNG motor driver
- 3 × HC-SR04 ultrasonic sensors
- 43 mm wheels (radius ≈ 2.15 cm)
- Track width ≈ 8.5 cm

---

## Software
- Written in **Arduino C++**
- Uses [PID_v1](https://playground.arduino.cc/Code/PIDLibrary/) library
- Modular structure:
  - `wheelService()` → PID loop at 40 Hz
  - `moveOneCell()` → drive exactly one maze cell
  - `pivot90()` / `pivot180()` → in-place turns
  - `readCM()` → ultrasonic distance in cm
  - Flood-fill algorithm for maze solving

---

## How to Run
1. Flash the code to your Arduino Nano.
2. Place the Micromouse at the maze start cell.
3. Press the button:
   - First press → **Explore mode** (maps the maze).
   - Second press → **Speed-run mode** (executes optimal path).
4. Watch the bot reach the center smoothly and fast!

---

## Calibration
Before racing:
- Run the **geometry calibration** routine to confirm:
  - Wheel radius (`WHEEL_R_CM`)
  - Track width (`TRACK_W_CM`)
- Adjust constants if encoder counts differ by >1%.

---

## Future Improvements
- Swap ultrasonic sensors for Sharp IR sensors (faster response).
- Add diagonal moves for shorter paths.
- Implement acceleration profiles for smoother speed runs.

---

## License
MIT License – free to use, modify, and share.
