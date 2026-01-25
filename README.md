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

## ⚡ Installation Guide (For Claude Code Users)

> 🎯 **Super Easy**: Just tell Claude what you need, and Claude will handle most of the work for you!

### 🤖 Let Claude Help You Install

If you're using Claude Code, simply say:

> "Help me install the dependencies for media-downloader"

Claude will automatically check and install the required tools. Just click "Allow" when Claude asks for permission.

---

### 📝 Manual Installation (If You Prefer)

#### Step 1: Download the Skill

Tell Claude: **"Help me download media-downloader to the skills folder"**

Or run this yourself in Terminal:
```bash
mkdir -p ~/.claude/skills && cd ~/.claude/skills && git clone https://github.com/yizhiyanhua-ai/media-downloader.git
```

#### Step 2: Install Required Tools

Tell Claude: **"Help me install yt-dlp and ffmpeg"**

Claude will run the installation commands for you. If you prefer to do it yourself:
```bash
pip install requests yt-dlp && brew install ffmpeg
```

> 💡 **What is brew?** It's a package manager for Mac. If you see "brew not found", tell Claude **"Help me install Homebrew"**, or visit https://brew.sh and follow the instructions.

#### Step 3: Get Your Free API Key

This step requires you to register an account yourself:

1. Open your browser and go to **https://www.pexels.com**
2. Click **Join** in the top right corner
   - You can use Google or Apple account for quick signup!
3. After signing up, visit **https://www.pexels.com/api/**
4. Click **Your API Key** button
5. You'll see a string of letters and numbers - that's your API Key. **Copy it**

#### Step 4: Save Your API Key

Tell Claude: **"Help me save my Pexels API Key to environment variables"**

Then paste your API Key when Claude asks.

Or run this yourself (replace `your_key` with your actual key):
```bash
echo 'export PEXELS_API_KEY="your_key"' >> ~/.zshrc && source ~/.zshrc
```

#### Step 5: Verify Installation

Tell Claude: **"Check if media-downloader is installed correctly"**

Or run:
```bash
python ~/.claude/skills/media-downloader/media_cli.py status
```

If you see green ✅ marks, you're all set! 🎉

---

## 📋 More API Keys (Optional)

> 💡 **Why do I need API Keys?**
>
> Think of an API Key as a "membership card" for stock photo websites. With it, you can search and download HD images and videos.
>
> **Good news**: Registration is completely free, and all assets are free for commercial use!

The quick install above only configured Pexels. If you want more image sources, you can register for these:

### 🟢 Pixabay (More Assets)

1. Go to **https://pixabay.com**
2. Click **Join** in the top right corner
3. After signup, visit **https://pixabay.com/api/docs/**
4. Your API Key will be displayed right on the page (in the green box)
5. Tell Claude: **"Help me save my Pixabay API Key to environment variables"**, then paste your key

### 🔵 Unsplash (More Artistic Images)

1. Go to **https://unsplash.com/developers**
2. Click **Register as a developer**
3. Create an Application (just give it any name)
4. Find and copy the **Access Key**
5. Tell Claude: **"Help me save my Unsplash API Key to environment variables"**

### 🔧 Having Issues?

Tell Claude: **"Check the status of media-downloader"**

Claude will tell you which tools are installed and which API Keys are configured. Just fix what's missing!

---

## 💬 Usage Examples

> ⚠️ **Important**: Before using, tell Claude **"Check the status of media-downloader"** to make sure all dependencies are installed!

### Download Images

```
"Download 5 starry sky images"
"Download 10 coffee shop photos"
"Find some landscape images suitable for wallpapers"
```

### Download Videos

> 💡 **Recommended**: If you need to download videos, **use YouTube first**! YouTube has rich content, high quality, and doesn't require an extra API Key.

```
"Download this video: https://youtube.com/watch?v=xxx"
"Download minute 2 to minute 3 of this YouTube video"
"Only download the audio from this video"
```

If you need short video clips from stock libraries:

```
"Download a city night video, under 30 seconds"
"Find me a 15-second ocean wave video"
"Find some natural scenery videos suitable for backgrounds"
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
