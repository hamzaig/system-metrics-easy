# System Metrics Easy

A comprehensive server monitoring tool that collects and sends system metrics to a Socket.IO server. This tool provides real-time monitoring of CPU, memory, disk, network, and GPU usage across different platforms.

## Features

- **Real-time Metrics Collection**: CPU, memory, disk, network, and GPU statistics
- **Multi-Platform Support**: Works on Linux, macOS, and Windows
- **GPU Support**: NVIDIA, Apple Silicon, AMD, and Intel GPUs
- **Socket.IO Integration**: Real-time data transmission to your monitoring server
- **Robust Error Handling**: Graceful handling of system errors and missing dependencies
- **Easy Configuration**: Interactive configuration setup
- **Command Line Interface**: Simple command-line options
- **Background Process Management**: Built-in background running with PID management

## Installation

### From Source (Current - Not Published to PyPI Yet)

```bash
# Clone the repository
git clone https://github.com/hamzaig/system-metrics-easy.git
cd system-metrics-easy

# Install the package
pip install -e .

# With Supervisor support
pip install -e .[supervisor]
```

**Note**: Make sure you're in the `package` directory when running `pip install -e .` if you're working with the source code directly.

### From PyPI (Coming Soon!)

```bash
# These commands will work once the package is published to PyPI
# Basic installation
pip install system-metrics-easy

# With Supervisor support (for advanced background running)
pip install system-metrics-easy[supervisor]

# With all optional dependencies
pip install system-metrics-easy[all]
```

**Note**: The package is not yet published to PyPI, so you need to install from source for now.

## Current Status

✅ **What Works Now:**

- Install from source: `git clone` + `pip install -e .`
- Run the tool: `system-metrics-easy`
- All monitoring features work perfectly
- Background process management works

❌ **What Doesn't Work Yet:**

- `pip install system-metrics-easy` (not published to PyPI)
- PyPI installation methods

## Quick Start (Super Simple!)

### Install and Run

```bash
# First, install from source (since it's not on PyPI yet)
git clone https://github.com/hamzaig/system-metrics-easy.git
cd system-metrics-easy
pip install -e .

# Run it - it will ask you for configuration and start in background!
system-metrics-easy
```

That's it! The script will:

1. **Ask you for configuration** (interval, server URL, server name)
2. **Start monitoring** in background automatically
3. **Save logs** to `system-metrics-easy.log`
4. **Handle all process management** for you

### Simple Commands

```bash
# Start monitoring (asks for config)
system-metrics-easy

# Check if it's running
system-metrics-easy --status

# Stop it
system-metrics-easy --stop
```

**That's it! Just simple commands: `system-metrics-easy`, `--status`, `--stop`**

## Metrics Collected

### System Information

- Hostname, OS, architecture
- Python version, uptime, boot time

### CPU Metrics

- Total CPU usage percentage
- Per-core CPU usage
- Load average (1min, 5min, 15min)
- Core count

### Memory Metrics

- Total, used, free, and available memory (GB)
- Memory usage percentage
- Swap memory statistics

### Disk Metrics

- Disk usage for all mounted filesystems
- Total, used, and free space (GB)
- Usage percentage per partition

### Network Metrics

- Network throughput per second
- Bytes sent/received per second
- Total bytes sent/received (GB)
- Per-interface statistics

### GPU Metrics

- **NVIDIA**: Utilization, memory usage, temperature
- **Apple Silicon**: Basic GPU information
- **AMD**: ROCm-based monitoring
- **Intel**: Basic GPU detection

## Socket.IO Integration

The tool connects to your Socket.IO server and emits metrics data in the following format:

```json
{
  "timestamp": 1640995200.0,
  "formatted_time": "2022-01-01 12:00:00",
  "server_id": "my-server-001",
  "system_info": { ... },
  "cpu": { ... },
  "memory": { ... },
  "disk": [ ... ],
  "network": [ ... ],
  "gpu": [ ... ],
  "cuda_processes": { ... }
}
```

