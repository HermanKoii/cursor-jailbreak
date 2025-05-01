# Cursor Auto Accept: Intelligent AI Code Suggestion Automation Tool

## Project Overview

Cursor Auto Accept is an intelligent automation tool designed to streamline the interaction with Cursor AI's code suggestion workflow. The tool automatically detects and clicks the "Accept" button for AI-generated code suggestions across multiple monitors, reducing manual intervention and improving developer productivity.

### Core Purpose

The primary goal of Cursor Auto Accept is to eliminate the repetitive task of manually accepting AI code suggestions by providing an intelligent, configurable bot that:
- Automatically identifies and clicks "Accept" buttons
- Works seamlessly across multiple monitor setups
- Minimizes user interaction during AI code generation

### Key Features

#### Intelligent Button Detection
- Advanced template matching algorithm for precise button location
- Supports multi-monitor configurations
- Configurable confidence thresholds for button matching

#### Smart Automation
- Rate-limited clicking (maximum 8 clicks per minute)
- Automatic cursor position restoration after interactions
- Dynamic calibration for different screen configurations

#### Robust Performance
- Detailed logging of all bot activities
- Error recovery and monitoring mechanisms
- Configurable detection and interaction parameters

### Benefits

- **Increased Productivity**: Reduces context switching by automating routine acceptance of code suggestions
- **Flexibility**: Supports diverse development environments with multi-monitor setups
- **Reliability**: Implements intelligent detection with high confidence thresholds
- **Transparency**: Provides comprehensive logging for tracking bot activities

## Project Structure

The project is organized into several key directories and files that support its functionality:

### Root Directory
- `main.py`: Primary entry point for the application
- `clickbot.py`: Core bot implementation
- `cursor_auto_accept.py`: Auto-acceptance functionality
- `requirements.txt`: Project dependencies
- Shell scripts for managing the application:
  - `run_bot.sh`: Script to run the bot
  - `start_clickbot.sh`: Start the clickbot
  - `stop_clickbot.sh`: Stop the clickbot
  - `setup.sh`: Initial setup script

### Configuration and Logging
- `logging_config.py`: Logging configuration
- `cursor-plugin.json`: Configuration for the Cursor plugin
- `clickbot.log`: Application log file (in `temp/logs/`)
- `clickbot.pid`: Process ID file

### Analysis and Utility Scripts
- `analyze_calibration.py`: Calibration analysis script
- `analyze_hover_results.py`: Hover results analysis
- `analyze_template.py`: Template matching analysis
- `error_recovery.py`: Error handling and recovery
- `hover_calibrate.py`: Hover calibration functionality
- `image_matcher.py`: Image matching utilities

### Testing
- `test_clickbot.py`: Main bot test suite
- `test_error_recovery.py`: Error recovery tests
- `test_final.py`: Final integration tests
- `test_matcher.py`: Image matcher tests

### Assets and Resources
- `assets/`: Directory containing various image and coordinate files
  - `monitor_0/`, `monitor_2/`: Monitor-specific assets
  - `backup/`: Backup image and coordinate files
- `debug/`: Debug images and matching results
- `images/`: General project images and screenshots

### Additional Documentation
- `README.md`: Main project documentation
- `cursor-instructions/`: Additional documentation files
  - `features.md`
  - `github-process.md`
  - `notes.md`
- `mvp-scope.md`: Minimum Viable Product scope document

### Extensions
- `extension.js`: Likely a browser or IDE extension

## Additional Notes

### Security and Performance Considerations

#### System Reliability
- Implements robust error recovery mechanisms
- Provides comprehensive logging for troubleshooting
- Supports multi-monitor configurations with per-monitor calibration
- Rate-limited to prevent excessive system load (max 8 clicks per minute)

#### Technical Constraints
- Requires Python 3.8+ environment
- Dependencies include OpenCV, PyAutoGUI, MSS, NumPy, and Pillow
- Designed for automated GUI interaction with precise click positioning
- Uses template matching for button recognition with configurable confidence thresholds

#### Calibration Sensitivity
- Button detection relies on visual template matching
- Calibration accuracy depends on:
  - Screen resolution
  - Button visibility
  - Lighting conditions
  - Monitor configuration

#### Performance Recommendations
- Ensure stable screen configurations during operation
- Minimize system resource contention
- Keep background applications to a minimum
- Verify consistent monitor layout during calibration

#### Known Limitations
- Requires manual intervention for initial monitor calibration
- Button recognition depends on consistent UI elements
- Not suitable for dynamically changing interfaces
- Performance may vary across different hardware configurations

#### Monitoring and Diagnostics
- Detailed activity logging available at `temp/logs/clickbot.log`
- Process management through PID tracking
- Configurable logging intervals (default: 5 seconds)

### Future Enhancements
- Improved multi-monitor support
- Enhanced button recognition algorithms
- More flexible configuration options
- Expanded error handling capabilities

## Contributing

We welcome contributions to the Cursor Auto Accept project! To ensure a smooth collaboration, please follow these guidelines:

### Branch Management

- Create a new branch for each major feature or when working on a primary branch
- Branch names should initially use a timestamp (they can be renamed later to be more descriptive)

### Commit Guidelines

- Commit your work to the branch after every group of changes related to a specific improvement or feature
- Push your work to the branch after each commit

### Development Setup

1. Fork the repository
2. Clone your forked repository
3. Create a virtual environment
4. Install dependencies from `requirements.txt`

### Testing

- Ensure all existing tests pass before submitting a pull request
- Add new tests for any new functionality
- Run tests using `pytest` or the included test scripts (e.g., `test_clickbot.py`, `test_matcher.py`)

### Code Quality

- Follow Python best practices and PEP 8 style guidelines
- Add appropriate type hints and docstrings
- Ensure code is well-commented and readable

### Pull Request Process

1. Update the README or documentation with details of changes
2. Ensure your code passes all existing tests
3. Include a clear description of your changes in the pull request

### Reporting Issues

- Use GitHub Issues to report bugs or suggest improvements
- Provide detailed information about the issue, including:
  - Steps to reproduce
  - Expected behavior
  - Actual behavior
  - Environment details (OS, Python version, etc.)

### Areas of Contribution

We're particularly interested in improvements to:
- Monitor detection and calibration
- Error handling
- Performance optimization
- Cross-platform compatibility

By contributing, you agree that your contributions will be licensed under the project's MIT License.

## License

This project is licensed under the MIT License. 

For the full license text, please refer to the details below:

The MIT License is a permissive open-source software license that allows you to:
- Use the software commercially
- Modify the software
- Distribute the software
- Privately use the software

The only condition is that you include the original copyright notice and the license text in any substantial portion of the software.

#### Key Permissions
- Commercial use
- Modification
- Distribution
- Private use

#### Key Limitations
- No Liability
- No Warranty

For complete license details, see the [MIT License](https://opensource.org/licenses/MIT).