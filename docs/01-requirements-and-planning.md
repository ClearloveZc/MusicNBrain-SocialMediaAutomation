# MusicNBrain Social Media Automation - Requirements & Planning

## Project Overview

**Project Name**: MusicNBrain Social Media Automation  
**Project Goal**: Build a TikTok video auto-publishing system

### Core Capabilities
- Automatic TikTok account login (via browser user data or cookies)
- Automatic video file upload and publishing
- Support for headless browser mode in Docker containers

---

## Core Features (MVP Scope)

| Feature Module | Description | Priority |
|----------------|-------------|----------|
| **Login Module** | Support auto-login via Chrome user data directory or cookie files | P0 |
| **Video Upload** | Select local video files and upload to TikTok | P0 |
| **Publish Config** | Set video title, description, hashtags | P0 |
| **Publish Execution** | Automatically click publish button to complete posting | P0 |
| **Docker Support** | Run in headless mode inside Docker | P1 |
| **Logging** | Record operation logs for debugging | P1 |
| **Error Handling** | Handle network timeouts, element not found exceptions | P1 |

---

## Technology Stack

| Category | Technology | Reason |
|----------|------------|--------|
| **Language** | Python 3.10+ | Rich ecosystem, good Selenium support |
| **Automation** | Selenium + undetected-chromedriver | Bypass basic anti-bot detection |
| **Browser** | Chrome/Chromium | Most stable, good Docker support |
| **Containerization** | Docker + docker-compose | Easy deployment and environment consistency |
| **Configuration** | Python dotenv / YAML | Flexible configuration management |

---

## Project Structure

```
MusicNBrain-SocialMediaAutomation/
├── src/
│   ├── __init__.py
│   ├── main.py              # Entry point
│   ├── browser.py           # Browser initialization and management
│   ├── login.py             # Login logic
│   ├── uploader.py          # Video upload logic
│   └── utils.py             # Utility functions
├── config/
│   └── config.yaml          # Configuration file
├── data/
│   ├── cookies/             # Cookie storage
│   └── videos/              # Videos to upload
├── logs/                    # Log directory
├── docker/
│   ├── Dockerfile
│   └── docker-compose.yml
├── requirements.txt         # Python dependencies
├── .env.example             # Environment variable template
├── .gitignore
└── README.md
```

---

## Key Technical Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| **TikTok Anti-Bot Detection** | Use `undetected-chromedriver`, simulate real user behavior (random delays, mouse movements) |
| **Login State Persistence** | Reuse Chrome user data directory (`--user-data-dir`) or export/import cookies |
| **Headless Mode Limitations** | Configure correct user-agent and window size to avoid robot detection |
| **Slow Video Upload** | Add explicit waits (WebDriverWait), handle large file upload timeouts |
| **Running Chrome in Docker** | Use `selenium/standalone-chrome` official image or custom image |

---

## Workflow Diagram

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│ Init Browser │ ──▶ │ Load Login  │ ──▶ │ Open Upload │ ──▶ │ Select Video│
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
                                                                   │
                                                                   ▼
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│Close Browser│ ◀── │Confirm Post │ ◀── │Click Publish│ ◀── │ Fill Details│
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
```

---

## Dependencies

```
selenium>=4.15.0
undetected-chromedriver>=3.5.0
webdriver-manager>=4.0.0
python-dotenv>=1.0.0
pyyaml>=6.0
loguru>=0.7.0
```
