# TMP117 Sensor Board

A SilicAI example project: RP2350A microcontroller reading a TMP117 temperature sensor over I2C.

See the [full walkthrough](https://mageoch.github.io/silicai/example-project/) in the SilicAI documentation.

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
kicad/            Generated KiCad files (not tracked)
```

## Setup

```bash
git clone git@github.com:mageoch/silicai-testproject.git
cd silicai-testproject
pip install silicai
```

Or with `uv`:

```bash
uv sync
```

## Generate Schematic

```bash
silicai-generate project.yaml --output kicad/
```

## MCP Integration

Add a `.mcp.json` at the project root (gitignored):

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
