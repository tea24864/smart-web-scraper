# Web Content Monitor

This project is a robust web content monitoring system that periodically checks specified URLs for changes and notifies users of significant updates via Discord webhooks.

## Features

- Monitors multiple URLs concurrently
- Configurable similarity threshold for change detection
- Discord webhook notifications for significant changes
- CDN detection to help identify potential caching issues
- Content archiving for changed pages
- Robust error handling and retry mechanism
- Detailed logging of operations and metrics

## Requirements

- Python 3.6+
- Required Python packages (see `requirements.txt`):
  - requests==2.26.0
  - beautifulsoup4==4.9.3
  - discord-webhook==0.14.0
  - urllib3==1.26.7

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/web-content-monitor.git
   cd web-content-monitor
   ```

2. Install the required packages:
   ```
   pip install -r requirements.txt
   ```

3. Set up your Discord webhook URL as an environment variable:
   ```
   export DISCORD_WEBHOOK_URL='your_discord_webhook_url_here'
   ```

## Configuration

Edit the `config.json` file to specify the URLs to monitor and other settings:

```json
{
  "urls": {
    "https://example.org": {
      "threshold": 0.9
    },
    "https://example.net": {
      "threshold": 0.98
    }
  },
  "output_dir": "current_content",
  "default_threshold": 0.95,
  "max_retries": 3,
  "max_data_age": 86400,
  "archive_dir": "content_archives"
}
```

- `urls`: A dictionary of URLs to monitor, with optional per-URL thresholds
- `output_dir`: Directory to store current content
- `default_threshold`: Default similarity threshold for change detection
- `max_retries`: Maximum number of retry attempts for failed requests
- `max_data_age`: Maximum age of data before considering it stale (in seconds)
- `archive_dir`: Directory to store archived content

## Usage

Run the main script:

```
python main.py
```

The script will continuously monitor the specified URLs and send Discord notifications when significant changes are detected.

## File Structure

- `main.py`: The main script that handles URL monitoring and change detection
- `discord_utils.py`: Utility functions for sending Discord notifications
- `config.json`: Configuration file for the monitoring system
- `requirements.txt`: List of required Python packages

## Logging

The script logs its operations to `web_content_extractor.log`. This log file includes information about URL processing, change detection, and any errors encountered.

## Contributing

Contributions are limited to invited individuals.

## License

This project is a proprietary asset.
