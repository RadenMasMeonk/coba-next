# CGTrader Model Downloader

Downloads 3D models from CGTrader.com using Selenium + ChromeDriver.

## ⚠️ Important

- **Chrome + ChromeDriver required** — Firefox is not supported. Install [ChromeDriver](https://chromedriver.chromium.org/) matching your Chrome version, or use `webdriver-manager` (auto-installs correct driver).
- This script creates temporary throw-away accounts via GuerrillaMail if none exist in `data/accounts.json`. For best results, add your own CGTrader credentials there first.
- CGTrader frequently changes their UI — CSS selectors may break and need updating.

## Setup

```powershell
# 1. Install Python 3
# 2. Install dependencies
pip install -r requirements.txt

# 3. Ensure Chrome browser is installed
# 4. (webdriver-manager auto-downloads correct ChromeDriver)
```

## Usage

```powershell
python main.py "https://www.cgtrader.com/3d-models/character/fantasy-character/yi-sun-shin-lone-destructor"
```

Pass multiple model URLs as space-separated arguments:

```powershell
python main.py "url1" "url2" "url3"
```

### Flags

- `-v` / `--verbose` — print verbose status (controlled via `config.json`)
- `-\?` / `-h` / `--help` — show this help and exit

## Config

Edit `config.json`:

```json
{
  "modelsBasePath": "models",          // folder to store downloaded models
  "override": false,                   // overwrite existing model dirs?
  "autoRestart": false,                // rerun forever on error (use with caution)
  "verbose": true                      // print per-model progress
}
```

## Account Management

The script can create temporary accounts via GuerrillaMail (disposable email). 
To use your own account instead, create `data/accounts.json`:

```json
[
  {
    "_id": "1",
    "username": "YOUR_CGTRADER_USERNAME",
    "password": "YOUR_CGTRADER_PASSWORD",
    "email": "YOUR_EMAIL",
    "download_count": 0
  }
]
```

## Disclaimer

Provided for educational purposes. Respect CGTrader's terms of service.

## Troubleshooting

- If script hangs with `************`, the CGTrader UI has likely changed — update CSS selectors in `cgtrader_accounts.py`.
- Ensure `chromedriver` is in your PATH or use `webdriver-manager`.