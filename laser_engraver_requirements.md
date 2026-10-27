# Requirements Document: Safe 40×40 cm Laser Engraver

Version 0.1 · Date: October 27, 2026 · Status: draft

## 1. Background and need

We want to design and build a desktop laser engraver (XY gantry type) with a 40 × 40 cm work area, using a 2 W laser module powered at 12 V. The main need is a reliable, affordable machine that is, above all, **safe** to engrave light materials (wood, cardboard, leather, opaque acrylic, etc.).

## 2. Objectives

- Engrave over a usable area of 40 × 40 cm.
- Use a 2 W laser module (optical power to be confirmed) powered at 12 V.
- Provide a level of safety suited to home or workshop use, protecting people, premises and materials.
- Keep the machine simple to build, operate and maintain.

## 3. Scope

**Included:** mechanical structure, X/Y axes, laser module, control electronics, power supply, protective enclosure, safety devices, basic documentation.

**Excluded (for now):** cutting thick materials, engraving bare metals, motorized Z axis, commercial production.

## 4. Functional requirements

| ID | Requirement |
| --- | --- |
| FR-01 | The usable engraving area must be at least 40 × 40 cm. |
| FR-02 | The laser must have a nominal power of 2 W and run on 12 V. |
| FR-03 | Laser power must be adjustable (PWM) from 0 to 100%. |
| FR-04 | The machine must accept standard engraving files (G-code) through open-source software (e.g. LaserGRBL, LaserWeb, Inkscape). |
| FR-05 | A machine origin (homing) must be defined by limit switches on X and Y. |
| FR-06 | Laser focus must be manually adjustable to suit the material thickness. |
| FR-07 | Travel speed must be configurable and suited to engraving (indicative target: up to 3000 mm/min). |

## 5. Safety requirements (top priority)

A 2 W laser is **Class 4** under IEC 60825-1 when its optical power exceeds 0.5 W: it can cause permanent eye injury, skin burns and fires, including from diffuse reflection. The following requirements are therefore mandatory.

| ID | Requirement |
| --- | --- |
| SR-01 | The machine must be fully enclosed in an enclosure opaque at the 450 nm laser wavelength, so that no direct or reflected radiation escapes. |
| SR-02 | An interlock switch must cut the laser when the lid or door is opened. |
| SR-03 | An easily accessible emergency stop must cut power to the laser and motors. |
| SR-04 | A key or enable switch must prevent unauthorized use. |
| SR-05 | An indicator light must clearly show that the machine is powered and the laser is armed. |
| SR-06 | The laser must switch off automatically on communication loss, software error or axis jam. |
| SR-07 | The laser must never turn on at startup or power-up (laser output low by default). |
| SR-08 | Certified protective eyewear, rated for 450 nm (blue) light with sufficient optical density, must be provided and worn at all times during adjustment or testing with the enclosure open. |
| SR-09 | An extraction or ventilation system must remove fumes and particles to the outside or through a suitable filter. |
| SR-10 | Fire protection must be provided (suitable extinguisher nearby, fire-resistant or low-flammability enclosure materials). The machine must never run unattended. |
| SR-11 | Hazardous materials (PVC, vinyl, polycarbonate, chrome-tanned leather, etc.) must be listed as prohibited in the documentation. |
| SR-12 | Class 4 laser warning labels must be affixed to the machine. |
| SR-13 | The 12 V supply must be protected by an appropriately rated fuse, adequately sized wiring and, where applicable, a grounded chassis. |
| SR-14 | Moving parts, belts and connectors must be guarded against pinching and accidental contact. |

## 6. Mechanical requirements

| ID | Requirement |
| --- | --- |
| MR-01 | The structure must be rigid (aluminum extrusions or equivalent) with no noticeable play. |
| MR-02 | External dimensions must allow for the protective enclosure, ventilation and cabling. |
| MR-03 | The flatness of the work surface must keep focus consistent across the whole 40 × 40 cm area. |
| MR-04 | The machine must sit on a stable surface with non-slip feet. |

## 7. Electrical and electronic requirements

| ID | Requirement |
| --- | --- |
| ER-01 | A single 12 V power supply sized with at least a 30% margin over total consumption (laser, motors, electronics). |
| ER-02 | A G-code compatible controller (e.g. GRBL-based) with a PWM output for the laser. |
| ER-03 | Stepper motor drivers matched to the chosen motors. |
| ER-04 | Limit switches and the interlock must be wired fail-safe (a cut wire or a fault stops the machine). |
| ER-05 | The laser module must be adequately cooled (heat sink and fan). |

## 8. Usage and documentation requirements

- A short manual covering assembly, commissioning, the safety test procedure and maintenance.
- A checklist before each use (interlock, emergency stop, ventilation, eyewear, no prohibited materials).
- A list of allowed and prohibited materials.
- A simple log of the initial safety tests.

## 9. Acceptance criteria

1. No measurable or visible laser radiation escapes from the closed enclosure.
2. Opening the lid cuts the laser in under one second.
3. The emergency stop cuts both the laser and the motors.
4. A test engraving covers the whole 40 × 40 cm area correctly.
5. The laser stays off at power-up and after a communication error.
6. Ventilation effectively clears fumes during a test engraving.

## 10. Assumptions and constraints

- The stated 2 W is assumed to be **optical** power; otherwise the classification and protections must be reassessed (modules sold as "10 W" sometimes have only 2 W of optical output, and vice versa).
- The machine is intended for personal or workshop use by informed adult users.
- Regulatory points are summarized in section 12 and must be confirmed before commissioning.
- Budget and schedule are still to be defined.

## 11. Confirmed details and open items

- **Wavelength:** 450 nm (blue diode). Eyewear and enclosure must be rated for this wavelength.
- **Main material:** plywood. Prefer laser-grade or untreated plywood; glues in some plywood produce more smoke and can hinder engraving, so ventilation must be sized for it.
- **Location:** indoors with access to ventilation. Exhaust duct path to the outside still to be defined.
- **Control software:** open source (to be selected, e.g. LaserGRBL or LaserWeb).
- **Still open:** confirmation that 2 W is optical power, budget and schedule.

## 12. Regulatory and compliance notes

For a machine built and used only by its owner, Canadian laser rules appear to apply lightly; the safety requirements in section 5 remain the real protection. This is a summary, not legal advice, as of October 27, 2026.

| Area | What applies | Action |
| --- | --- | --- |
| Federal: Health Canada | The Radiation Emitting Devices Act and its laser regulations govern the sale, lease and import of laser products. Updated regulations took effect on October 9, 2025. They do not appear to cover a single machine built for personal use. | None for personal use. If the machine is ever sold or leased, or laser parts are imported for resale, contact Health Canada's Consumer and Clinical Radiation Protection Bureau (ccrpb-pcrpcc@hc-sc.gc.ca). |
| Quebec: workplaces | CNESST occupational health and safety rules apply to workplaces, not to personal hobby use. | Applies only if the machine is used in a business, school or shared workshop. |
| Municipality | Fire prevention bylaws and, if a duct or building change is needed, the building code. | Check with the municipality before cutting an exhaust opening. |
| Landlord and insurer | Lease terms and home insurance may restrict or exclude home-built equipment. | Ask the landlord (if renting) and the insurer before commissioning. |

Source: [Health Canada, laser products](https://www.canada.ca/en/health-canada/services/consumer-radiation/hand-held-lasers-laser-pointers.html). No Quebec law specific to personal laser use was found; confirm locally.
