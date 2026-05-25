# SEA/SKY-6 CMS -- Weapons Control Console

A browser-based submarine combat management system (CMS) simulator with a fully interactive weapons fire control console. Built as a single HTML file with no external dependencies.

> **SIMULATION ONLY -- NOT FOR OPERATIONAL USE. All contacts are simulated.**

---

## Overview

SEA/SKY-6 CMS is a fictional tactical interface modeled after submarine fire control systems. It simulates the full weapon engagement cycle: contact tracking, target designation, tube preparation, firing authorization, and post-launch wire guidance. The aesthetic is a phosphor-green monochrome terminal running on a black background, styled after real naval CMS displays.

---

## Features

### Contact Management
- Live-generated sonar contacts with randomized bearing, range, speed, and threat classification
- Color-coded contact types: Hostile (red), Unknown (amber), Friendly (green), Neutral (blue)
- Per-contact threat level assignment via dropdown (HIGH / MEDIUM / LOW / UNKNOWN)
- Click a row to select a contact; right-click the tactical plot to designate it as a target

### Tactical Fire Control Plot
- Animated polar plot showing own-ship at center and all contacts in real time
- Click a contact on the plot to select it
- Right-click any contact on the plot to designate it as the firing target
- Selected and targeted contacts are visually distinguished

### Target Motion Analysis (TMA)
- Bearing (BRG), range (RNG), speed (SPD), and probability of kill P(K) update every 2 seconds for the selected contact
- P(K) color codes: red above 70%, amber 40--70%, green below 40%
- TMA values feed directly into weapon preset calculations

### Tube and Weapon Status
- Four torpedo tubes with independent state machines: LOADED > FLOODED > READY > FIRED
- Supported weapons: MK-48 ADCAP, MK-48 MOD7, UUM-44 SUBROC, BGM-109 TLAM
- Per-tube weapon type selection via dropdown
- Reload workflow appears automatically after a tube fires or a torpedo detonates

### Weapon Preset Parameters
- Depth limit slider (50--800 m)
- Enable range slider (200--5000 m)
- Homing mode selector: ACTIVE/PASSIVE, PASSIVE ONLY, ACTIVE ONLY, WAKE HOMING
- Search pattern fixed at SNAKE-6
- Presets are uploaded to the active tube before firing

### Interlocks and Authorization
- Four independent interlocks must all be enabled before firing: FIRE AUTH KEY, CO CONFIRM, XO CONFIRM, FLOOD CONFIRMED
- Dual-trigger fire sequence: FIRE A arms the system (red glow, blinking); FIRE B completes the shot within a time window
- Interlock violations are logged as critical events

### Wire Guidance Control
- Post-launch steering via arrow buttons or numpad (8/4/6/2) for depth and course
- Speed command slider (10--55 kt)
- Wire pays out automatically; torpedo goes autonomous at the 18,000 m limit
- CUT WIRE severs guidance immediately; ENABLE HOMING activates the onboard seeker

### Event and Fire Control Log
- Timestamped log of every system action
- Color-coded severity: green (informational), amber (warning / state change), red (critical: fires, detonations, interlock violations)
- Auto-scrolls; supports manual scroll-up to review history
- Detonation events record which torpedo destroyed which contact

---

## Fire Sequence

1. Click a tube card to select it as the active tube (must be LOADED)
2. Designate a target via right-click on the plot or the TGT button in the contact list
3. Click **FLOOD & EQUALIZE** -- tube border turns amber and blinks
4. Click **OUTER DOOR OPEN** -- tube border turns solid green (READY)
5. Optionally click **UPLOAD PRESET** to push depth and enable-range settings
6. Enable all four interlocks
7. Press **[ FIRE A ]** -- button arms with red glow
8. Press **[ FIRE B ]** within the window -- weapon away

---

## Usage

Open `index.html` in any modern browser. No build step, no server, no dependencies required.

```
open index.html
```

The simulation starts automatically: sonar contacts appear within the first few seconds and the clock begins running from 00:00:00Z.

A built-in tutorial section is accessible via the **TUTORIAL** button in the header bar.

---

## Browser Compatibility

Tested in modern Chromium-based browsers and Firefox. Requires a screen wide enough to display the multi-column grid layout comfortably (recommended minimum: 900px). A responsive breakpoint at 800px and 500px collapses the grid to a single column for narrower viewports.

---

## Project Structure

```
index.html    -- entire application (HTML, CSS, JS in one file)
README.md     -- this file
```

---

## Disclaimer

This project is a creative simulation for entertainment and interface design purposes only. It does not represent real weapons systems, real naval doctrine, or real operational procedures. All contacts, weapons, and system behaviors are entirely fictional.
