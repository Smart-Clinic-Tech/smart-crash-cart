# smart-crash-cart

Repository: <https://github.com/Smart-Clinic-Tech/smart-crash-cart>

Firmware and design files for the graduation project **Design of a Smart Medical Crash Cart with Access Control and Tamper
Detection** — Majmaah University, College of Applied Medical Sciences, Department of Medical Equipment
Technology. Course: Design Project (0481 BMET), First Semester 1448 H (481), 2026-2027.
Supervisor: Dr. Ahmad Alassaf.

## Team

| Student | Role |
|---|---|
| Abdulsalam Al-Humud | Electronics & Power — Arduino, keypad, servo, supply, wiring |
| Shaher Al-Qarni | Firmware & Logic — PIN state machine, `millis()` timing, alarms, event log, this repository |
| Ibrahim Al-Harbi | Mechanical & Enclosure — drawer unit, locking bar and latch, sensor mounting |
| Khaled Al-Harbi | Testing & Documentation — literature, test protocol, data, report integration |

## What the system does

One servo moves a single locking bar that holds every drawer of a mock crash cart. A 4x3 keypad and a shared
unit PIN release it. A reed switch on each drawer reports open or closed, a housing microswitch and a
vibration module cover tampering, a 16x2 I2C LCD shows the state, and every event is written to a microSD
card with the time from a DS3231 real-time clock.

## Repository layout

| Folder | Content |
|---|---|
| `firmware/` | Arduino sketch and its headers, one folder per version tag |
| `docs/` | State diagram, connection table and circuit drawings used by the firmware |
| `logs/` | Event-log CSV files copied off the SD card during testing |

## Schedule (supervision plan W5-W14)

| Week | Firmware milestone |
|---|---|
| W5 | Repository created; architecture and state diagram agreed |
| W6 | Architecture frozen; state diagram updated to the supervisor's decisions |
| W7 | Gate 1; bench-test the components that have arrived |
| W8 | Prototype Phase 1 — access control proven on the bench, code committed with a version tag |
| W10 | Integration into the cart |
| W11-W13 | Validation runs and the event-log evidence |

No firmware is committed before Week 8: the parts are ordered in Week 6 and bench-tested in Week 7. At the Week 5 submission this repository therefore holds the structure, this README and the `.gitignore` only, and that is the intended state, not an omission.

## Version rule

Firmware versions are tagged `v0.1`, `v0.2`, and so on. Every test log records the firmware version it ran
on. Files follow the project rule `SCC_<content>_v<version>_<YYYYMMDD>`.

## Security note

**No PIN value is ever committed to this repository or written into any project document.** PINs live only in
`firmware/secrets.h`, which is listed in `.gitignore` and never uploaded. `firmware/secrets.h.example` shows
the file's shape with placeholder values; each person copies it to `secrets.h` and fills in the real values
locally.
