# Mini TikTok Automation System - Environment Setup

## Project Structure

```
MiniTiktokAutomationSystem/
├── src/                          # Source code directory
│   ├── __init__.py               # Package init
│   ├── main.py                   # Entry point
│   ├── browser.py                # Browser management module
│   ├── login.py                  # Login module
│   ├── uploader.py               # Video upload module
│   └── utils.py                  # Utility functions
├── config/
│   └── config.yaml               # Configuration file
├── data/
│   ├── videos/                   # Videos to upload
│   │   └── .gitkeep
│   └── cookies/                  # Cookie storage
│       └── .gitkeep
├── logs/                         # Log directory
│   └── .gitkeep
├── docker/
│   ├── Dockerfile                # Docker image config
│   └── docker-compose.yml        # Docker Compose config
├── docs/
│   ├── 01-requirements-and-planning.md
│   └── 02-environment-setup.md
├── requirements.txt              # Python dependencies
├── .gitignore                    # Git ignore rules
└── README.md                     # Project documentation
```

---

## Dependencies

### requirements.txt

| Package | Version | Purpose |
|---------|---------|---------|
| selenium | >=4.15.0 | Core web automation framework |
| undetected-chromedriver | >=3.5.0 | Anti-detection Chrome driver |
| webdriver-manager | >=4.0.0 | Automatic WebDriver management |
| python-dotenv | >=1.0.0 | Environment variable management |
| pyyaml | >=6.0 | YAML config parsing |
| loguru | >=0.7.0 | Logging |
| requests | >=2.31.0 | HTTP request utility |

---

## Configuration

### config/config.yaml

```yaml
# Browser settings
browser:
  headless: false           # Headless mode
  window_size:
    width: 1920
    height: 1080
  implicit_wait: 10         # Implicit wait time (seconds)
  page_load_timeout: 60     # Page load timeout (seconds)

# TikTok URLs
tiktok:
  base_url: "https://www.tiktok.com"
  upload_url: "https://www.tiktok.com/tiktokstudio/upload"
  login_url: "https://www.tiktok.com/login"

# Upload settings
upload:
  max_title_length: 150     # Max title length
  max_retries: 3            # Max retry count
  upload_timeout: 300       # Upload timeout (seconds)

# Timing delays (simulate human behavior)
timing:
  min_delay: 1              # Min delay (seconds)
  max_delay: 3              # Max delay (seconds)
  typing_delay: 0.05        # Typing delay (seconds)
```

---

## Module Descriptions

### 1. main.py - Entry Point
- Parse command line arguments
- Load configuration file
- Coordinate modules to execute upload task

### 2. browser.py - Browser Management
- Initialize Chrome browser (using undetected-chromedriver)
- Configure anti-detection options
- Manage browser lifecycle

### 3. login.py - Login Management
- Detect login status
- Load/save cookies
- Support manual login

### 4. uploader.py - Video Upload
- Navigate to upload page
- Upload video file
- Fill in title and tags
- Click publish button

### 5. utils.py - Utility Functions
- Config file loading
- Logging setup
- Video file validation

---

## Installation Steps

### Local Development

```bash
# 1. Create virtual environment
python -m venv venv

# 2. Activate virtual environment
# macOS/Linux:
source venv/bin/activate
# Windows:
venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt
```

### Docker Environment

```bash
# Build image
cd docker
docker-compose build

# Run container
docker-compose up
```
