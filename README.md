# Axiom Build Roadmap

An interactive build plan for **Axiom**, my voice-activated AI assistant hardware project: a table-mounted claw that wakes when someone walks up and says "Axiom", reasons through the Claude API, and answers through a salvaged Echo speaker.

**Live demo:** https://robertmartinez19.github.io/AxiomBuildRoadmap/

## System architecture

| Part | Role |
|---|---|
| VL53L8 ToF sensor (ST) | Presence detection, gates the wake word |
| NUCLEO-N657X0-Q (STM32N6) | On-device wake-word detection ("the ears") |
| MacBook + Claude API | Speech in, reasoning, speech out ("the brain") |
| Arduino Uno + SG90 servos | Claw control with a ToF grip check ("the hands") |
| PAM8403 amp + salvaged Echo driver | Audio output ("the mouth") |

Layered wake design: the ToF sensor moves the system from **Idle** to **Alert**, but only the spoken wake word moves it to **Awake**. Presence alone never triggers a response, which cuts false triggers and keeps wake-word inference off when nobody is there.

## Build phases

1. **Arduino fundamentals:** digital I/O, analog input, PWM servo control
2. **ToF sensor evaluation:** bring-up on ST Nucleo hardware plus a real-world characterization matrix (lighting, distance, angle)
3. **Axiom capstone:** presence gate, wake word, serial bridge, claw, and audio, integrated and documented

## The page

A single self-contained HTML file with no build step and no framework. It has an animated wiring diagram with a step-by-step wake simulation, per-phase progress tracking saved in the browser, and light/dark themes. It also respects the system's reduced-motion setting.
