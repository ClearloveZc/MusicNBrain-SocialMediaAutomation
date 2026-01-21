# Mini TikTok Automation System - Testing & Validation

## Environment Verification

### ✅ Dependencies Installed Successfully

Installed core packages:
- selenium 4.40.0
- undetected-chromedriver 3.5.5
- webdriver-manager 4.0.2
- python-dotenv 1.2.1
- pyyaml 6.0.3
- loguru 0.7.3
- requests 2.32.5
- setuptools 80.10.1 (Python 3.12+ compatibility)

### ✅ Program Startup Test

```bash
$ python src/main.py --help

usage: main.py [-h] -v VIDEO [-t TITLE] [--tags TAGS [TAGS ...]] [--headless]
               [-c CONFIG]

Mini TikTok Automation System

options:
  -h, --help            show this help message and exit
  -v, --video VIDEO     Path to the video file to upload
  -t, --title TITLE     Video title/caption
  --tags TAGS [TAGS ...]
                        Hashtags for the video (without #)
  --headless            Run browser in headless mode
  -c, --config CONFIG   Path to config file
```

---

## Command Line Arguments

| Argument | Required | Description |
|----------|----------|-------------|
| `-v, --video` | ✅ | Path to video file to upload |
| `-t, --title` | ❌ | Video title/caption |
| `--tags` | ❌ | Tag list (without #, space separated) |
| `--headless` | ❌ | Run browser in headless mode |
| `-c, --config` | ❌ | Custom config file path |

---

## Usage Examples

### Basic Upload

```bash
# Activate virtual environment
source venv/bin/activate

# Upload video (first run opens browser for manual login)
python src/main.py -v data/videos/test.mp4
```

### With Title and Tags

```bash
python src/main.py \
  -v data/videos/my_video.mp4 \
  -t "Check out this cool video!" \
  --tags fyp viral funny
```

### Headless Mode (requires prior login)

```bash
python src/main.py \
  -v data/videos/my_video.mp4 \
  -t "Auto published" \
  --headless
```

---

## Issues Encountered & Solutions

### Issue: ModuleNotFoundError: No module named 'distutils'

**Cause**: Python 3.12+ removed the distutils module

**Solution**:
```bash
pip install setuptools
```

This dependency has been added to requirements.txt.
