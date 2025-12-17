# eyeD3 ID3v2 Metadata Management Guide

## Basic Commands

### View Metadata
```bash
eyeD3 song.mp3
```

## Core Metadata Fields

### Title
```bash
eyeD3 --title "Song Title" song.mp3
```

### Artist
```bash
eyeD3 --artist "Artist Name" song.mp3
```

### Album
```bash
eyeD3 --album "Album Name" song.mp3
```

### Track Numbers
```bash
# Set current track number and total tracks
eyeD3 --track "01" --track-total "12" song.mp3
```

### Dates
```bash
# Format: yyyy, yyyy-mm, or yyyy-mm-dd
eyeD3 --release-date "2024-10-30" --recording-date "2024-10-15" song.mp3
```

### Comments
```bash
# Basic comment
eyeD3 --add-comment "Your comment text" song.mp3

# Comment with description and language
eyeD3 --add-comment "Comment text:Description:eng" song.mp3
```

## Images (APIC Frames)

### Adding Images
```bash
# Basic syntax
eyeD3 --add-image image_path:PICTURE_TYPE song.mp3

# With description
eyeD3 --add-image image_path:PICTURE_TYPE:"Description" song.mp3
```

### Common Picture Types

| Type | Description |
|------|-------------|
| `FRONT_COVER` | Front album cover |
| `BACK_COVER` | Back album cover |
| `ARTIST` | Artist/performer image |
| `BAND` | Band/group photo |
| `OTHER` | Generic/other image |


### Examples
```bash
# Add front cover
eyeD3 --add-image cover.jpg:FRONT_COVER song.mp3

# Add multiple images with descriptions (recommended)
eyeD3 --add-image front.jpg:FRONT_COVER:"Front Cover" song.mp3
eyeD3 --add-image back.jpg:BACK_COVER:"Back Cover" song.mp3
eyeD3 --add-image artist.jpg:ARTIST:"Artist Photo" song.mp3
```

> **Important:** When adding multiple images, always include descriptions to prevent them from overwriting each other.

## Lyrics

### Unsynchronized Lyrics (USLT)
```bash
# Add lyrics from file
eyeD3 --add-lyrics lyric_path song.mp3

# With description
eyeD3 --add-lyrics lyric_path::"Description" song.mp3

# With description and language
eyeD3 --add-lyrics lyric_path::"Description":"eng" song.mp3
```

### Synchronized Lyrics (SYLT)
```bash
# eyeD3 doesn't support SYLT, use kid3-cli instead
kid3-cli -c "set SYLT:'lyric.lrc' 'Song synced lyric'" song.mp3

# View SYLT frames with exiftool
exiftool -SYLT song.mp3
```

> **Note:** eyeD3 cannot handle synchronized lyrics (SYLT). Use kid3-cli for writing and exiftool for viewing SYLT frames.

## Advanced Fields

### URL Frames
```bash
# Add user-defined URL
eyeD3 --user-url-frame "Description":"https://example.com" song.mp3

# Add multiple URLs (use different descriptions)
eyeD3 --user-url-frame "Official Website":"https://artist.com" song.mp3
eyeD3 --user-url-frame "Streaming":"https://music.service.com/track" song.mp3
```

### Custom Text Frames
```bash
# Add user-defined text field (key-value pair)
eyeD3 --user-text-frame "Custom Key:Custom Value" song.mp3

# Examples
eyeD3 --user-text-frame "Mood:Energetic" song.mp3
eyeD3 --user-text-frame "BPM:120" song.mp3
```

### Binary Objects (GEOB)
```bash
# Add arbitrary binary data
eyeD3 --add-object path:"mime/type" song.mp3

# With description
eyeD3 --add-object path:"mime/type":"Description" song.mp3

# With description and owner ID
eyeD3 --add-object path:"mime/type":"Description":"Owner ID" song.mp3

# Example
eyeD3 --add-object data.pdf:"application/pdf":"Liner Notes":"publisher@example.com" song.mp3
```

## Batch Processing Examples

### Update Multiple Fields at Once
```bash
eyeD3 --title "Song Title" \
      --artist "Artist Name" \
      --album "Album Name" \
      --track "01" \
      --track-total "12" \
      --release-date "2024" \
      --add-image cover.jpg:FRONT_COVER \
      song.mp3
```
