# System Metrics Easy

A comprehensive server monitoring tool that collects and sends system metrics to a Socket.IO server. This tool provides real-time monitoring of CPU, memory, disk, network, and GPU usage across different platforms.

## Features

- **Real-time Metrics Collection**: CPU, memory, disk, network, and GPU statistics
- **Multi-Platform Support**: Works on Linux, macOS, and Windows
- **GPU Support**: NVIDIA, Apple Silicon, AMD, and Intel GPUs
- **Socket.IO Integration**: Real-time data transmission to your monitoring server
- **Robust Error Handling**: Graceful handling of system errors and missing dependencies
- **Easy Configuration**: Simple environment variable configuration
- **Command Line Interface**: Flexible command-line options

## Installation

### From PyPI (Recommended)

```bash
# Basic installation
pip install system-metrics-easy

# With Supervisor support (for background running)
pip install system-metrics-easy[supervisor]

# With all optional dependencies
pip install system-metrics-easy[all]
```

### From Source

```bash
git clone https://github.com/yourusername/system-metrics-easy.git
cd system-metrics-easy
pip install -e .

# With Supervisor support
pip install -e .[supervisor]
```

## Quick Start (Super Simple!)

### Install and Run

```bash
# Install the package
pip install system-metrics-easy

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

- **supervisor** (for background process management)
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
server-metrics-background

# Check if running
server-metrics-background --status

# Stop it
server-metrics-background --stop

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

## Development

### Setup Development Environment

```bash
git clone https://github.com/yourusername/system-metrics-easy.git
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

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support

- **Issues**: [GitHub Issues](https://github.com/yourusername/system-metrics-easy/issues)
- **Documentation**: [GitHub Wiki](https://github.com/yourusername/system-metrics-easy/wiki)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/system-metrics-easy/discussions)

## Changelog

### Version 1.0.0

- Initial release
- Support for CPU, memory, disk, network, and GPU metrics
- Socket.IO integration
- Multi-platform support
- Command-line interface
- Environment variable configuration
