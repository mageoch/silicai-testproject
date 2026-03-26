# TMP117 Sensor Board

A SilicAI test project: RP2350A microcontroller reading a TMP117 temperature sensor over I2C.

## Overview

- **MCU:** RP2350A
- **Sensor:** TMP117AIDRVR (I2C, address 0x48)
- **Bus:** I2C at 400 kHz with 4.7 kΩ pull-ups to +3V3
- **Power:** 3.3 V

## Structure

```
circuits/
  tmp117.yaml     TMP117 sensor circuit definition
  rp2350a.yaml    RP2350A microcontroller circuit definition
project.yaml      SilicAI project definition
kicad/            KiCad project files (not tracked)
```

## Setup

Requires [silicai](https://github.com/mageoch/silicai) and [silicai-components](https://github.com/mageoch/silicai-components) cloned as siblings:

```
mageoch/
├── silicai/
├── silicai-components/
└── silicai-testproject/    ← this repo
```

```bash
uv sync
```

## Generate Schematic

```bash
silicai-generate project.yaml --output kicad/
```

## MCP Integration

Copy `.mcp.json` (gitignored) from the template below and adjust paths for your machine:

```json
{
  "mcpServers": {
    "SilicAI": {
      "type": "stdio",
      "command": ".venv/bin/silicai-mcp",
      "args": ["--project-dir", "."]
    }
  }
}
```
