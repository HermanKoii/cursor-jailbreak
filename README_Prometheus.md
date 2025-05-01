# Cursor Auto-Accept Bot: Automated AI Interaction Assistant

## Getting Started, Installation, and Setup

### Prerequisites

- Python 3.8 or higher
- Git
- A Unix-like operating system (Linux/macOS recommended)

### System Requirements

- OpenCV
- PyAutoGUI
- MSS (Multi-Screen Shot)
- NumPy
- Pillow

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

### Virtual Environment

The setup script creates a Python virtual environment. Activate it before running the project:
```bash
source venv/bin/activate
```

### Calibration Setup

Before first use, you must calibrate the bot for each monitor:

1. Stop any existing bot instance:
```bash
./stop_clickbot.sh
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

#### Calibration Process
- Move Cursor to the target monitor
- Trigger an AI prompt to show the accept button
- Move your mouse over the accept button
- Keep the mouse still for 5 seconds
- Wait for confirmation message
- Press Enter to continue to next monitor (if calibrating multiple)

### Starting the Bot

After calibration, start the bot with:
```bash
./start_clickbot.sh
```

### Stopping the Bot

To stop the bot:
```bash
./stop_clickbot.sh
```

## Usage

The ClickBot is an automated screen clicking tool that uses image recognition to locate and click on specific targets.

### Basic Usage

To run the ClickBot, use the following command:

```bash
python3 clickbot.py
```

This will start the bot, which continuously scans the screen for a predefined target image and clicks on it automatically when found.

### Command Line Options

There are no explicit command-line arguments for the basic script. The bot uses a predefined target image located at `images/target.png`.

### Configuration

The bot has several configurable parameters within the script:

- Target image precision can be adjusted by modifying the `threshold` in the `ImageMatcher` initialization (default is 0.85)
- Screen check interval can be modified by changing the `check_interval` parameter in the `run()` method (default is 1.0 seconds)

### Running with Shell Script

For easier management, you can use the provided shell script:

```bash
./run_bot.sh
```

This script handles different operating systems and attempts to open the bot in a new terminal window.

### Behavior Notes

- The bot uses PyAutoGUI's fail-safe feature: quickly moving the mouse to a corner will stop the script
- It implements intelligent clicking with confidence thresholds to prevent false triggers
- Logging is enabled, with logs written to `temp/logs/clickbot.log`

### Stopping the Bot

- Press `Ctrl+C` to stop the bot gracefully
- The fail-safe feature allows you to abort by quickly moving the mouse to a screen corner

## Project Structure

The project is organized into several key directories and files that support its functionality:

### Root Directory
The root directory contains primary Python scripts, shell scripts, and configuration files:
- `main.py`: Primary entry point for the application
- `clickbot.py`: Core bot implementation script
- `cursor_auto_accept.py`: Automated acceptance functionality
- `run_bot.sh`: Script to run the bot
- `start_clickbot.sh`: Startup script for the bot
- `stop_clickbot.sh`: Script to stop the bot
- `requirements.txt`: Python dependencies
- `setup.sh`: Setup script for the project
- `logging_config.py`: Logging configuration
- `cursor-plugin.json`: Plugin configuration file

### Auxiliary Python Scripts
Several specialized Python scripts for different functionalities:
- `image_matcher.py`: Image matching and template recognition
- `error_recovery.py`: Error handling and recovery mechanisms
- `hover_calibrate.py`: Hover calibration utilities
- `analyze_calibration.py`: Calibration analysis script
- `analyze_hover_results.py`: Analysis of hover-related results

### Test Directory
Test scripts to validate bot functionality:
- `test_clickbot.py`: Main bot testing
- `test_error_recovery.py`: Error recovery testing
- `test_matcher.py`: Image matching tests
- `test_final.py`: Final integration tests

### Assets Directory
Contains visual assets and configuration files:
- `assets/`: Multiple subdirectories with monitor-specific assets
  - Screen captures
  - Button images
  - Click coordinate files
- `debug/`: Debug-related images and diagnostic outputs
- `images/`: General project images and visual resources

### Temporary and Log Directories
- `temp/`: Temporary file storage
  - `temp/logs/`: Log file storage
- `temp/clickbot.pid`: Process ID file
- `cursor_bot.log`: Bot log file

### Cursor Instructions
- `cursor-instructions/`: Documentation and process notes
  - `features.md`
  - `github-process.md`
  - `notes.md`
  - `readme.md`

### Extension and Plugin
- `extension.js`: Possible browser or IDE extension implementation

This structure supports a modular, extensible bot application with clear separation of concerns between core functionality, testing, assets, and configuration.

## Additional Notes

### Performance and Limitations

The auto-accept bot is designed with several performance considerations:
- Rate limited to 8 clicks per minute to prevent system overload
- Configurable confidence threshold (default 80% match)
- Low system resource consumption with 0.2-second search intervals
- Supports multi-monitor setups with individual calibration

### Compatibility

- Primarily tested with Cursor AI on modern desktop environments
- Requires Python 3.8+ with OpenCV and PyAutoGUI
- Compatible with most Linux and macOS systems
- Limited Windows support (testing recommended)

### Known Limitations

- Requires manual calibration for each monitor
- Button detection relies on visual template matching
- Potential issues with:
  - Non-standard UI themes
  - Rapidly changing UI layouts
  - Extremely low-contrast or dynamic interfaces

### Security Considerations

- Local operation with no external network dependencies
- No personal data collection
- Minimal system interaction (mouse click simulation)
- Logs stored locally with 5-second update intervals

### Troubleshooting

If the bot encounters persistent issues:
- Verify monitor calibration
- Check system accessibility settings
- Ensure Cursor AI interface remains consistent
- Review log files for detailed error information

### Future Development

Potential areas for future enhancement:
- Enhanced multi-monitor support
- More robust button detection algorithms
- Adaptive UI recognition
- Configurable click strategies
- Extended logging and diagnostics

## Contributing

We welcome contributions to this project! Here are some guidelines to help you get started:

### Branch Strategy
- Create a new branch for each major feature or significant work
- Use a timestamp as the initial branch name, which can be renamed later for clarity
- Commit your work frequently, focusing on logical groups of changes

### Contribution Process
1. Fork the repository
2. Create a new branch for your feature or bugfix
3. Make your changes, committing often with clear, descriptive commit messages
4. Ensure all existing tests pass
5. Add tests for new functionality if applicable
6. Submit a pull request with a clear description of your changes

### Development Requirements
Ensure you have the following dependencies installed:
- Python 3.x
- OpenCV (>= 4.8.0)
- NumPy (>= 1.24.0)
- PyAutoGUI (>= 0.9.54)
- Pillow (>= 10.0.0)
- MSS (>= 9.0.1)

### Testing
- Run existing tests using the test files in the project
- Ensure new functionality is accompanied by appropriate test cases
- Verify that all tests pass before submitting a pull request

### Code Style
- Follow standard Python naming conventions
- Write clear, readable, and well-documented code
- Include type hints and docstrings where appropriate

### Reporting Issues
If you find a bug or have a suggestion:
- Check existing issues to avoid duplicates
- Provide a clear and detailed description
- Include steps to reproduce the issue if applicable
- If possible, include a minimal code example or screenshot

We appreciate your help in making this project better!

## License

This project is licensed under the MIT License. For the full license text, please see the [MIT License](https://opensource.org/licenses/MIT).

#### Key Terms
- You are free to use, modify, and distribute this software
- Attribution is appreciated but not required
- The software is provided "as is" without warranty
- Commercial use is permitted
- Modifications and derivative works are allowed

#### Contribution and Use
By contributing to or using this project, you agree to the terms of the MIT License.