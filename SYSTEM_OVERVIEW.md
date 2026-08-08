# System Overview

## Purpose

LoRaWAN Industrial Site Monitoring Demo is an industrial HMI application for Elecrow CrowPanel ESP32-P4 panels. It presents the operating state of a beverage production and bottling plant as one connected process.

The application combines equipment telemetry, communication status, warnings, trends, and guided fault scenarios in a touchscreen interface intended for local plant monitoring.

![Industrial site overview](images/site-overview.png)

## Plant Model

The simulated site contains six connected production areas:

- **Production Hall A** — water preparation, mixing, pumps, motors, and process lines;
- **Production Hall B** — filling, packaging, conveyors, compressors, and production environment;
- **Utilities Area** — process water, cooling, compressed air, and power distribution;
- **Tank Farm** — storage tanks, transfer pumps, valves, and pipelines;
- **Warehouse** — cold storage, gates, lighting, leakage, and environmental monitoring;
- **Outdoor Infrastructure** — drainage, outdoor cabinets, remote pumps, tanks, and meters.

The model contains 60 LoRaWAN devices. Device types include tank monitors, pump and motor condition sensors, flow and pressure nodes, environmental sensors, energy meters, actuator controllers, warehouse nodes, and outdoor utility nodes.

## Process Relationships

Equipment values are connected through a common plant model rather than changing independently. Examples include:

- tank level and valve position affect available process flow;
- pump condition affects pressure, flow, current, vibration, and temperature;
- utility cooling affects production equipment temperature;
- Hall A output affects the product supply available to Hall B;
- packaging throughput affects warehouse load;
- an open warehouse gate affects cold-room conditions;
- rainfall and drainage pump condition affect outdoor flood risk.

These relationships allow one fault to propagate through several pieces of equipment and production areas.

## Equipment and Communication States

Physical equipment condition and LoRaWAN communication condition are displayed separately.

**Equipment Health** can be:

- `Normal`
- `Warning`
- `Alarm`
- `Unknown`

**Communication State** can be:

- `Online`
- `Stale`
- `Offline`

An offline device does not automatically mean that its equipment has stopped. The HMI retains the last received value and indicates that the telemetry is no longer current.

## HMI Screens

### Site Overview

Shows the complete plant, six production areas, online device count, warnings, active alarms, and the main value for each area.

### Zone Overview

Shows the equipment within one production area, its current health, key measurements, and the number of associated devices and alarms.

![Production area equipment](images/zone-overview.png)

### Equipment Detail

Shows equipment status, current measurements, communication freshness, alarm information, operating limits, trends, and process context.

![Detailed equipment status](images/equipment-detail.png)

### Demo

Provides automatic simulation and manually selected guided scenarios. A guided scenario highlights the affected area, follows the fault through connected equipment, and identifies the root cause.

### Settings

Provides Wi-Fi, time, and display brightness controls.

## Demonstration Scenarios

The application includes normal operation and the following fault scenarios:

- low syrup level;
- transfer pump degradation;
- restricted pipeline flow;
- valve position mismatch;
- telemetry loss;
- chiller overload;
- unstable mixing in Production Hall A;
- packaging line jam in Production Hall B;
- warehouse gate left open;
- outdoor drainage pump failure.

## Operating Modes

- **Presentation mode** cycles through three introductory screens.
- **Auto simulation** continuously updates the plant and introduces operating deviations automatically.
- **Manual scenario** starts a selected guided fault sequence.

Pressing and holding the lower-right corner of the touchscreen for 3 seconds switches between the presentation and the HMI. The application does not switch modes automatically after a period of inactivity.
