# Robot Framework MBT Adapter

A **generic Model-Based Testing adapter** for [Robot Framework](https://robotframework.org), starting with **AltWalker** as the first supported engine.
The project enables seamless integration between Robot Framework and MBT engines, with advanced techniques such as **path and data generation**, **rich logging**, **guard-condition evaluation**, **end criteria based on coverage matrics** and both **online** and **offline** MBT approaches — with planned support for multiple engines.

---

## 🎯 Motivation and Goals

Model-Based Testing (MBT) provides a powerful way to design, visualize, and execute tests based on system behavior models or just system models.  
While Robot Framework excels at keyword-driven automation, its native support for MBT workflows has been limited to a few small-scale libraries or academic prototypes.

The **goal** of this project is to build a flexible, visual, and extensible bridge between Robot Framework and modern MBT engines — starting with AltWalker and later supporting custom or external model execution “brains”.

During this development, special attention is given to creating a solution that integrates naturally into a tester’s workflow, covers the practical gaps of different MBT engines, and remains well-aligned with standard Robot Framework logging, reporting, and dashboarding systems — without shifting too much logic outside the executable test itself. This balance between graphical model execution and textual keyword-driven testing is one of the key design challenges and ambitions of the project.

---

## Core Principles (Vision and Concept)
- **Generic architecture:** decoupled adapter layer connecting Robot Framework to any MBT engine (AltWalker, GraphWalker, custom).
- **Native RF integration:** models can be executed directly inside `.robot` suites without new syntax.
- **Advanced MBT techniques:** path and data generation, guard-condition evaluation, randomization, and reproducibility (via seeds or pregenerated static scenarios).
- **Rich reporting:** native Robot Framework logs + visual heatmaps, and timeline tracking.
- **Online & offline MBT:**  
  - *Online* – dynamically driven by a running model engine (e.g., AltWalker).  
  - *Offline* – generated test cases or paths exported and replayed in Robot Framework.
---

## 🧩 Why Build a New Adapter?

Existing MBT solutions for Robot Framework (like `robotframework-mbt` or `RoboMachine`) provide basic functionality but lack:
- true model visualization within the Robot test context
- support for external engines and mixed online/offline execution
- flexible guard- and data-driven execution.

This adapter focuses on **extensibility and transparency** — allowing developers to use models visually, run them inside Robot Framework, and later swap or extend the underlying MBT engine without changing their tests too much.

---

## 🔍 Overview of Existing MBT Solutions

| Tool | Type | Strengths | Limitations |
|------|------|------------|-------------|
| **AltWalker** | Open-source MBT engine built on GraphWalker | Mature EFSM support, visual editor, path generation | External to RF, requires manual integration |
| **GraphWalker** | Java MBT core engine | Powerful path generation, coverage metrics | No native Python/RF integration |
| **robotframework-mbt** | RF library | Runs MBT models directly in RF | Limited visualization and engine flexibility |
| **RoboMachine** | EFSM model generator | Simple syntax, lightweight | Focused on web demos, limited community |
| **Axini AMP** | Commercial platform | Advanced symbolic transition systems, formal coverage | no adapter for RF, maybe dificult to integrate with RF as runner |
| **TorXakis** | Open-source academic tool | Strong in formal testing and protocols | Complex setup |

---