## Requirements

- Python 3.8 or higher
- psutil (for system metrics)
- python-socketio (for real-time communication)
- python-dotenv (for configuration)

### Optional Dependencies

- **supervisor** (for advanced background process management)
  - Install with: `pip install system-metrics-easy[supervisor]`

## Platform Support

- **Linux**: Full support for all metrics
- **macOS**: Full support including Apple Silicon GPU detection
- **Windows**: Full support with Windows-specific optimizations

## GPU Support

- **NVIDIA**: Requires nvidia-smi (usually included with NVIDIA drivers)
- **Apple Silicon**: Native macOS support
- **AMD**: Requires ROCm tools (rocm-smi)
- **Intel**: Basic detection support

## Error Handling

The tool includes robust error handling:

- Graceful degradation when tools are unavailable
- Retry logic for transient failures
- Comprehensive logging and error messages
- Safe fallbacks for missing data

## Background Running (Super Simple!)

### Easy Background Running

```bash
# Start in background (one command!)
system-metrics-easy

# Check if running
system-metrics-easy --status

# Stop it
system-metrics-easy --stop

# View logs
tail -f system-metrics-easy.log
```

### Advanced Options (Optional)

If you need more control, you can also use:

```bash
# Using nohup
nohup system-metrics-easy > metrics.log 2>&1 &

# Using screen
screen -S metrics
system-metrics-easy
# Press Ctrl+A, D to detach

# Using tmux
tmux new-session -s metrics
system-metrics-easy
# Press Ctrl+B, D to detach
```

## Configuration

### Environment Variables

You can set these environment variables for automatic configuration:

```bash
export TIME_INTERVAL=10
export SOCKET_SERVER_URL=http://localhost:8000
export SERVER_ID=my-server-001
```

### Interactive Configuration

If no environment variables are set, the tool will ask you for:

1. **Time Interval**: How often to collect metrics (seconds)
2. **Server URL**: Your Socket.IO server URL
3. **Server ID**: Unique identifier for this server

## Development

### Setup Development Environment

```bash
git clone https://github.com/hamzaig/system-metrics-easy.git
cd system-metrics-easy
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -e .[supervisor]  # Include supervisor for testing
```

### Running Tests

```bash
python -m pytest tests/
```

### Building Package

```bash
python -m build
```

### Publishing to PyPI (When Ready)

```bash
# Install build tools
pip install build twine

# Build the package
python -m build

# Upload to PyPI (requires PyPI account)
python -m twine upload dist/*
```

After publishing, users will be able to install with:

```bash
pip install system-metrics-easy
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

- **Issues**: [GitHub Issues](https://github.com/hamzaig/system-metrics-easy/issues)
- **Documentation**: [GitHub Wiki](https://github.com/hamzaig/system-metrics-easy/wiki)
- **Discussions**: [GitHub Discussions](https://github.com/hamzaig/system-metrics-easy/discussions)

## Changelog

### Version 1.0.0

- Initial release
- Support for CPU, memory, disk, network, and GPU metrics
- Socket.IO integration
- Multi-platform support
- Command-line interface
- Interactive configuration
- Built-in background process management

## About

System Metrics Easy is a simple yet powerful tool for monitoring server performance. It's designed to be easy to use while providing comprehensive system metrics collection and real-time data transmission to your monitoring infrastructure.

### Resources

- **Repository**: [https://github.com/hamzaig/system-metrics-easy](https://github.com/hamzaig/system-metrics-easy)
- **Documentation**: [GitHub Wiki](https://github.com/hamzaig/system-metrics-easy/wiki)
- **Issues**: [GitHub Issues](https://github.com/hamzaig/system-metrics-easy/issues)

### License

MIT License - see [LICENSE](LICENSE) file for details.

---

**Made with ❤️ by [Moonsys](https://github.com/hamzaig)**
