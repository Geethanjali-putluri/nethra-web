# PROJECT NETHRA 🚀
### Navigational Eye for Terrain Hazard Reconnaissance & Avoidance

[![Live Demo](https://img.shields.io/badge/Vercel-Live%20Demo-000000?style=for-the-badge&logo=vercel&logoColor=white)](https://nethra-web-three.vercel.app)
[![Tech Stack](https://img.shields.io/badge/Stack-HTML5%20%7C%20CSS3%20%7C%20JavaScript-blue?style=for-the-badge)](https://nethra-web-three.vercel.app)

**Project NETHRA** is an autonomous Unmanned Ground Vehicle (UGV) ground control station and pathfinding simulator engineered for rapid disaster reconnaissance in hazardous, GPS-denied environments. 

The platform allows mission operators to monitor autonomous traversal, place real-time hazard barriers, and evaluate deterministic collision-free detour trajectories across a discrete 2D spatial costmap.

---

## 🌐 Live Deployment

Access the interactive ground control cockpit:  
👉 **[https://nethra-web-three.vercel.app](https://nethra-web-three.vercel.app)**

---

## ✨ Key Features

- **Dynamic A* Path Planning:** Sub-millisecond shortest-path evaluation using an admissible Manhattan distance heuristic ($f(n) = g(n) + h(n)$).
- **Interactive Obstacle Placement:** Real-time costmap modifications that trigger instant route replanning around blocked corridors.
- **Mission Operator Controls:** Supervisory controls including mission launch (`Start`), execution freeze (`Stop / Resume`), and spatial inspection modes.
- **Real-Time Telemetry:** Continuous reporting of current coordinates, remaining path nodes, and total replanning cycles.
- **Fail-Safe Locomotion:** Automated emergency stops when destinations are reached or when all viable paths are blocked.

---

## 📐 Algorithm & System Design

The core engine uses the **$A^*$ (A-Star) search algorithm** operating over a 12×12 discrete coordinate grid:

$$f(n) = g(n) + h(n)$$

- **$g(n)$**: Exact cost from the origin `(0, 0)` to node $n$.
- **$h(n)$**: Admissible Manhattan heuristic $\vert{}x_1 - x_2\vert{} + \vert{}y_1 - y_2\vert{}$ to goal `(11, 11)`.

Because the UGV moves along cardinal grid axes (4-directional), the Manhattan heuristic guarantees an optimal path without overestimating travel costs or evaluating unpromising nodes.

---

## 🛠️ Multi-Phase Engineering Roadmap

- **Phase 1: Deterministic Ground Station (Current)**  
  Zero-dependency client-side simulation, interactive costmap, and operator telemetry dashboard hosted on Vercel.

- **Phase 2: Edge Vision Integration (Prototyped)**  
  Monocular camera ingestion running lightweight **YOLOv8 Nano** inference to identify human survivors and trigger automated safety stops.

- **Phase 3: Hardware Actuation (Planned)**  
  Serial/UART telemetry link forwarding path coordinates to an Arduino/ESP32 differential-drive chassis equipped with HC-SR04 ultrasonic rangefinders.

---

## 🚀 Local Development

No complex installations or package managers required.

1. Clone the repository:
   ```bash
   git clone [https://github.com/](https://github.com/)<YOUR_GITHUB_USERNAME>/nethra-web.git
   cd nethra-web
