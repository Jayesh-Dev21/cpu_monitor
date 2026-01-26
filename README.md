```text
======================================
CPU MONITOR - Real-time CPU Usage Visualization Tool
======================================
```
![](./sample/bash_cpu_M.png)

```text
======================================
DESCRIPTION
======================================

A lightweight CPU monitoring tool written in pure Bash.
Displays real-time per-core CPU usage with visual progress bars.
Linux-specific implementation using the /proc filesystem.
Similar to HTOP but focused solely on CPU visualization.

======================================
FEATURES
======================================

- Real-time CPU usage monitoring for all cores
- Color-coded visual progress bars
- Per-core usage percentage display
- Dynamic terminal resize support
- Offline CPU detection
- Clean modular code structure
- Zero external dependencies (pure Bash)

======================================
REQUIREMENTS
======================================

- Linux operating system
- Bash shell
- Terminal with ANSI color support
- Access to /proc/stat filesystem

======================================
PROJECT STRUCTURE
======================================

cpu_monitor/
  |
  |-- cpu_M                         Main executable script
  |-- tri                           Original reference implementation
  |-- README.md                     This file
  |
  |-- dependencies/                 Function library directory
  |     |-- fun_copyData            Copy data between hashmaps
  |     |-- fun_readProc            Read CPU stats from /proc/stat
  |     |-- fun_printBar            Print visual CPU usage bars
  |     |-- fun_visualize           Orchestrate display output
  |     |-- fun_getAllCpus          Discover system CPU cores
  |     |-- fun_updateWindowSize    Handle dynamic window resizing
  |
  |-- sample/                       Sample screenshots and demos

======================================
INSTALLATION
======================================

1. Clone the repository
   git clone https://github.com/Jayesh-Dev21/cpu_monitor.git

2. Navigate to the directory
   cd cpu_monitor

3. Make the script executable
   chmod +x cpu_M

4. Run the monitor
   ./cpu_M

======================================
USAGE
======================================

To start the CPU monitor:
   ./cpu_M

To disable colors:
   NO_COLOR=1 ./cpu_M

To exit:
   Press Ctrl+C

======================================
HOW IT WORKS
======================================

The monitor reads CPU statistics from /proc/stat which contains:
- user: time spent in user mode
- nice: time spent in user mode with low priority
- system: time spent in system mode
- idle: time spent in idle task
- iowait: time spent waiting for I/O
- irq: time spent servicing interrupts
- softirq: time spent servicing softirqs
- steal: time stolen by other operating systems
- guest: time spent running a virtual CPU

Busy time = user + nice + system + irq + softirq + steal + guest + guest_nice
Idle time = idle + iowait

CPU usage % = (busy_time_delta / total_time_delta) * 100

The monitor updates every second with real-time calculations.


======================================
TECHNICAL DETAILS
======================================

Color Codes:
- Red (31m)      - Progress bar fill
- Magenta (35m)  - CPU core labels
- Cyan (36m)     - Percentage values
- Dim (2m)       - Timestamps and offline status

Terminal Control:
- Alternate buffer mode for clean display
- Hidden cursor during monitoring
- Dynamic bar length based on terminal width
- SIGWINCH handler for window resize events

======================================
CREDITS
======================================

Inspired by: "You Suck at Programming" philosophy
License: MIT

======================================
NOTES
======================================

This is a learning project demonstrating:
- Bash scripting techniques
- Linux /proc filesystem usage
- Terminal control sequences
- Real-time data visualization
- Modular code organization

======================================
```