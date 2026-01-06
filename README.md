**raspcamx: The Pi Camera**      
This is a camera that can practically take amazing high quality photos and videos using just a raspberry pi!    

<img width="723" height="689" alt="Screenshot (36)" src="https://github.com/user-attachments/assets/e85f2226-e55f-4eaf-b909-c1dfac0671c9" />


**Hardware**    
This uses a Raspberry pi 4 8gb model and a sandisk luxe pendrive to make sure video recording is fast.      
It uses a Pi HQ Camera which has a sony IMX 477 12.3MP Sensor.      
It even has interchangeable lenses!    
I am powering the whole thing using a cuzor mini ups.
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
