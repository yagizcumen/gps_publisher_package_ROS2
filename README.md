# GPS NEO-6M and Arduino with ROS2 Publisher Package

This repository aims to receive GPS data from the NEO-6M module using an Arduino, filter it, and publish it via a ROS2 Humble publisher.

## Required Hardware and Software

- **Arduino (Uno, Mega, etc.)**
- **NEO-6M GPS Module**
- **ROS2 Humble**
- **Arduino IDE**
- **Python 3 (for ROS2 Publisher)**

## Connection Diagram

| GPS Module (NEO-6M) | Arduino |
|----------------------|---------|
| VCC                 | 5V      |
| GND                 | GND     |
| TX                  | RX (Pin 0) |
| RX                  | TX (Pin 1) |

> **Note:** It is recommended to use a level shifter or software serial communication instead of directly connecting the GPS module to the Arduino.

## Description

This repository contains an Arduino code and a Python-based ROS2 publisher. The Arduino filters the GPS data received from the module and sends it via the serial port. The ROS2 publisher reads this data and publishes it on the `/gps_data` topic in the ROS2 environment.

## Installation and Usage

1. **Upload the Arduino Code**  
   - Open the Arduino IDE.
   - Load the `Arduino_GPS.ino` file.
   - Select the appropriate board and port, then upload the code to the Arduino.

2. **Set Up the ROS2 Package**  
   - Open a terminal and initialize your ROS2 environment:
     ```sh
     source /opt/ros/humble/setup.bash
     mkdir -p ~/ros2_ws/src
     cd ~/ros2_ws/src
     git clone <repo-link>
     cd ..
     colcon build
     source install/setup.bash
     ```

3. **Run the ROS2 Publisher**  
   ```sh
   ros2 run gps_publisher gps_publisher.py
   ```

4. **Monitor GPS Data**  
   ```sh
   ros2 topic echo /gps_data
   ```

With this setup, you can monitor GPS data in the ROS2 environment.

---

If you encounter any issues or have suggestions for improvement, please open an issue or submit a PR. 🚀
