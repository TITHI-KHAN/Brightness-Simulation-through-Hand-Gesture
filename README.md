# Brightness-Simulation-through-Hand-Gesture

### The purpose of this code is to demonstrate the concept of mapping hand gestures to brightness control without actually implementing OS-specific brightness control.

This Python script uses computer vision and hand tracking to control the brightness of the display on a Windows system. Here's what each part of the code does:

1. **Imports**: It imports necessary libraries including OpenCV (`cv2`), MediaPipe for hand tracking (`mediapipe`), and the `win32api` and `win32con` modules for adjusting display brightness on Windows.

2. **MediaPipe Setup**: It sets up MediaPipe for hand tracking. This includes initializing `mp_drawing` for drawing hand landmarks and `mp_hands` for hand detection.

3. **Brightness Mapping Function**: The `map_hand_distance_to_brightness()` function maps the distance between thumb tip and index finger tip to a brightness value. It takes the distance as input and returns a brightness value within a specified range.

4. **Brightness Adjustment Function**: The `set_brightness()` function adjusts the display brightness on a Windows system. It uses the `win32api.SetMonitorBrightness()` function to set the brightness level of the primary monitor.

5. **Video Capture Initialization**: It initializes video capture from the default camera (`cap = cv2.VideoCapture(0)`).

6. **Main Loop**:
   - It continuously reads frames from the video capture.
   - It processes each frame for hand detection using MediaPipe.
   - If hands are detected in the frame, it calculates the distance between the thumb tip and index finger tip.
   - It maps the distance to a brightness value using the `map_hand_distance_to_brightness()` function.
   - It adjusts the display brightness using the `set_brightness()` function based on the calculated brightness value.
   - It draws the hand landmarks on the frame for visualization using `mp_drawing.draw_landmarks()`.
   - It displays the frame with hand landmarks and brightness adjustment control using `cv2.imshow()`.
   - It exits the loop if the ESC key is pressed.

7. **Release Resources**: After the loop, it releases the video capture and closes all OpenCV windows using `cap.release()` and `cv2.destroyAllWindows()`.

Overall, this script allows you to control the brightness of your Windows display by moving your hand closer or farther from the camera. The closer your hand is, the higher the brightness will be, and vice versa.

## How the hand will move to increase and decrease brightness?

The hand movement is detected using MediaPipe's hand tracking module. Specifically, it tracks the position of the thumb tip and the index finger tip. The distance between these two landmarks is then used to control the brightness of the display.

Here's how hand movement affects brightness control:

1. **Increasing Brightness**: As the hand moves closer to the camera (i.e., the distance between the thumb tip and index finger tip decreases), the brightness of the display increases. This is because the `map_hand_distance_to_brightness()` function maps shorter distances to higher brightness values.

2. **Decreasing Brightness**: Conversely, as the hand moves away from the camera (i.e., the distance between the thumb tip and index finger tip increases), the brightness of the display decreases. Longer distances are mapped to lower brightness values by the `map_hand_distance_to_brightness()` function.

Therefore, by moving your hand closer or farther from the camera, you can control the brightness of the display in real-time. This interaction allows for intuitive brightness adjustment without the need for physical controls.
