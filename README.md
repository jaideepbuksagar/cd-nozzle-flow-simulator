# CD Nozzle Flow Simulator

Interactive simulation of compressible gas flow in **convergent-divergent (CD) nozzles** — covering subsonic, supersonic, and shock-wave regimes across three nozzle wall profiles and two propulsion configurations.

> DE Project, OVGU Magdeburg (SoSe 2025) — Solver Development & UI Design Team.  
> Final submission: August 2025. Interactive app built in Unity/Blender.

---

## Overview

A CD nozzle accelerates gas from subsonic to supersonic velocities through a converging section (throat) followed by a diverging section. This simulator solves the governing 2D compressible gas-dynamics equations numerically and visualises the resulting flow fields interactively.

**Three nozzle wall profiles:**
- **Method of Characteristics (MoC)** — classical irrotational design for shock-free supersonic flow
- **Rao's optimised contour** — industry-standard thrust-optimised profile used in real rocket engines
- **Elliptical profile** — geometric reference case for comparative analysis

**Two propulsion configurations:**
- Rocket engine exit nozzle conditions
- Scramjet engine exit nozzle conditions

---

## Physics

The solver addresses the 2D compressible Euler equations for an ideal gas:

**Continuity:**
$$\frac{\partial \rho}{\partial t} + \nabla \cdot (\rho \mathbf{u}) = 0$$

**Momentum:**
$$\frac{\partial (\rho \mathbf{u})}{\partial t} + \nabla \cdot (\rho \mathbf{u} \otimes \mathbf{u} + p\mathbf{I}) = 0$$

**Energy:**
$$\frac{\partial E}{\partial t} + \nabla \cdot ((E + p)\mathbf{u}) = 0$$

**Regimes modelled:**
- Subsonic: $Ma < 1$ throughout
- Supersonic: $Ma > 1$ in diverging section
- Normal shock: captured numerically in the diverging section

---

## Repository Structure

```
cd-nozzle-flow-simulator/
├── src/
│   ├── solver/
│   │   ├── governing_equations.py    # 2D compressible Euler discretisation
│   │   ├── nozzle_profiles.py        # MoC, Rao, elliptical wall generators
│   │   ├── shock_analysis.py         # Normal shock detection & analysis
│   │   └── boundary_conditions.py    # Inlet/outlet/wall BCs
│   ├── visualisation/
│   │   └── data_grid_export.py       # Structured grid export for Unity
│   └── main.py
├── profiles/
│   ├── moc_contour.dat
│   ├── rao_contour.dat
│   └── elliptical_contour.dat
├── figures/
│   ├── mach_contour_supersonic.png
│   ├── pressure_distribution.png
│   └── shock_location_analysis.png
├── app/                              # Unity/Blender interactive app (binary)
├── report/
│   └── cd_nozzle_report.pdf
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Key Features

- **Nozzle contour generator** — MoC-derived wall profiles for perfectly expanded supersonic flow; Rao contours for maximum thrust; elliptical profiles for geometric comparison
- **Shock capturing** — normal shock position detected and resolved numerically in the diverging section
- **Parametric analysis** — vary inlet stagnation conditions, back pressure ratio, and nozzle geometry
- **Data grid export** — structured output formatted for real-time 3D flow visualisation in Unity
- **Dual configurations** — rocket and scramjet exit conditions with appropriate boundary conditions

---

## Usage

```bash
git clone https://github.com/jaideepbuksagar/cd-nozzle-flow-simulator
cd cd-nozzle-flow-simulator
pip install -r requirements.txt
python src/main.py --profile moc --config rocket
```

**Options:**
```
--profile    moc | rao | elliptical
--config     rocket | scramjet
--mach       target exit Mach number (default: 2.5)
--plot        show flow-field plots
```

---

## Results Preview

*(Figures will be added at final submission, August 2025)*

| Profile | Exit Mach (design) | Shock-free? | Application |
|---|---|---|---|
| MoC | 2.5 | Yes | Research / optimised design |
| Rao | 2.5 | Yes | Rocket engine (industry standard) |
| Elliptical | 2.5 | Partial | Geometric baseline |

---

## Team

6-person cross-functional team, OVGU Magdeburg:
- **Solver team (3):** governing equations, nozzle contour generation, numerical methods
- **App team (3):** Unity/Blender visualisation, UI design, deployment

**My contribution:** mathematical model definition, solver implementation, nozzle contour generation (MoC, Rao, elliptical), shock analysis, data grid generation for visualisation, UI wireframe co-design.

---

## Status

🔄 **In active development** — final submission August 2025.  
Solver core complete. App integration ongoing.

---

## License

MIT

---

## Author

**Jaideep Buksagar** — Solver Development & UI Design  
MSc Chemical & Energy Engineering, OVGU Magdeburg  
[GitHub](https://github.com/jaideepbuksagar) · [LinkedIn](https://linkedin.com/in/[handle])
