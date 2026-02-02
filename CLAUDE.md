# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

"Wyld Wattage" weblog using weblog.lol service - a Rivian R1T ownership blog. Auto-publishes via GitHub Actions on push.

## How It Works

1. Write posts as Markdown in `weblog/` directory
2. Push to GitHub
3. GitHub Actions triggers `neatnik/weblog.lol@v1` action
4. Action syncs content to weblog.lol service

## Project Structure

```
weblog/                    # Blog posts (Markdown)
  YYYY-MM-DD_HH_MM_*.md    # Post filename format
configuration/
  configuration.txt        # Weblog settings
  template.html            # HTML template
.github/workflows/
  main.yml                 # Auto-publish workflow
```

## Creating Posts

Post filename format: `YYYY-MM-DD_HH_MM_title-slug.md`

Post structure:
```markdown
Date: YYYY-MM-DD HH:MM

# Post Title

Content in Markdown...
```

## Configuration

Key settings in `configuration/configuration.txt`:

| Setting | Value |
|---------|-------|
| Title | Wyld Wattage |
| Author | Zak Winnick |
| Timezone | America/Los_Angeles |
| Landing page posts | 10 |
| Feed posts | 25 |
| Search | enabled |
| Tags | enabled |
| Post path format | /Y/m/ |

## Deployment

Requires `WEBLOG_API_KEY` secret in GitHub repository settings.

Workflow (`.github/workflows/main.yml`):
```yaml
env:
  ADDRESS: zak
  WEBLOG_API_KEY: ${{ secrets.WEBLOG_API_KEY }}
```

Runs on every push to any branch.

## Social Links

Configured in navigation:
- wyldwattage.com (main site)
- youtube.com/@wyldwattage
- instagram.com/wyldwattage
- x.com/wyldwattage
