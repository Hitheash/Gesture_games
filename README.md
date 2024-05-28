**Hand Gesture Controlled Gaming**

This project demonstrates a hand gesture-based control system for a virtual car using a webcam. The system tracks the user's hand movements to control the car's steering and acceleration in real-time using simulated keyboard inputs (W, A, S, D).

Features

- **Hand Tracking**: Uses OpenCV's tracking algorithms to follow hand movements.
- **Gesture Detection**: Detects specific gestures to control the car's movements.
- **Real-time Control**: Implements real-time control for a smooth user experience.
- **Keyboard Simulation**: Simulates keyboard key presses based on detected gestures to control the virtual car.

## Requirements

- Python 3.6+
- OpenCV
- imutils
- pynput
- numpy

## Installation

1. **Clone the Repository**:
    ```bash
    git clone https://github.com/yourusername/hand-gesture-car-control.git
    cd hand-gesture-car-control
    ```

2. **Install Dependencies**:
    ```bash
    pip install -r requirements.txt
    ```

## Usage

1. **Run the Script**:
    ```bash
    python main.py
    ```

2. **Initialize the Camera**:
    The script will open your webcam. Position your hands so that the system can detect and track them.

3. **Setup Phase**:
    - A timer will count down from 3, allowing you to get ready.
    - You'll be prompted to select regions for your left and right hands. This initializes the bounding boxes for tracking.

4. **Control the Car**:
    - **Left Hand**: Controls the car's forward and backward movement:
      - Moving up simulates pressing 'W' (forward).
      - Moving down simulates pressing 'S' (backward).
    - **Right Hand**: Controls the car's left and right steering:
      - Moving left simulates pressing 'A' (left).
      - Moving right simulates pressing 'D' (right).

## Code Overview

### Main Components

1. **Hand Tracking Initialization**:
    ```python
    trackerleft = cv2.TrackerKCF_create()
    trackerright = cv2.TrackerKCF_create()
    trackerleft.init(FRAME, bboxleft)
    trackerright.init(FRAME, bboxright)
    ```

2. **Main Loop**:
    - Reads frames from the webcam.
    - Updates tracker positions.
    - Detects hand centroids.
    - Determines control commands based on hand positions.
    - Simulates keyboard key presses.

3. **Gesture Detection**:
    - `keyboard_events_l` and `keyboard_events_r` functions determine the appropriate command based on hand position.
    - `reset_press_flag` function resets the command if hands move back to the neutral zone.

### Helper Functions

- **get_centroid**: Calculates the center of a bounding box.
- **draw_circle**: Draws a circle on the frame.
- **detect_center**: Draws a circle at the center of the hand and returns the coordinates.
- **draw_controller_left/right**: Draws control boundaries for steering and acceleration.
- **keyboard_events_l/r**: Determines the command based on hand position and simulates key press.
- **reset_press_flag**: Resets the press flag and releases the key if the hand moves back to the neutral zone.

### Example Workflow

1. **Setup**:
    - Select the bounding boxes for your left and right hands.
2. **Tracking**:
    - The system will continuously track your hands and update the bounding boxes.
3. **Control**:
    - Moving your left hand up or down will simulate 'W' or 'S' key presses.
    - Moving your right hand left or right will simulate 'A' or 'D' key presses.

## Future Improvements

- Improve hand detection and tracking accuracy.
- Add support for additional gestures.
- Integrate with an actual car simulation software for a more immersive experience.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

- [OpenCV](https://opencv.org/) for providing powerful computer vision libraries.
- [imutils](https://github.com/jrosebr1/imutils) for simplifying image processing tasks.
- [pynput](https://pypi.org/project/pynput/) for keyboard control.

Feel free to contribute to this project by submitting issues or pull requests. Happy coding!
