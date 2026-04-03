# pagemap

Crawl a website and create a structured map of its pages.

## Features

- Recursive site crawling with configurable depth
- Output to CSV, JSON, and other formats
- External link detection
- Broken link checking
- Image inventory with alt text auditing
- Missing meta tag detection

## Installation

```bash
pipx install pagemap
```

## Usage

```bash
# Map all pages on a site
pagemap https://www.example.com

# Recursive crawl with JSON output
pagemap https://www.example.com --recursive --format json

# Check for broken links
pagemap https://www.example.com --check-links

# Inventory images and check alt text
pagemap https://www.example.com --images --check-alt

# Map external links
pagemap https://www.example.com --external
```

## License

MIT
