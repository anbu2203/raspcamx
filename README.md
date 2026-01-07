**raspcamx: The Pi Camera**      
This is a camera that can practically take amazing high quality photos and videos using just a raspberry pi!    

<img width="723" height="689" alt="Screenshot (36)" src="https://github.com/user-attachments/assets/e85f2226-e55f-4eaf-b909-c1dfac0671c9" />


**Hardware**    
This uses a Raspberry pi 4 8gb model and a sandisk luxe pendrive to make sure video recording is fast.      
It uses a Pi HQ Camera which has a sony IMX 477 12.3MP Sensor.      
It even has interchangeable lenses!    
I am powering the whole thing using a cuzor mini ups.

## why raspberry pi 4 ##

- Although there are cheaper alternatives available, the Raspberry Pi 4 (8GB) is the most suitable and reliable choice for this project due to the following technical and practical reasons.

1. Full Compatibility with HQ Camera (IMX477)

- The Raspberry Pi 4 offers native and official support for the Raspberry Pi HQ Camera using the CSI interface.
- Direct hardware-level camera support
- Stable drivers maintained by Raspberry Pi Foundation
- No adapters, hacks, or third-party patches required
- Cheaper boards often lack official IMX477 support, leading to instability, driver issues, or reduced image quality.

2. Required Processing Power for Cinema Firmware
-This project uses Cinemate2 (built on CinePi), which requires:
- High CPU performance
- Sufficient RAM for video buffering
- Stable I/O for continuous recording
- The Raspberry Pi 4 provides:
 Quad-core CPU
 Up to 8GB RAM
 Reliable USB 3.0 bandwidth

- Lower-cost boards like Pi Zero, ESP32-CAM, or older SBCs cannot reliably handle this workload without dropped frames or crashes.

3. Reliable High-Speed Storage Support
- Cinema-style video recording demands fast and stable write speeds.
- Raspberry Pi 4 has USB 3.0 ports
- Enables smooth recording to high-speed USB drives
- Prevents frame loss and file corruption
- Cheaper alternatives usually have:
  USB 2.0 only
  Slower I/O speeds
  Unstable recording for large video files

4. Software Ecosystem & Community Support :

- Raspberry Pi has the largest open-source ecosystem among SBCs.
- Well-documented camera stack
- Active CinePi & Cinemate2 community
- Easy troubleshooting and updates
Using cheaper boards would require:
 Custom drivers
 Kernel-level modifications
 Advanced Linux expertise
 This increases complexity, risk, and development time.

5. Same Learning Curve, Higher Output Quality
- While cheaper boards may reduce cost, they do not reduce learning effort. Raspberry Pi 4 provides maximum output for the same learning level Better performance with the    same Linux commands and workflows. Efficient use of time and effort Thus, Pi 4 gives better value per hour of learning, not just lower component cost.

6. Stable Power Management with UPS
- This project uses a Mini UPS to ensure safe shutdown during recording.
- Raspberry Pi 4 supports proper power-handling
- Stable under continuous load
- Prevents SD/USB corruption
- Cheaper boards often lack:
 Power stability
 Proper voltage regulation
 Safe shutdown support

7. Professional-Grade Output
- The goal of this project is quality, not just cost reduction.
- 12.3MP IMX477 sensor
- Interchangeable lenses
- Cinema-style video firmware
Only Raspberry Pi 4 can fully utilize the camera’s capabilities without compromises.

**electrical wiring diagram**
        ┌────────────────────┐
        │   Cuzor Mini UPS   │
        │                    │
        │  5V OUT (USB-A)    │
        └─────────┬──────────┘
                  │
                  │ USB Power Cable
                  ▼
        ┌────────────────────┐
        │  Raspberry Pi 4    │
        │  (8GB RAM)         │
        │                    │
        │  USB-C Power IN ◄──┘
        │                    │
        │  USB 3.0 Port ────────► SanDisk Luxe USB Drive
        │                    │
        │  CSI Camera Port   │
        └─────────┬──────────┘
                  │
                  │ 15-pin CSI Ribbon Cable
                  ▼
        ┌────────────────────┐
        │ Raspberry Pi HQ    │
        │ Camera (IMX477)    │
        │                    │
        │ Lens Mount         │
        └────────────────────┘
![main](https://github.com/anbu2203/raspcamx/blob/main/wiring%20diagram.jpeg)

Detailed Wiring Connections
1. Power Connection

UPS Output → Raspberry Pi

UPS 5V USB output → Raspberry Pi USB-C power port

Provides:

Stable 5V supply

Protection from sudden power loss

Safe shutdown during recording

⚠️ Do NOT power Pi from GPIO pins.

2. Camera Connection

HQ Camera → Raspberry Pi

Use 15-pin CSI ribbon cable

One end → Camera CSI port on Pi

Other end → HQ Camera connector

Blue side of ribbon faces USB ports on Pi

This connection handles:

Video data

Camera control signals

Clock & synchronization

3. Storage Connection

USB Pendrive → Raspberry Pi

Plug SanDisk Luxe USB into USB 3.0 port (blue port)

Used for:

High-speed video recording

Cinemate2 media storage

4. Control Button (Optional – Power / Shutdown)

If you have a button mounted on the enclosure:

Push Button
 ┌───────┐
 │       │
 └─┬───┬─┘
   │   │
   │   └──────────► GND (Pin 6)
   │
   └──────────────► GPIO 3 (Pin 5)


Used for safe shutdown or wake

Requires software configuration in Raspberry Pi

Power Flow Summary
Battery → Mini UPS → Raspberry Pi → Camera + USB Storage

Signal Flow Summary
Camera Sensor → CSI Cable → Raspberry Pi → USB Storage

Safety & Best Practices

✔ Always connect camera before powering ON
✔ Use short, high-quality USB cables
✔ Ensure UPS can supply ≥ 3A at 5V
✔ Secure ribbon cable to avoid loose connections


**Software**    
For software I am using the open source firmware called Cinemate2.    
It is built upon CinePi.   
https://github.com/will127534/cinemate2    
