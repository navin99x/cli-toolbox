# yt-dlp 🎬 📥 🚀

> A modern, feature-rich fork of `youtube-dl`, serves as the ultimate command-line companion for downloading videos and audio from YouTube and beyond! 🌐

---

## 📦 Installation

**Linux/macOS/WSL:**
```bash
sudo curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
sudo chmod a+rx /usr/local/bin/yt-dlp
```

**Windows:**

- Download yt-dlp.exe file from [yt-dlp GitHub Release](https://github.com/yt-dlp/yt-dlp?tab=readme-ov-file#recommended "yt-dlp GitHub repo").
- Add it to your system `PATH`.

## 🧰 Basic Usage

```bash
yt-dlp [options] <URL>
```

Replace \<URL\> with link to video or playlist you want to download.

## ⚙️ Essential Commands

### 🎥 Video Downloads

1. Download a video at best quality.

```bash
yt-dlp https://www.youtube.com/watch?v=xrIWVqvgMvk
```

2. Download to a particular path (default is current directory).

```bash
yt-dlp -P <path> <URL>
```

3. List all available formats for a video.

```bash
yt-dlp -F <URL>
```

4. Download specific format (get ID from -F command).

```bash
yt-dlp -f 22 <URL>
```

### 🔍 Quality Selection

5. Best video and audio quality (default).

```bash
yt-dlp -f "bestvideo+bestaudio" <URL>
```

6. 1080p video with best audio.

```bash
yt-dlp -f "bestvideo[height=1080]+bestaudio" <URL>
```

7. MP4 video up to 720p.
   
```bash
yt-dlp -f "bestvideo[height<=720][ext=mp4]+bestaudio[ext=m4a]/mp4" <URL>
```

### 🎵 Audio Options

8. Download best audio only.

```bash
yt-dlp -f bestaudio <URL>
```

9. Download best audio and convert it to mp3 format.

```bash
yt-dlp -f bestaudio --extract-audio --audio-format mp3 <URL>
```

10.  Embed thumbnail in audio file.

```bash
yt-dlp -x --audio-format mp3 --embed-thumbnail <URL>
```

### 📋 Naming & Organization

13. Download with specific filename (default to `"%(title)s [%(id)s].%(ext)s"`).

```bash
yt-dlp -o "%(channel)s-%(title)s.%(ext)s" <URL>
```

> Common fields for filename include:
> `id`, `title`, `ext`, `channel`, `upload_date`, `duration`, `autonumber`, `playlist_title`, `playlist_index`, etc.

14. Create directory structure for downloads.

```bash
yt-dlp -o "%(uploader)s/%(playlist)s/%(playlist_index)s - %(title)s.%(ext)s" <URL>
```

### 📄 Subtitles & Extras

15. Download video with embedded subtitles.

```bash
yt-dlp --embed-subs <URL>
```

16. Download specific language subtitles.

```bash
yt-dlp --write-sub --sub-lang en <URL>
```

17. Download only video thumbnail.

```bash
yt-dlp --skip-download --write-thumbnail <URL>
```

18. Download video with thumbnail and metadata.

```bash
yt-dlp --write-thumbnail --add-metadata <URL>
```

## 🎞️ Working with Playlists

19. Download all videos from playlist.

```bash
yt-dlp <Playlist_URL>
```
> Use `--no-playlist` when downloading just one video from playlist URL.

20. Download specific videos from playlist.

```bash
yt-dlp --playlist-items 2,4-6,-1 <Playlist_URL>
```

> This will download 2nd, 4th, 5th, 6th and last videos on that playlist.

21. Download all videos from a channel.

```bash
yt-dlp https://www.youtube.com/c/ChannelName
```

## 🔄 Advanced Options

22. Resume partially downloaded files.

```bash
yt-dlp -c <URL>
```

23. Download through a proxy.

```bash
yt-dlp --proxy http://proxy.example.com:8000 <URL>
```

24. Download from list of URLs.

```bash
yt-dlp -a urls.txt
```

1.  Limit download rate.

```bash
yt-dlp --limit-rate 1M <URL>
```

27. Skip files that already exist.

```bash
yt-dlp --no-overwrites <URL>
```

## 🔐 Authentication

29. Login with username and password (for sites like Udemy).

```bash
yt-dlp -u username -p password <URL>
```

30. Use cookies from browser.

```bash
yt-dlp --cookies-from-browser chrome <URL>
```

31. Use cookies file.

```bash
yt-dlp --cookies cookies.txt <URL>
```

## 🧹 Maintenance

32. Update `yt-dlp`.

```bash
yt-dlp -U
```

---

## 📚 Resources
- [yt-dlp github](https://github.com/yt-dlp/yt-dlp)
- [RapidSeedbox Guide](https://www.rapidseedbox.com/blog/yt-dlp-complete-guide)
- [CommandMasters Guide](https://commandmasters.com/commands/yt-dlp-common/)

## 💡 My Use Cases

- 🎓 Downloading educational playlists
- 🎵 Archiving music videos into audio libraries
- 📺 Saving offline copies of tutorials
- 🔖 Creating personal collections of documentaries
