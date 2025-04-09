# gallery-dl 🖼️ 

> A powerful command-line program designed to download image galleries and collections from various websites 🌐 including Pinterest, DeviantArt, Discord, flickr, Instagram and hundreads more.

---

## 📦 Installation

**Linux/macOS/WSL:**

### Using pip
pip install -U gallery-dl

### Manual installation

```bash
sudo curl -L https://github.com/mikf/gallery-dl/releases/latest/download/gallery-dl -o /usr/local/bin/gallery-dl
sudo chmod a+rx /usr/local/bin/gallery-dl
```

**Windows:**

- Download gallery-dlp.exe file from [gallery-dl GitHub Release](https://github.com/mikf/gallery-dl/tree/master?tab=readme-ov-file).
- Add it to your system `PATH`.

## 🧰 Basic Usage

```bash
gallery-dl [options] <URL>
```

Replace \<URL\> with link to the gallery or image you want to download.

## ⚙️ Essential Commands

### 🖼️ Basic Downloads

1. Download images from a URL.

```bash
gallery-dl <URL>
```

2. Download multiple URLs.

```bash
gallery-dl <URL-1> <URL-2>
```

3. Download from a text file containing URLs (one per line).

```bash
gallery-dl -i urls.txt
```

4. Only retrive URl's

```bash
gallery-dl --get-urls <URL>
```

### 📁 Output Options

5. Specify output directory.

```bash
gallery-dl -D /path/to/download/directory <URL>
```

6. Use a custom filename pattern.

```bash
gallery-dl -o filename="{id}_{title}.{extension}" URL
```

7. Skip existing files (don't redownload).

```bash
gallery-dl --no-skip URL
```

### 🔍 Filtering & Selection

8. Download only the first 10 images.

```bash
gallery-dl --range 1-10 URL
```

9.  Filter images by width.

```bash
gallery-dl --filter "width == 1080" URL
```

10. Filter images by extension.

```bash
gallery-dl --filter "extension == 'png'" URL
```

## 🔄 Advanced Options

### 📊 Download Management

11. Limit download rate (e.g., 500 KB/s).

```bash
gallery-dl --limit-rate 500k <URL>
```

12. Add Dealy to avoid rate limits.

```bash
gallery-dl --sleep 2 <URL>
```

### 🔐 Authentication

13. Use cookies from browser.

```bash
gallery-dl --cookies-from-browser chrome <URL>
```

14. Use cookies file.

```bash
gallery-dl --cookies cookies.txt <URL>
```

15. Use username and password.

```bash
gallery-dl -u username -p password <URL>
```

### 🧹 Maintenance

16.  Update `gallery-dl`.

```bash
gallery-dl -U
```

---

## 📚 Resources
- [gallery-dl GitHub](https://github.com/mikf/gallery-dl)
- [CommandMasters Guide](https://commandmasters.com/commands/gallery-dl-common/)

## 💡 My Use Cases

- 🎨 Archiving artwork from favorite artists
- 📸 Creating offline collections of photography
- 🖌️ Downloading inspiration for design projects
- 🌟 Saving complete image sets from social media
