# Helmet Detection Using Raspberry Pi and CircuitDigest Cloud

As adults, it is our duty to follow traffic rules, and wearing a helmet while riding a two-wheeler is one of the most critical for safety. This project introduces a compact system to ease the burden on traffic police by automatically monitoring traffic and checking whether riders are wearing helmets. By utilizing a Raspberry Pi and the CircuitDigest Cloud Helmet Detection API, this system provides accurate real-time results without the need for manual dataset collection, labeling, or model training.

## Features
- **Real-Time Detection:** Automatically detects helmet violations in real-time using cloud-based AI.
- **Multiple Operating Modes:**
  - **Keyboard Mode:** Capture images manually by pressing the `SPACE` key (ideal for desktop/VNC use).
  - **Auto Mode:** Automatically captures images after a fixed time interval for continuous traffic monitoring.
  - **SSH Mode:** Runs completely via the terminal without needing an OpenCV display window.
- **No Local Processing Overhead:** Leverages the CircuitDigest Cloud for heavy lifting, saving local processing power and setup time.

## Hardware Requirements
- **Raspberry Pi** (Any capable model like Pi 3 or Pi 4, connected to external power)
- **USB Web Camera** (For live traffic monitoring)
- **Laptop/PC** (For initial setup and viewing results)
- MicroSD Card (with Raspberry Pi OS installed)

## Hardware Setup
1. Connect the USB Camera to one of the USB ports on the Raspberry Pi.
2. Ensure the Raspberry Pi is powered by a sufficient external power supply.
3. Place the camera in a proper position with good lighting conditions and a clear angle of the traffic.

## Software Setup
1. Setup your Raspberry Pi using the **Raspberry Pi Imager** with a standard OS installation.
2. Create an account on the [CircuitDigest Cloud](https://www.circuitdigest.cloud/).
3. Navigate to the **Helmet Detection** feature and obtain your **API Key**.
4. Open **Thonny IDE** (or your preferred Python editor) on your Raspberry Pi.
5. Install the necessary Python packages:
   ```bash
   pip install opencv-python requests
   ```

## Installation & Usage
1. Clone this repository or copy the Python script to your Raspberry Pi.
2. Edit the script to include your API key and configure parameters:
   ```python
   SERVER_URL = "https://www.circuitdigest.cloud/api/v1/helmet-detection/detect"
   API_KEY    = "YourApikey"  # <-- Paste your CircuitDigest API Key here
   MODE = "keyboard"          # <-- Set to "keyboard", "auto", or "ssh"
   AUTO_INTERVAL = 10         # <-- Interval in seconds for auto mode
   ```
3. Run the script:
   ```bash
   python helmet_detection.py
   ```
4. Depending on the mode selected, the system will capture images and send them to the CircuitDigest Cloud API. The result (helmet or no helmet) will be displayed in the terminal.

## Troubleshooting
- **Camera not found! Check USB camera connection:** 
  Check the physical connection. Try changing the camera index from `cv2.VideoCapture(0)` to `cv2.VideoCapture(1)` if multiple cameras are connected.
- **API request timeout:** 
  Verify your Wi-Fi or Ethernet connection. A slow or unstable network can cause this. You can also try increasing the timeout value in the request.
- **Invalid API key error:** 
  Check that your API key is copied correctly from Circuit Digest Cloud without any extra spaces or missing characters.
- **Poor helmet detection accuracy:** 
  Ensure good lighting and a clear camera angle. Try increasing the image resolution in OpenCV settings.
- **Program crashes during execution:** 
  Ensure all required libraries (`opencv-python` and `requests`) are properly installed. Restart the Raspberry Pi if the camera feed continuously breaks.

## Advantages & Limitations
| Advantages | Limitations |
| :--- | :--- |
| Automatically detects helmet violations in real time | Requires a stable internet connection for cloud processing |
| Reduces manual work for traffic police | Detection accuracy depends on camera quality and angle |
| Easy to install and use with a standard USB camera | Poor lighting can negatively affect detection results |
| Supports both manual and automatic capture modes | Cloud API usage may have daily or monthly limits |
| Improves road safety monitoring efficiently | Slight delay may occur due to API response time |

## Relevant Links
- [CircuitDigest Cloud Platform](https://www.circuitdigest.cloud/)
- [Raspberry Pi based Helmet Detection GitHub Repo](https://github.com/Circuit-Digest/Raspberry-Pi-based-Helmet-Detection)
