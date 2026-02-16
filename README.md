# Facebook Reel Downloader

Download public Facebook reels and videos to local MP4 files.

This repository is organized in marketplace-compatible layout, with installable skill content under `skill/`.

## Features

- Extracts HD video when available, with SD fallback.
- Detects and downloads separate audio streams when needed.
- Muxes video + audio with `ffmpeg` without re-encoding.
- Supports common Facebook reel/watch/video URL formats.

## Repository Layout

```text
fb-reel-downloader/
├── README.md
├── .gitignore
└── skill/
    ├── SKILL.md
    └── scripts/
        └── fb_downloader.py
```

## Prerequisites

- Python 3.8+
- `ffmpeg`

Install `ffmpeg`:

- macOS: `brew install ffmpeg`
- Ubuntu/Debian: `sudo apt install ffmpeg`
- Windows: `winget install ffmpeg`

## Usage

Run from repository root:

```bash
python skill/scripts/fb_downloader.py <facebook_url> [output_directory]
```

With `uv`:

```bash
uv run skill/scripts/fb_downloader.py <facebook_url> [output_directory]
```

Examples:

```bash
python skill/scripts/fb_downloader.py https://www.facebook.com/reel/856954873853388
python skill/scripts/fb_downloader.py https://www.facebook.com/watch?v=1234567890 ~/Downloads
python skill/scripts/fb_downloader.py https://fb.watch/abcDEF12/
```

## Supported URL Formats

- `https://www.facebook.com/reel/{id}`
- `https://www.facebook.com/watch?v={id}`
- `https://www.facebook.com/videos/{id}`
- `https://fb.watch/{shortcode}`

## Limitations

- Public videos only.
- Private, region-locked, or login-required videos may fail.
- Facebook markup/API changes can break extraction patterns.

## GitHub Submission Notes

- Keep installable skill files in `skill/`.
- Avoid committing downloaded media outputs.
- Add a license file before public release if you want explicit reuse terms.
