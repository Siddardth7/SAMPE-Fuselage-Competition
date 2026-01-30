# SAMPE Fuselage Competition (2024‑2025)

## Overview

This repository contains the design, analysis and manufacturing records for a student‑built composite fuselage section created for the 2025 **SAMPE Student Chapter Fuselage Competition**.  The aim of the competition is to design, fabricate and test a glass‑fibre fuselage section that satisfies strict geometric constraints while withstanding at least **1 000 lbf** in three‑point bending with **< 1 inch** deflection.  Our team at the University of Illinois developed a sandwich fuselage using an E‑glass/epoxy skin and Nomex honeycomb core, optimized the laminate through analytical, numerical and experimental methods, built the part via vacuum‑bagged prepreg layup and autoclave cure, and validated the final structure in a universal testing machine.

## Objective

The project’s objectives were to:

* Comply with the **SAMPE fuselage design rules** (≥ 24 in length, 5.5–6 in diameter, four door cut‑outs, fibreglass only) and achieve a minimum **load capacity of 1 000 lbf** with less than **1 inch deflection**.
* Minimise weight while maintaining bending stiffness by selecting the appropriate number of plies, fibre orientations and core thickness.
* Design cut‑outs and stiffeners to minimise stress concentrations around the door openings.
* Develop a repeatable manufacturing process using prepreg layup, vacuum bagging and autoclave cure.
* Demonstrate the finished fuselage in a three‑point bending test and document performance.

## My Role

As part of a four‑person team I:

* Generated the **CAD model** of the fuselage and cut‑outs in SolidWorks and prepared drawings for manufacturing.
* Carried out **Classical Laminate Theory** calculations and wrote a **Python optimisation script** (`code/layup_optimizer.py`) to explore symmetric, balanced stacking sequences.  The program uses simulated annealing to maximise bending stiffness while controlling weight and enforcing symmetry and ply‑percentage constraints.
* Performed **finite‑element simulations** in Abaqus to estimate displacements and stresses for candidate layups; the chosen configuration produced ~2.5 mm displacement under design load.
* Evaluated manufacturing methods and selected **vacuum‑bagged prepreg layup with Nomex core** as the most cost‑effective process.  I documented risk sources (vacuum leaks, uneven pressure, resin pooling, porosity and environmental variability) and mitigation strategies.
* Led **layup and curing** in the composites lab, including core bonding, vacuum bagging, autoclave cure and trimming.  Process photos are available under the `images/` directory.
* Conducted the **three‑point bending test** and recorded load–deflection data.  The fuselage carried **≈ 2.6 kip** (≈ 2 590 lbf) at failure with **≈ 0.74 in deflection**, exceeding the competition requirements.
* Wrote the final design report, manufacturing report, risk assessment and presentation slides (see `docs/`).

## Technical Details

- **Materials:**
  - **Skins:** Woven **E‑glass/epoxy prepreg** (7781 E‑glass) chosen for cost and availability; S‑glass was analysed but deemed unnecessary after simulations predicted acceptable deflection with E‑glass.
  - **Core:** **Nomex honeycomb**, bonded between inner and outer skins to form a sandwich structure; core thickness selected based on stiffness–weight trade‑off.
  - **Adhesive:** Film adhesive (epoxy) used to bond core to skins.

- **Manufacturing & Analysis Methods:**
  - **Analytical design:** Classical Laminate Theory used to compute bending stiffness and first‑ply failure for candidate stacking sequences; results informed fibre orientation choices.  A **simulated annealing algorithm** (see `code/layup_optimizer.py`) searched for symmetric, balanced layups that maximise stiffness with minimum weight and 10 % ply‑orientation quotas.
  - **Finite‑element simulation:** 3D models built in **Abaqus** predicted a maximum displacement of ~2.5 mm for the selected layup under 1 000 lbf bending load.
  - **Manufacturing:**
    1. **Prepreg cutting:** Fibreglass prepreg, peel‑ply, release film, breather and vacuum bag were cut to size.  Core sections were cut from Nomex honeycomb.
    2. **Layup:** Layers were wrapped on a mandrel in the sequence [–45/0/45/90/Core/90/45/0/–45]s (symmetric with eight plies per face).  Light debulking was performed every four plies to remove air.
    3. **Core bonding:** Nomex core bonded to first skin using film adhesive; second skin laid on top.
    4. **Vacuum bagging:** The laminate stack was sealed with bag film, breather and tape; vacuum ports were attached, and the assembly was leak‑checked.
    5. **Autoclave cure:** Cured according to the prepreg cycle (ramp to cure temperature, hold, then cool).  A small amount of shrink tape provided radial compression.
    6. **Trimming & cut‑outs:** After cure, the fuselage was trimmed to 24 in length and four circular cut‑outs (≈ 2.5 in diameter) were machined per competition rules.
  - **Testing:** A **three‑point bending test** on a universal testing machine measured load and deflection.  The fuselage withstood **≈ 2.59 kip** before catastrophic failure with maximum deflection **≈ 0.74 in** at mid‑span, meeting the < 1‑inch deflection requirement at the specified 1 000 lbf load.

