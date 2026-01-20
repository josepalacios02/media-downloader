# 🎬 Media Downloader

> Smart media downloader - Automatically search and download images/video clips based on your description, with auto-trimming support.

[🇨🇳 中文文档](./README_CN.md)

---

## 🚀 What Can I Do?

| You say... | I will... |
|------------|-----------|
| "Download some cute cat pictures" | Search and download 5 cat images |
| "Find a 15-second ocean wave video" | Download a 15s ocean wave clip |
| "Get me a 30-second cooking video" | Download a trimmed cooking clip |
| "Download this YouTube video from 1:30 to 2:00" | Download and auto-trim the specified segment |

---

## ✨ Features

- 🖼️ **Image Download** - Search HD images from professional stock libraries
- 🎬 **Video Clips** - Get free commercial-use video footage
- 📺 **YouTube Download** - Download and trim support
- ✂️ **Smart Trimming** - Auto-crop to your desired length
- 🌍 **Bilingual** - Supports both Chinese and English commands

---

## ⚡ Quick Install (1 Minute)

> 🎯 **For beginners**: Just copy and paste the commands below into your Terminal!

### Step 1: Download the Skill

Open Terminal (press `Cmd + Space`, type "Terminal", press Enter), then paste:

```bash
mkdir -p ~/.claude/skills && cd ~/.claude/skills && git clone https://github.com/yizhiyanhua-ai/media-downloader.git
```

### Step 2: Install Required Tools

```bash
pip install requests yt-dlp && brew install ffmpeg
```

> 💡 Don't have `brew`? Install it first: https://brew.sh (just copy the command from their homepage)

### Step 3: Get Your Free API Key (30 seconds)

1. Open https://www.pexels.com and click **Join** (top right)
2. After signup, go to https://www.pexels.com/api/
3. Click **Your API Key** and copy it

### Step 4: Save Your API Key

```bash
echo 'export PEXELS_API_KEY="paste_your_key_here"' >> ~/.zshrc && source ~/.zshrc
```

> ⚠️ Replace `paste_your_key_here` with your actual API key!

### Step 5: Verify Installation

```bash
python ~/.claude/skills/media-downloader/media_cli.py status
```

If you see green ✅ marks, you're all set! 🎉

---

## 📋 Detailed Setup Guide

> Already completed Quick Install? Skip to [Usage Examples](#-usage-examples)!

### Check Basic Tools

Run this command to check status:

```bash
python ~/.claude/skills/media-downloader/media_cli.py status
```

If yt-dlp or ffmpeg are not installed, run:

```bash
# Install Python dependencies
pip install requests yt-dlp

# Install video processing tool (macOS)
brew install ffmpeg

# Linux
apt install ffmpeg
```

### Step 2: Get Free API Keys

> 💡 **Why do I need API Keys?**
>
> Images and videos come from professional stock sites like Pexels and Pixabay. These sites provide free high-quality assets, but require a registered account to get an API Key (like a "pass") to use their search service.
>
> **Good news**: Registration is completely free, and all assets are free for commercial use!

#### 🟠 Get Pexels API Key (Recommended - Easiest)

1. Go to https://www.pexels.com
2. Click **Join** in the top right corner (can use Google/Apple for quick signup)
3. After registration, visit https://www.pexels.com/api/
4. Click **Your API Key** button
5. Fill in simple info, then copy the displayed API Key

#### 🟢 Get Pixabay API Key

1. Go to https://pixabay.com
2. Click **Join** in the top right corner
3. After registration, visit https://pixabay.com/api/docs/
4. Your API Key will be displayed on the page (in the green box)

#### 🔵 Get Unsplash API Key (Optional)

1. Go to https://unsplash.com/developers
2. Click **Register as a developer**
3. Create an Application
4. Find **Access Key** in the application details page

### Step 3: Save Your API Keys

Add the obtained keys to your terminal config file.

**macOS / Linux users**, edit `~/.zshrc` or `~/.bashrc`:

```bash
# Media Downloader API Keys
export PEXELS_API_KEY="your_pexels_key"
export PIXABAY_API_KEY="your_pixabay_key"
export UNSPLASH_ACCESS_KEY="your_unsplash_key"  # Optional
```

After saving, run `source ~/.zshrc` to apply the configuration.

### Step 4: Verify Setup

```bash
python ~/.claude/skills/media-downloader/media_cli.py status
```

If you see green ✅ marks, configuration is successful!

---

## 💬 Usage Examples

### Download Images

```
"Download 5 starry sky images"
"Download 10 coffee shop photos"
"Find some landscape images suitable for wallpapers"
```

### Download Video Clips

```
"Download a city night video, under 30 seconds"
"Find me a 15-second ocean wave video"
"Find some natural scenery videos suitable for backgrounds"
```

### YouTube Download & Trim

```
"Download this video: https://youtube.com/watch?v=xxx"
"Download minute 2 to minute 3 of this YouTube video"
"Only download the audio from this video"
```

---

## 📁 Download Location

By default, all files are saved to:

```
~/.claude/skills/media-downloader/downloads/
```

### Custom Download Directory

You can specify a custom download location using the `-o` or `--output` option:

```bash
# Download images to a specific folder
media_cli.py image "cats" -o ~/Pictures/cats

# Download videos to Desktop
media_cli.py video "sunset" -o ~/Desktop

# Download YouTube video to current directory
media_cli.py youtube "URL" -o .
```

Or simply tell me where you want the files:

```
"Download 5 cat images to my Desktop"
"Save the video to ~/Videos/project"
```

---

## ❓ FAQ

### Q: Why are there no image search results?
A: Please confirm API Key is configured. Run `status` command to check configuration status.

### Q: YouTube video download failed?
A: YouTube download doesn't need an API Key, but requires yt-dlp. Run `pip install yt-dlp` to install.

### Q: Video trimming doesn't work?
A: ffmpeg is required. macOS users run `brew install ffmpeg`.

### Q: Can these images/videos be used commercially?
A: Assets from Pexels, Pixabay, and Unsplash can all be used commercially for free, no attribution required (though attribution is appreciated).

---

## 🛠️ CLI Reference

For advanced users using command line directly:

```bash
# Check configuration status
media_cli.py status

# Download images
media_cli.py image "keywords" -n count -o output_dir

# Download stock videos
media_cli.py video "keywords" -d max_duration -n count

# Download YouTube video
media_cli.py youtube "URL" --start start_seconds --end end_seconds

# Search media (no download)
media_cli.py search "keywords" --type image/video/all

# Trim local video
media_cli.py trim input_file --start start --end end
```

---

## 📦 Supported Sources

| Source | Type | Features |
|--------|------|----------|
| Pexels | Images + Videos | High quality, frequently updated |
| Pixabay | Images + Videos | Large quantity, diverse categories |
| Unsplash | Images | Artistic, great for wallpapers |
| YouTube | Videos | Rich content, trimming support |

---

## 📄 License

MIT License

---

🎬 **Start using! Just tell me what images or videos you want!**
