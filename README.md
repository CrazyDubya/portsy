# Portsy - Port Scanner & Route Analyzer

A highly optimized, super simple command-line and GUI tool that locates what's running on what ports, discovers exposed routes, and identifies potential duplicate dev servers.

## Features

- 🚀 **Lightning Fast** - Multi-threaded port scanning (100 concurrent connections)
- 🔍 **Smart Detection** - Identifies Python/Node.js frameworks (Flask, FastAPI, Express, React, etc.)
- 🌐 **Deep Route Discovery** - 70+ framework-specific endpoints 
- 🎯 **Scan Presets** - Quick, dev, web, full, and services modes
- 📊 **Duplicate Detection** - Finds potential duplicate services
- 💻 **Dual Interface** - Both CLI and GUI available
- 📄 **Export Support** - JSON export for integration

## Installation

### System-wide Installation
```bash
pip install -e .
```

### From Source
```bash
git clone <repository-url>
cd portsy
pip install -e .
```

## Usage

### Command Line Examples

```bash
# Quick scan (default dev ports 3000-9000)
portsy

# Full system scan (1-65535 ports)
portsy --preset full

# Development server scan with deep route discovery  
portsy --preset dev --comprehensive-routes

# Scan specific port range
portsy -s 8000 -e 8100

# List all available scan presets
portsy --list-presets

# Export results to JSON
portsy --json results.json

# Launch GUI (if tkinter available)
portsy --gui
```

### Scan Presets

- **`quick`** - Common dev ports (3000-9000, 8000-8100)
- **`dev`** - Extended dev ranges (3000-3100, 4000-4100, 5000-5100, 8000-8100, 9000-9100, 8080-8090)
- **`web`** - Web server ports (80, 443, 8080, 8443, plus dev ranges)
- **`full`** - Complete port scan (1-65535) ⚠️ Slow
- **`services`** - Database & service ports (MySQL, PostgreSQL, Redis, MongoDB, etc.)

### Framework Detection

Portsy automatically detects and provides enhanced analysis for:

**Python Frameworks:**
- Flask, Django, FastAPI, Streamlit, Gradio, Jupyter

**Node.js Frameworks:**  
- Express, Next.js, React Dev Server, Vue Dev Server

**Other Services:**
- Ollama, Spring Boot, Nginx, Apache, and more

## Sample Output

```
🔍 Running dev scan: Extended dev server ranges
🌐 Using comprehensive route discovery (all frameworks)
✅ Found 12 open ports

📋 Running Services:
Port     PID      Process         Framework       Routes                              Response
8000     1234     Python          FastAPI         /docs, /redoc, /api/v1/health      2.3ms
8080     5678     node            React Dev       /webpack-dev-server, /             4.7ms
9922     9876     Python          FastAPI         /openapi.json, /redoc, /docs       4.5ms

🐍 Python Services Analysis:
  Port 8000 (FastAPI)
    API Endpoints: /api/v1/health, /api/v1
    PID: 1234, Response: 2.3ms

🟢 Node.js Services Analysis:
  Port 8080 (React/Vue Dev Server)
    Dev Server: /webpack-dev-server
    PID: 5678, Response: 4.7ms
```

## Requirements

- Python 3.8+
- psutil
- requests
- tkinter (optional, for GUI)

## License

MIT License