# AI-Now PCB Templates

**Standardized KiCad PCB Design Templates for OSHPark Fabrication**

A collection of reusable **KiCad PCB project templates** developed for **AI-Now Technology, Inc.**, designed to accelerate hardware development, maintain consistent PCB design standards, and simplify manufacturing through [OSHPark](https://oshpark.com/).

The repository provides ready-to-use **2-layer and 4-layer PCB templates** with predefined project structures and fabrication-oriented design guidelines.

## Features

- **Standardized PCB Projects** — Reusable KiCad templates for consistent hardware development.
- **OSHPark-Oriented Design** — Design guidelines tailored to OSHPark PCB fabrication services.
- **2-Layer and 4-Layer Support** — Suitable for general electronics, embedded systems, and compact digital hardware.
- **Rapid Prototyping** — Reduce repetitive project setup and accelerate PCB development.
- **Reusable Project Structure** — Includes schematic, PCB layout, worksheet configuration, and project metadata.
- **Engineering Consistency** — Establish common PCB development practices across AI-Now hardware projects.

## Repository Structure

```text
AI-Now-PCB-Templates/
├── OshPark-2Layer/
│   ├── OshPark-2Layer.pro
│   ├── OshPark-2Layer.sch
│   ├── OshPark-2Layer.kicad_pcb
│   ├── OshPark-2Layer-cache.lib
│   ├── default.kicad_wks
│   └── meta/
│
└── OshPark-4Layer/
    ├── OshPark-4Layer.pro
    ├── OshPark-4Layer.sch
    ├── OshPark-4Layer.kicad_pcb
    ├── OshPark-4Layer-cache.lib
    ├── default.kicad_wks
    └── meta/
```

### File Descriptions

| File | Description |
|---|---|
| `*.pro` | Legacy KiCad project configuration |
| `*.sch` | Legacy KiCad schematic document |
| `*.kicad_pcb` | PCB layout and board configuration |
| `*-cache.lib` | Cached schematic symbols |
| `default.kicad_wks` | Custom drawing sheet and title block |
| `meta/` | Project previews, icons, and documentation |

> **KiCad Compatibility:** These templates use legacy KiCad project and schematic formats. Modern KiCad releases use `.kicad_pro` and `.kicad_sch`. Conversion may be required when opening the templates in newer versions.

## OSHPark PCB Specifications

The templates target two common PCB fabrication configurations.

### 1. OSHPark 2-Layer PCB

**Directory:** `OshPark-2Layer/`

Designed for general-purpose electronics, microcontroller boards, sensor interfaces, and embedded hardware prototypes.

| Parameter | Specification |
|---|---|
| Copper Layers | 2 |
| Layer Configuration | Front / Back |
| Minimum Trace Width | 6 mil (0.1524 mm) |
| Minimum Trace Spacing | 6 mil (0.1524 mm) |
| Minimum Finished Drill | 10 mil (0.254 mm) |
| PCB Material | FR-4 |
| Surface Finish | ENIG |
| Solder Mask | Purple |

**Recommended Applications:**

- Microcontroller development boards
- Sensor interface modules
- Low-speed digital circuits
- Analog signal conditioning
- IoT hardware prototypes
- General-purpose embedded electronics

### 2. OSHPark 4-Layer PCB

**Directory:** `OshPark-4Layer/`

Designed for compact electronic systems requiring improved signal integrity, dedicated reference planes, and more efficient power distribution.

| Parameter | Specification |
|---|---|
| Copper Layers | 4 |
| Top Layer | Signal |
| Inner Layer 1 | Ground Plane |
| Inner Layer 2 | Power Plane |
| Bottom Layer | Signal |
| Minimum Trace Width | 5 mil (0.127 mm) |
| Minimum Trace Spacing | 5 mil (0.127 mm) |
| Minimum Finished Drill | 10 mil (0.254 mm) |
| PCB Material | FR-4 |
| Surface Finish | ENIG |
| Solder Mask | Purple |

**Recommended Applications:**

- Compact embedded computing boards
- ESP32 and ARM microcontroller systems
- Mixed-signal electronics
- Multi-voltage digital circuits
- High-density component layouts
- Medium-speed digital interfaces

### Recommended 4-Layer Stackup

```text
+--------------------------------+
| L1 - Top Signal Layer          |
+--------------------------------+
| FR-4 Dielectric                |
+--------------------------------+
| L2 - Ground Plane              |
+--------------------------------+
| FR-4 Core                      |
+--------------------------------+
| L3 - Power Plane               |
+--------------------------------+
| FR-4 Dielectric                |
+--------------------------------+
| L4 - Bottom Signal Layer       |
+--------------------------------+
```

A continuous ground reference plane helps reduce return-path impedance and electromagnetic interference.

For high-speed signals, impedance calculations must use the actual fabrication stackup, including dielectric thickness and copper weight.

> **Fabrication Note:** The values above are template design targets. Verify current manufacturing capabilities, drill requirements, annular rings, clearances, and stackup dimensions against the official [OSHPark documentation](https://docs.oshpark.com/) before fabrication.

## Getting Started

### Prerequisites

- KiCad EDA installed
- Git
- Linux, macOS, or another KiCad-supported operating system
- Basic familiarity with schematic capture and PCB layout

### 1. Clone the Repository

```bash
git clone \
  https://github.com/johntsaiainow/AI-Now-PCB-Templates.git

cd AI-Now-PCB-Templates
```

### 2. Create a New PCB Project

Choose the appropriate template.

**For a 2-layer PCB:**

```bash
cp -r OshPark-2Layer \
  ../my-new-hardware-project
```

**For a 4-layer PCB:**

```bash
cp -r OshPark-4Layer \
  ../my-new-hardware-project
```

### 3. Open the Project in KiCad

Navigate to the new project directory and open its legacy `.pro` project file using a compatible KiCad version.

For newer KiCad releases, use the appropriate legacy project import or conversion workflow.

After conversion, save the project using modern KiCad file formats when applicable.

### 4. Customize Your Design

1. Rename the project files to match your hardware project.
2. Update the schematic and component symbols.
3. Assign footprints to components.
4. Configure the board outline and mechanical dimensions.
5. Verify copper layer assignments.
6. Review track widths, clearances, and via dimensions.
7. Complete component placement and routing.
8. Run electrical and design rule checks.

## PCB Design Guidelines

### Trace Width and Spacing

Maintain the minimum fabrication clearances appropriate for the selected PCB service.

Use wider traces where necessary for current-carrying capability, voltage drop, and thermal performance.

### Grounding

For 2-layer designs:

- Use ground copper pours where practical.
- Maintain short return-current paths.
- Minimize unnecessary ground-plane interruptions.

For 4-layer designs:

- Prefer a continuous ground reference plane.
- Place decoupling capacitors close to device power pins.
- Minimize high-speed signal transitions between reference planes.
- Avoid routing critical signals across reference-plane splits.

### Power Distribution

- Size power traces and planes according to expected current.
- Use appropriate copper widths for high-current circuits.
- Place bulk and local decoupling capacitors strategically.
- Review thermal performance of regulators and power components.

### Design Rule Checks

Before generating manufacturing files:

- Run KiCad Electrical Rules Check (ERC).
- Run KiCad Design Rules Check (DRC).
- Verify drill sizes and annular rings.
- Check board-edge clearances.
- Inspect copper zones and unconnected nets.
- Confirm all footprints and mechanical dimensions.

## Manufacturing with OSHPark

Once the PCB design is complete, prepare the manufacturing files.

### Generate Gerber Files

In KiCad PCB Editor:

1. Open **File → Fabrication Outputs → Gerbers**.
2. Select the required copper, solder mask, silkscreen, and board outline layers.
3. Generate Gerber files.
4. Generate Excellon drill files.
5. Review the outputs using a Gerber viewer.

### Package Manufacturing Files

From the directory containing the generated fabrication files:

```bash
zip -r pcb-fabrication.zip \
  *.gbr *.drl
```

Adjust the command if your KiCad version uses different output extensions.

### Submit to OSHPark

Visit:

https://oshpark.com/

Upload the Gerber archive or another supported board file.

Review the fabrication preview, verify layer alignment, and confirm the selected manufacturing service before placing an order.

## Engineering Workflow

The recommended hardware development process is:

```text
Project Requirements
        |
        v
Select PCB Template
        |
        v
Schematic Design
        |
        v
Component Selection
        |
        v
PCB Layout
        |
        v
ERC / DRC Verification
        |
        v
Gerber Generation
        |
        v
OSHPark Fabrication
        |
        v
PCB Assembly
        |
        v
Hardware Validation
        |
        v
Design Revision
```

This workflow supports repeatable hardware development from initial prototypes through validated PCB revisions.

## Future Improvements

Potential repository enhancements include:

- Migration to current KiCad project formats
- Preconfigured KiCad design rule files
- OSHPark fabrication profiles
- Standardized board title blocks
- PCB revision and version tracking
- Automated DRC validation
- GitHub Actions integration
- Additional PCB stackup templates
- Standardized component libraries
- Automated fabrication output generation

## License & Attribution

Copyright © AI-Now Technology, Inc.

Developed and maintained as part of the hardware engineering standards of **AI-Now Technology, Inc.**

The repository is intended to provide reusable PCB design foundations for hardware engineering and rapid prototyping.

No open-source license is implied unless a separate `LICENSE` file is provided.

## Maintainer

**AI-Now Technology, Inc.**  
Hardware Engineering

**Repository:** [AI-Now-PCB-Templates](https://github.com/johntsaiainow/AI-Now-PCB-Templates)

---

*From schematic to silicon, building reliable hardware begins with a solid foundation.*
