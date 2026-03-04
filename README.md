# bilibili-cli

A CLI for Bilibili — browse videos, users, favorites from the terminal 📺

## Features

- 🎬 **Video details** — view title, stats, subtitles for any BV video
- 👤 **User profiles** — look up UP主 info and their latest videos
- 🔍 **Search** — search users by keyword
- 📂 **Favorites** — browse your favorite folders and videos
- 🔐 **Smart auth** — auto-extracts cookies from Chrome/Firefox, or QR code login
- 📊 **JSON output** — all commands support `--json` for scripting

## Installation

```bash
pip install bilibili-cli
```

Or from source:

```bash
git clone git@github.com:jackwener/bilibili-cli.git
cd bilibili-cli
uv sync
```

## Usage

```bash
# Check login status (auto-detects browser cookies)
bili status

# Or login via QR code
bili login

# View video details
bili video BV1vezvBsEzV
bili video BV1vezvBsEzV --subtitle    # show subtitles
bili video BV1vezvBsEzV --json        # raw JSON output

# View UP's profile and recent videos
bili user 946974
bili user "影视飓风" --count 20

# Search users
bili search "影视飓风"

# Browse favorites (requires login)
bili favorites
bili favorites <收藏夹ID> --page 2
```

## Authentication

bilibili-cli uses a 3-tier authentication strategy:

1. **Saved credential** — loads from `~/.bilibili-cli/credential.json`
2. **Browser cookies** — auto-extracts `SESSDATA`/`bili_jct` from Chrome, Firefox, Edge, or Brave via `browser-cookie3`
3. **QR code login** — `bili login` displays a QR code in the terminal for Bilibili App scan

Most commands work without login. Subtitles and favorites require authentication.

## License

Apache-2.0