- **Tools & Software:** SolidWorks, Abaqus/CAE, Python (NumPy), Pandoc, universal testing machine (Instron), autoclave, vacuum pump and leak detector.

- **Standards & Constraints:** All work followed the **SAMPE Student Chapter Fuselage Contest Rules (2024‑25)**, which prescribe geometry (24 in minimum length; 5.5–6 in diameter), material restrictions (fibreglass only), four door cut‑outs per fuselage, and a design load of 1 000 lbf with ≤ 1 in deflection.

## Key Results

| Metric                     | Value / Outcome                        |
|---------------------------|----------------------------------------|
| FEA predicted deflection | ~2.5 mm at 1 000 lbf (Abaqus)          |
| Final layup              | [–45/0/45/90/Core/90/45/0/–45]s        |
| Manufactured length      | 24 in                                  |
| Outer diameter           | 6 in (5.5 in inner diameter)           |
| Number of cut‑outs       | 4 (2 per side, 2.5 in diameter)        |
| Test load at failure     | ≈ 2.59 kip (≈ 2 590 lbf)               |
| Deflection at failure    | ≈ 0.74 in                              |
| Weight                   | (not measured)                         |

## Engineering Challenges

* **Layup symmetry and balance:** Achieving a symmetric, balanced laminate with the required 0°, ±45° and 90° percentages while minimising ply count was non‑trivial.  The simulated annealing tool accelerated this search and identified an eight‑ply skin as optimal.
* **Vacuum integrity:** Minor leaks during vacuum bagging caused inconsistent consolidation.  The team used leak detectors and extra sealant tape to reduce porosity.
* **Core bonding:** Ensuring full adhesion between Nomex and skins without crushing the core required careful pressure control; shrink tape and breather materials assisted.
* **Stress concentration around cut‑outs:** The door cut‑outs introduced local stress raisers.  Choosing a woven prepreg and adding extra plies around openings mitigated these effects.
* **Testing fixture compliance:** Aligning the fuselage in the three‑point bending rig and preventing rotation during loading demanded fixturing modifications.

## What This Demonstrates

This project showcases skills and experience relevant to composites design and manufacturing roles:

* **Composite structures:** Deep understanding of classical laminate theory, ply orientation effects and sandwich construction.
* **Structural simulation:** Experience using Abaqus for FEA and interpreting deflection, stress and failure results.
* **Algorithm development:** Implemented a simulated annealing optimiser to automate layup selection under multiple constraints.
* **Hands‑on manufacturing:** Fabricated a composite fuselage via prepreg layup, vacuum bagging and autoclave curing; performed trimming and finishing.
* **Testing & validation:** Conducted a full‑scale three‑point bending test and analysed load–deflection behaviour against design requirements.
* **Risk management:** Identified and mitigated risks in vacuum bagging (leaks, uneven pressure, resin pooling, voids and environmental factors), documenting strategies for quality control.
* **Team collaboration & communication:** Coordinated with teammates to balance design, analysis and manufacturing tasks and produced comprehensive reports and presentations.

## Documentation

The `docs/` folder contains the full project documentation:

| File | Description |
|-----|------------|
| **AE526_Final_Report.pdf** | Detailed design report including literature review, analytical calculations, FEA results and first ply failure analysis. |
| **Manufacturing_Report.pdf** | Comprehensive manufacturing report covering material selection, process evaluation, detailed prepreg layup steps, vacuum bagging procedure, autoclave cure schedule, risk assessment and mitigation strategies. |
| **Risk_Analysis.docx** | In‑depth risk and mitigation analysis for vacuum bagging, highlighting critical failure modes (bag leaks, uneven pressure, resin pooling, porosity, environmental factors) and recommended controls. |
| **Layup_Info.docx** | Literature survey summarising optimal ply counts, fibre orientations and symmetric/balanced stacking sequences for cylindrical fuselages. |
| **Competition_Rules.pdf** | Official SAMPE Student Chapter Fuselage Competition rules (2024‑25 edition). |
| **AE526_Presentation.pdf** | Slide deck summarising the design, manufacturing process and results for the course presentation. |

Process photos, FEA plots and test images are in the `images/` folder, while source code for the layup optimiser resides in `code/` and the SolidWorks model in `cad/`.

## Notes

* **NDA considerations:** All information provided here pertains to a student competition project and is publicly shareable.  No proprietary data or confidential sponsor information is included.
* **Future work:** Improving core modelling in simulations, exploring S‑glass skins for higher stiffness, performing additional testing to measure weight and failure modes, and refining cut‑out reinforcement methods.