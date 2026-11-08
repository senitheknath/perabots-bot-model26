# PeraBots '26 — University Category Final Round

> Autonomous differential-drive robot and competition arena simulation built in **Cyberbotics Webots R2025a** for the PeraBots '26 University Category.

---

## 📌 About the Project

**PeraBots '26 Dev Journey** documents the development, simulation, and autonomous control of our competition robot for the **PeraBots '26 University Category Final Round**. 

The competition challenges autonomous robots to navigate a three-stage multi-terrain arena requiring real-time obstacle avoidance, maze navigation, and precision object manipulation. This repository contains the complete simulation workspace: modular PROTO definitions for the robot and arena, physics and collision models, and Python controller routines.

---

## 🤖 Robot Specifications (`TwoWheelRobot`)

The robot is modeled in Webots as a high-precision differential-drive autonomous platform:

| Parameter | Specification | Details |
|---|---|---|
| **Chassis** | $80\text{ mm} \times 50\text{ mm} \times 30\text{ mm}$ | Lightweight rigid body ($150\text{ g}$) |
| **Drivetrain** | Differential Drive | 2 independent drive wheels + passive rear caster ball |
| **Wheel Dimensions** | Radius $20\text{ mm}$, Width $10\text{ mm}$ | High-traction cylindrical contact |
| **Actuators** | 2x `RotationalMotor` | `left_wheel_motor`, `right_wheel_motor` |
| **Encoders** | 2x `PositionSensor` | `left_wheel_sensor`, `right_wheel_sensor` |
| **Status LEDs** | Dual visual indicators | `led_blue`, `led_green` (competition-compliant status signaling) |
| **Sensor Suite** | 8x `DistanceSensor` | Full $360^\circ$ coverage: front, rear, sides, and $45^\circ$ diagonals |
| **Expansion** | `extensionSlot` | Open slot for custom sensor arrays, cameras, and grippers |

---

## 🏟️ Competition Arena Overview

The arena ($2.44\text{ m} \times 3.66\text{ m}$) consists of three consecutive, interconnected trial zones:

```
+-------------------------------------------------------------+
|        Section 3: The Nine-Point Board (3x3 Grid)           |
|        Dynamic Game Pieces: Green Cubes & Blue Cylinders    |
+-------------------------------------------------------------+
|        Section 2: Labyrinth of Hidden Signs (Maze)          |
|        9x4 Grid of 25cm Cells & Color Markers               |
+-------------------------------------------------------------+
|        Section 1: Obstacle Field                            |
|        2.44m x 1.22m White Floor & Fixed Obstacle Matrix    |
+-------------------------------------------------------------+
                              ▲ START
```

1. **Section 1 — Obstacle Field ($2.44\text{ m} \times 1.22\text{ m}$):** White floor populated with fixed obstacle blocks. Requires agile collision avoidance and pathfinding from the starting pad.
2. **Section 2 — Labyrinth of Hidden Signs ($2.44\text{ m} \times 1.22\text{ m}$):** A $9 \times 4$ maze of $25\text{ cm}$ cells on a black floor featuring colored transition markers. Tests dead reckoning, wall-following, and pattern detection.
3. **Section 3 — The Nine-Point Board ($2.44\text{ m} \times 1.22\text{ m}$):** A $3 \times 3$ grid with collection zones and 6 dynamic $30\text{ g}$ game pieces ($5\text{ cm}$ green cubes and $\varnothing 5\text{ cm} \times 5\text{ cm}$ blue cylinders). Designed for object localization, docking, and manipulation.

---

## 📂 Repository Structure

```plaintext
perabots26-Dev-Journey/
├── controllers/
│   └── main_controller/
│       └── main_controller.py       # Autonomous Python robot controller
├── protos/
│   ├── Arena.proto                  # Complete arena model (floors, walls, dividers)
│   ├── Obstacles.proto              # Section 1 fixed obstacle layout
│   ├── GamePieces.proto             # Section 3 dynamic cubes & cylinders
│   └── TwoWheelRobot.proto          # Differential drive robot model with sensors
├── worlds/
│   ├── Arena.wbt                    # Competition simulation world file
│   └── preview.png                  # World thumbnail preview
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

1. **Webots R2025a** (or later): [Download Webots](https://cyberbotics.com/)
2. **Python 3.10+ (64-bit)**: Installed and added to system `PATH`

### Running the Simulation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/senitheknath/perabots26-Dev-Journey.git
   cd perabots26-Dev-Journey
   ```

2. **Open the Arena:**
   - Launch Webots.
   - Go to **File** > **Open World...** (`Ctrl + O`).
   - Select `worlds/Arena.wbt`.

3. **Start the Controller:**
   - Ensure the robot controller is set to `main_controller`.
   - Click the **Play / Real-time** button ($\blacktriangleright$) on the top Webots toolbar.
   - The robot will start executing autonomous navigation logic.

---

## 🛠️ Tech Stack & Tools

- **Simulation Engine:** [Cyberbotics Webots](https://cyberbotics.com/) (Open-source 3D robot simulator)
- **Programming Language:** Python 3.12
- **Robot Kinematics:** Differential Drive (2-wheel drive + rear caster)
- **Modeling:** VRML97 / Webots PROTO architecture with Open Dynamics Engine (ODE) physics

---

## 👥 Authors

Developed for **PeraBots '26** — University Category.
- **Repository:** [@senitheknath](https://github.com/senitheknath)
