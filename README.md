# printer-material-manager

A Qt Quick / QML desktop application and API client for managing, inspecting, and synchronizing 3D printer filament and material profiles.

## Project Overview

`printer-material-manager` interfaces with Formide-compatible 3D printer daemons via REST API and WebSockets. It enables operators to query available printing materials, inspect extruder and heated bed thermal parameters, review detailed filament specifications, and synchronize material profiles across print jobs.

## Features

- **Material Profile Inspection**: Browse loaded filament presets (PLA, ABS, PETG, etc.) and view target extruder and bed temperatures.
- **REST & WebSocket Integration**: Communicates dynamically with local and networked 3D printer backends for real-time printer telemetry and notifications.
- **Profile Deletion & Management**: Manage material database entries with interactive confirmation dialogues.
- **Embedded UI Form Factor**: Optimized for touchscreens and embedded displays (480x272 resolution).

## Prerequisites

- **Qt SDK**: Qt 5.5+ or Qt 6.x with modules:
  - `QtQuick`
  - `QtQuick.Controls`
  - `Qt.WebSockets`
- **C++ Compiler**: GCC (MinGW), Clang, or MSVC (C++11 compatible).
- **Backend Service**: Formide printer backend daemon or mock REST service running on `localhost:1337`.

## Installation / Build

### Using QMake

1. Clone the repository:
   ```bash
   git clone https://github.com/AntonioHellin/getMaterialsGcode.git printer-material-manager
   cd printer-material-manager
   ```

2. Generate Makefile and compile:
   ```bash
   qmake testMaterials.pro
   make # or 'nmake' / 'mingw32-make' on Windows
   ```

### Using Qt Creator

1. Open Qt Creator.
2. Select **File > Open File or Project...** and open `testMaterials.pro`.
3. Select your desired Qt Kit and build/run (`Ctrl+R`).

## Configuration & Environment Variables

The application connects by default to a local printer daemon:

| Configuration | Default | Description |
| :--- | :--- | :--- |
| `baseUrl` | `http://127.0.0.1:1337` | REST API endpoint for Formide database |
| `sock.url` | `ws://127.0.0.1:8080` | WebSocket endpoint for real-time print events |

## Usage

1. Launch the application.
2. The initial screen connects to the printer service and displays **Get Materials**.
3. Click **Get Materials** to fetch and list all registered filament profiles.
4. Click on any individual material item to view its details (Extruder Temperature, Bed Temperature, Material Type).
5. Use **Back** to return to the catalog or **Delete** to remove a profile.

## License

This project is licensed under the [MIT License](LICENSE).
