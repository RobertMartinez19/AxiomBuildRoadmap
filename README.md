# Axiom Build Roadmap

An interactive build plan for **Axiom**, my voice-activated AI assistant hardware project: a desk-sized, expressive robotic arm that turns to face you when you walk up, wakes when you say "Axiom", reasons through the Claude API, gestures while it talks, and answers through a salvaged Echo speaker.

**Live demo:** https://robertmartinez19.github.io/AxiomBuildRoadmap/

## Where the build is at (Sep 27, 2026)

| Piece | Status |
|---|---|
| Software brain (Python + Claude API) | ✅ Running: wake word (openWakeWord placeholder model), conversation mode, interruptible replies, ElevenLabs voice, long-term memory, screen vision, web search, floating holographic UI |
| ST evaluation kits | 📦 Received, not yet powered |
| Arduino fundamentals, ToF bring-up | ⏳ Next |
| Arm design | 🤝 Starting, with a mechanical-engineer partner (CAD + 3D printing) |
| Arm build, N6 wake word, presence gate | ⏳ Planned |

Budget target: $0, built only from parts already on hand.

## System architecture

| Part | Role |
|---|---|
| VL53L8 ToF sensor (ST) | Presence detection that gates the wake word; its 8×8 zones also tell which side you're on |
| NUCLEO-N657X0-Q (STM32N6) | On-device wake-word detection ("the ears") |
| MacBook + Claude API | Speech in, reasoning, speech out ("the brain") |
| Arduino Uno + 4× SG90 servos | Shoulder, elbow, wrist, and gripper ("the arm") |
| P-NUCLEO-IHM03 gimbal motor (FOC) | Smooth base rotation to face you |
| SATEL-VL53L8 | Grip check at the gripper |
| PAM8403 amp + salvaged Echo driver | Audio output ("the mouth") |
| 3D-printed shells | Matte black, round joint drums, curved links, parallel gripper |

Layered wake design: the ToF sensor moves the system from **Idle** to **Alert** (and turns the base toward you), but only the spoken wake word moves it to **Awake**. Presence alone never triggers a response, which cuts false triggers and keeps wake-word inference off when nobody is there.

## Build phases

1. **Arduino fundamentals:** digital I/O, analog input, PWM servo control
2. **ToF sensor evaluation:** bring-up on ST Nucleo hardware plus a real-world characterization matrix (lighting, distance, angle)
3. **Axiom capstone:** speaker, presence gate, wake word, serial bridge, arm, base rotation, and expressive gestures, integrated and documented

## The page

A single self-contained HTML file with no build step and no framework. It has a build log, an animated wiring diagram with a step-by-step wake simulation, per-phase progress tracking saved in the browser, and light/dark themes. It also respects the system's reduced-motion setting.
