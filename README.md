# 🚀 GALAGA - Mbed Edition

A **C++** reimplementation of the classic arcade game **Galaga**, built for an **Mbed**-compatible board equipped with a **C12832** LCD screen (Mbed Application Board).

The player pilots a ship, shoots down enemies spawning from the right edge of the screen, and tries to rack up the highest score possible without getting hit.

## 🎮 Game Overview

- Vertical movement of the player's ship
- Shooting projectiles to destroy enemies
- Continuous, randomized enemy spawning
- Score tracking system
- Start menu and a help screen (controls)
- "Game Over" screen
- Sound effects via a PWM-driven buzzer
- Hidden cheat codes triggered through joystick input sequences

## 🛠️ Tech Stack

| Component       | Detail                                                              |
|------------------|------------------------------------------------------------------|
| Language         | C++                                                               |
| Platform         | [Mbed OS (classic / mbed-os 2)](https://os.mbed.com) via `mbed.bld` |
| Target board     | Mbed-compatible board (e.g. NXP LPC1768) with Mbed Application Shield |
| Display          | **C12832** LCD controller (128x32, `C12832.lib` library)          |
| Input            | 5-way joystick (`DigitalIn`)                                      |
| Audio output     | Buzzer driven via `PwmOut`                                        |
| Build            | Mbed Online Compiler or Mbed CLI                                  |

## 📁 Project Structure

```
GALAGA/
└── project_galaga/
    ├── main.cpp        # Game logic (main loop, rendering, input, sound)
    ├── mbed.bld         # Reference to the official Mbed library
    ├── C12832.lib       # Reference to the C12832 LCD driver library
    └── .gitignore
```

## 🔌 Wiring / Pins Used

| Function              | Pin(s)                         |
|------------------------|--------------------------------|
| C12832 LCD screen      | `p5`, `p7`, `p6`, `p8`, `p11`   |
| Joystick - Up          | `p15`                           |
| Joystick - Down        | `p12`                           |
| Joystick - Left        | `p13`                           |
| Joystick - Right       | `p16`                           |
| Joystick - Center      | `p14`                           |
| Buzzer (sound)         | `p26`                           |

This pinout matches the **Mbed Application Board**, suggesting the use of a board such as the NXP LPC1768.

## 🕹️ In-Game Controls

- **Right**: shoot
- **Up**: move up
- **Down**: move down
- **Left**: special attack (triggered via a specific key combination)
- **Reset button**: restart the game

## ⚙️ Setup and Build

This project uses the **Mbed** ecosystem, where dependencies are referenced through `.lib`/`.bld` files rather than vendored source code — the standard workflow of the Mbed Online Compiler.

### Option 1 — Mbed Online Compiler
1. Import the `project_galaga` folder into the [Mbed Online Compiler](https://os.mbed.com/compiler/).
2. Dependencies (`mbed`, `C12832`) will be resolved automatically from the `mbed.bld` and `C12832.lib` files.
3. Compile and flash the generated binary (`.bin`) onto the board.

### Option 2 — Mbed CLI (local build)
```bash
mbed import <repo-url>
cd project_galaga
mbed deploy      # fetches the referenced libraries (mbed, C12832)
mbed compile -m <TARGET> -t <TOOLCHAIN>
```
Then copy the generated binary onto the board connected via USB (drag & drop mode).

## ✨ Notable Features

- **Start menu** with a help screen displaying the controls.
- **Game loop** simultaneously handling player movement, shooting, enemies, collisions, and score.
- **Simple collision detection** between projectiles and enemies.
- **Game over screen** triggered on contact with an enemy.
- **Hidden joystick sequences** unlocking bonus effects (special attack, score bonus) — to be discovered in-game.

## 👤 Author

Project by [Yanis-LM5](https://github.com/Yanis-LM5).

## 📄 License

No license is currently defined for this project.