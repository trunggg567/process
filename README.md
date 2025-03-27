# Process Management Utility

A lightweight process management tool for monitoring and controlling system processes.

![Process Management](https://img.shields.io/badge/status-active-brightgreen)
![Python Version](https://img.shields.io/badge/python-3.8%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Tests](https://img.shields.io/badge/tests-passing-brightgreen)
![Coverage](https://img.shields.io/badge/coverage-95%25-green)

## Features

- 📊 List running processes with detailed information (PID, name, status, etc.)
- 🔍 Advanced process filtering (name, PID, user, resource usage)
- ⚡ Safe process control (start/stop/restart with confirmation)
- 📈 Real-time resource monitoring (CPU, memory, disk, network)
- 🌐 Cross-platform support (Linux, macOS, Windows)
- 🛡️ Graceful termination with fallback to force kill
- 📝 Comprehensive logging and audit trail
- 🗂️ Process grouping and tagging
- 🔄 Batch operations for multiple processes

## Installation

### Prerequisites
- Python 3.8+
- pip 20.0+
- Recommended: virtualenv

### Install from PyPI
```bash
pip install process-utility --upgrade
```

### Install from source
```bash
git clone https://github.com/trunggg567/process.git
cd process
python -m pip install -e ".[dev]"
```

## Usage

### Basic Commands
```python
from process import ProcessManager

# Initialize with configuration
pm = ProcessManager(
    verbose=True,
    safe_mode=True,
    log_file="process.log"
)

# Get all processes with extended details
processes = pm.list_processes(
    detailed=True,
    sort_by="cpu",
    descending=True
)

# Find processes with advanced filtering
chrome_processes = pm.find_process(
    name="chrome",
    exact_match=False,
    min_cpu=1.0,
    max_memory=1024
)

# Terminate process safely
pm.terminate(
    pid=1234,
    force=False,
    confirm=True,
    timeout=10
)
```

### Command Line Interface
```bash
# List processes with tree view and JSON output
process list --tree --format json

# Monitor multiple processes with alerts
process monitor --pid 1234 5678 --interval 1 --alert-cpu 90 --alert-memory 80

# Batch terminate processes by name
process kill --name "chrome" --force --no-confirm

# Get detailed process statistics
process stats --pid 1234 --output csv --save report.csv
```

## Advanced Features

```python
# Custom monitoring with thresholds
def resource_handler(process):
    if process.cpu > 90:
        pm.notify(f"Critical CPU: {process.name} ({process.pid})")
    elif process.memory > 80:
        pm.log_warning(f"High memory: {process.name}")

pm.monitor(
    pids=[1234, 5678],
    callback=resource_handler,
    interval=5,
    duration=300
)

# Process visualization and analysis
pm.analyze_process_tree(
    root_pid=1,
    show_resources=True,
    max_depth=3
)

# Export process data
pm.export_processes(
    output_format="json",
    filename="processes.json",
    filter={"status": "running"}
)

## 更新

feature: Add feature improvements for process handling - 2025-03-27

```markdown
# Pull Request Description

## Overview
This PR introduces functional improvements to enhance the overall performance and user experience of the repository. The changes aim to address specific pain points and streamline existing processes.

## Changes
- Implemented functional improvements to optimize performance
- Updated relevant components to align with the latest requirements
- Refactored code for better readability and maintainability
- Added new features to support enhanced functionality

## Testing
To verify the changes:
1. Clone the repository and checkout the `feature/update-20250327-122400` branch
2. Run the existing test suite to ensure all tests pass
3. Manually test the new features and improvements to confirm they work as expected
4. Check for any potential regressions in existing functionality

## Related Issues
- N/A (No related issues at this time)
```