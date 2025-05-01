# Cursor Auto-Accept: AI Suggestion Automation Toolkit

## Project Overview

A sophisticated automation tool designed to streamline the interaction with Cursor, an AI coding assistant. This project addresses the repetitive task of manually accepting AI-generated code suggestions by providing an intelligent, configurable bot that automatically detects and clicks accept buttons across multiple monitors.

### Core Purpose

The primary goal is to reduce developer friction by automating the acceptance of AI code suggestions, allowing developers to maintain their workflow without constant manual intervention. By leveraging advanced image recognition and multi-monitor support, the tool provides a seamless background service for accepting Cursor's AI recommendations.

### Key Features

- **Multi-Monitor Compatibility**: Supports automated clicks across different monitors with per-monitor calibration
- **Intelligent Image Matching**: Uses template matching with configurable confidence thresholds to ensure accurate button detection
- **Adaptive Click Management**: 
  - Rate limiting to prevent excessive clicking (max 8 clicks per minute)
  - Automatic cursor position restoration after interactions
- **Robust Error Handling**: 
  - Comprehensive error recovery mechanisms
  - Detailed logging for troubleshooting
- **Flexible Configuration**: Easily adjustable settings for interval, confidence levels, and monitoring

### Benefits

- **Increased Productivity**: Reduces manual interaction with AI suggestion accept buttons
- **Cross-Platform Compatibility**: Works with different monitor setups and screen configurations
- **Minimal Intrusion**: Runs as a background service with low system overhead
- **Customizable**: Supports debug modes and fine-tuning of detection parameters

## Getting Started, Installation, and Setup

### Prerequisites

- Python 3.8 or higher
- Git
- A Unix-like operating system (Linux, macOS)

### System Requirements

- Cursor AI application installed
- Multiple monitor setup (optional, but recommended)

### Installation Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/cursor-auto-accept.git
   cd cursor-auto-accept
   ```

2. Run the setup script to initialize the project:
   ```bash
   ./setup.sh
   ```
   This script will:
   - Create necessary directories
   - Set up file permissions
   - Create a Python virtual environment
   - Install required dependencies

### Dependencies

The project requires the following Python packages (automatically installed):
- OpenCV (`opencv-python`) >= 4.8.0
- NumPy >= 1.24.0
- PyAutoGUI >= 0.9.54
- Pillow >= 10.0.0
- MSS (Multi-Screen Shot) >= 9.0.1

### Calibration Setup

Before using the bot, you must calibrate it for each monitor:

1. Activate the virtual environment:
   ```bash
   source venv/bin/activate
   ```

2. Run calibration for all monitors:
   ```bash
   python cursor_auto_accept.py --capture
   ```

   Or for a specific monitor (0-based index):
   ```bash
   python cursor_auto_accept.py --capture --monitor 0  # First monitor
   python cursor_auto_accept.py --capture --monitor 1  # Second monitor
   ```

3. Follow the on-screen calibration instructions:
   - Move Cursor to the target monitor
   - Trigger an AI prompt
   - Move mouse over the accept button
   - Keep mouse still for 5 seconds
   - Wait for confirmation
   - Press Enter to continue to next monitor

### Running the Bot

Start the bot:
```bash
./start_clickbot.sh
```

Stop the bot:
```bash
./stop_clickbot.sh
```

### Monitoring

Monitor bot activity by viewing the log file:
```bash
tail -f temp/logs/clickbot.log
```

## Additional Notes

### Automated AI Suggestion Acceptance

This project is designed to automate the process of accepting AI suggestions in the Cursor IDE, addressing the repetitive task of manually clicking "Accept" buttons during coding sessions.

### Performance Considerations

- The bot employs a conservative rate limit of 8 clicks per minute to prevent potential system overload
- Uses a 0.8 (80%) confidence threshold for image matching to ensure accurate button detection
- Performs periodic screen scans at 0.2-second intervals for real-time responsiveness

### Cross-Platform Flexibility

While primarily developed for monitoring AI suggestion acceptance, the core image matching and automation techniques can be adapted to various screen interaction scenarios across different applications and development environments.

### Monitoring and Diagnostics

- Comprehensive logging mechanism captures all bot activities
- Supports multi-monitor configurations with per-monitor calibration
- Detailed error tracking and recovery mechanisms implemented

### Security and Privacy

- No external data transmission occurs during operation
- All processing happens locally on the user's machine
- Respects user workflow by minimizing intrusive interactions

### Future Potential

The modular design of the image matching and automation framework suggests potential extensions to:
- Accessibility tools
- Automated testing scripts
- Screen interaction utilities
- Cross-application workflow automation

### Known Limitations

- Requires visual consistency in UI elements for reliable matching
- Performance may vary based on screen resolution and UI scaling
- Dependent on OpenCV and PyAutoGUI for screen interaction

## Contributing

We welcome contributions to this project! To ensure a smooth and effective collaboration, please follow these guidelines:

### Contribution Process

1. **Branch Management**
   - Create a new branch for each major feature or significant change
   - Use a timestamp-based naming convention for new branches
   - Rename branches to a more descriptive name as the work progresses

2. **Commit Guidelines**
   - Commit your work after completing a specific improvement or feature
   - Push your changes to the branch after each commit

### Development Setup

#### Prerequisites
- Python 3.x
- Required dependencies (install via `requirements.txt`):
  - opencv-python (>=4.8.0)
  - numpy (>=1.24.0)
  - pyautogui (>=0.9.54)
  - pillow (>=10.0.0)
  - mss (>=9.0.1)

### Testing

#### Running Tests
- Execute unit tests using `unittest`
- Test files are located in the project root (e.g., `test_clickbot.py`)
- Ensure all tests pass before submitting a pull request

### Code Quality

#### Recommended Practices
- Follow Python best practices and PEP 8 style guidelines
- Write clear, concise, and well-documented code
- Include unit tests for new functionality
- Ensure debug logging is implemented for complex features

### Pull Request Process
1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to your branch
5. Submit a pull request with a clear description of your changes

#### Note
By contributing, you agree that your contributions will be licensed under the project's existing license.

## License

This project is licensed under the MIT License. For the full license text, see the [LICENSE](LICENSE) file in the repository.

### Key Permissions
- Commercial use
- Modification
- Distribution
- Private use

### Conditions
- License and copyright notice must be included
- The software is provided "as is" without warranties

### Limitations
- No liability
- No warranty