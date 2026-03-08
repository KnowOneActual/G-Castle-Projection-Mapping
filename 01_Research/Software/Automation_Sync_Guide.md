# 04 - Sync & Automation Guide (DMX & Audio)

To turn the G-Castle from a simple video loop into a professional, multi-sensory show, you need to sync the projection with music and (optionally) Christmas lights.

## 🛠️ The Core Software Stack (Industry Standards)

| Software | Role | Why? |
| :--- | :--- | :--- |
| **xLights** | **The Sequencer** | The "Director" of your show. This is where you line up your music, your lights (DMX/Pixels), and your video files on a single timeline. |
| **Falcon Player (FPP)** | **The Show Player** | The "Brain." Typically runs on a Raspberry Pi or BeagleBone. It plays the final sequences and sends the video signal to the projector and the DMX signal to your lights. |

---

## 🏗️ Automation Architecture

### 1. The "Master-Remote" Setup
If the G-Castle is large and you have lights in different areas, you can use **FPP Multi-Sync**:
*   **FPP Master:** A Raspberry Pi in the house that plays the audio and sends sync commands over your home network (Wi-Fi or Ethernet).
*   **FPP Remote (The Projector):** A second Raspberry Pi (running FPP) located at the projector. It receives the sync signal and plays the high-res video file locally to ensure no lag.

### 2. Audio Synchronization
*   **FM Transmitter:** Connect a low-power FM transmitter to the FPP Master Pi. This allows cars passing by the castle to "tune in" to your show on their radio.
*   **Outdoor Speakers:** For people walking by, you can use weatherproof outdoor speakers connected to the same Pi.

### 3. DMX/Pixel Integration
If you have Christmas lights (Pixels/LEDs) on the castle turrets:
*   **E1.31 (DMX over Ethernet):** xLights sends light data over your network to a pixel controller (like a Falcon Controller or Kulp Controller). 
*   **Video-as-Light:** You can actually "sequence" your projection in xLights by treating the projector as a "Virtual Matrix" of lights.

---

## 🔄 Step-by-Step Workflow for Sync

1.  **Import Music:** Drop your MP3 or WAV file into xLights.
2.  **Add Your Projector:** Define a "Virtual Matrix" in xLights that matches the resolution of your projector.
3.  **Place Video Assets:** Drop your DaVinci Resolve renders onto the Virtual Matrix layer.
4.  **Add Light Effects:** Sequence your physical lights to "chase" or flash in time with the video.
5.  **Export to FPP:** Use "FPP Connect" in xLights to push your show files to your Raspberry Pi.
6.  **Schedule the Show:** Use FPP's built-in scheduler to make the show start automatically at 6:00 PM every night.

---

## 📝 Next Research Steps
*   [ ] Decide if you want to use **FM Transmission** for audio.
*   [ ] Determine if you need **one or two Raspberry Pis** (depending on projector distance from the house).
*   [ ] Create a basic 30-second test sequence in xLights.
