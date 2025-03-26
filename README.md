# Process Management Utility

A lightweight process management tool for monitoring and controlling system processes.

![Process Management](https://img.shields.io/badge/status-active-brightgreen)
![Python Version](https://img.shields.io/badge/python-3.6%2B-blue)
![License](https://img.shields.io/badge/license-MIT-green)

## Features

- 📊 List running processes with detailed information
- 🔍 Filter processes by name, PID, or other attributes
- ⚡ Start/stop processes programmatically
- 📈 Monitor process resource usage (CPU, memory, disk I/O)
- 🌐 Cross-platform support (Linux, macOS, Windows)
- 🛡️ Safe process termination with confirmation
- 📝 Process logging and history tracking

## Installation

### Prerequisites
- Python 3.6+
- pip package manager

### Install from PyPI
```bash
pip install process-utility --upgrade
```

### Install from source
```bash
git clone https://github.com/trunggg567/process.git
cd process
pip install -e .
```

## Usage

### Basic commands
```python
from process import ProcessManager

# Initialize with detailed output
pm = ProcessManager(verbose=True)

# List all processes with extended info
processes = pm.list_processes(detailed=True)

# Find process by name with partial matching
chrome_processes = pm.find_process(name="chrome", exact_match=False)

# Safely terminate process with confirmation
pm.terminate(pid=1234, force=False, confirm=True)
```

### Command Line Interface
```bash
# List all processes with tree view
process list --tree

# Monitor process resources with refresh interval
process monitor --pid 5678 --interval 2

# Terminate multiple processes
process kill 1234 5678 9012 --force

# Get process statistics
process stats --pid 1234 --output json
```

## Advanced Features

```python
# Monitor process with callback
def resource_alert(process):
    if process.cpu > 90:
        print(f"High CPU usage: {process.cpu}%")

pm.monitor(pid=1234, callback=resource_alert, interval=5)

# Process tree visualization
pm.print_process_tree(root_pid=1)
```

## Contributing

We welcome contributions! Please see our [Contribution Guidelines](CONTRIBUTING.md) for details.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## Support

For help or questions, please [open an issue](https://github.com/trunggg567/process/issues).

## License

MIT License - see [LICENSE](LICENSE) for details.

---

> ⚠️ **Warning**: Terminating system processes may cause instability. Use with caution.