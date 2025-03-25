# Hugo Module Setup with Media Support

## Basic Setup

```bash
# Create new site
hugo new site my-new-site
cd my-new-site

# Initialize as Hugo module
hugo mod init github.com/yourusername/my-new-site
```

## Configuration (config.toml)

```toml
tou
```

## Directory Structure

```
my-new-site/
├── assets/
├── config.toml
├── content/
│   └── docs/
│       ├── _index.md
│       └── my-first-page.md
├── layouts/
│   └── shortcodes/
│       ├── audio.html
│       ├── image.html
│       └── video.html
└── static/
    ├── audio/
    ├── images/
    └── video/
```

## Media Shortcodes

### Video Shortcode (layouts/shortcodes/video.html)

```html
<video controls width="100%" preload="metadata">
  <source src="{{ .Get "src" }}" type="video/mp4">
  Your browser does not support the video tag.
</video>
```

### Audio Shortcode (layouts/shortcodes/audio.html)

```html
<audio controls preload="metadata">
  <source src="{{ .Get "src" }}" type="audio/mpeg">
  Your browser does not support the audio tag.
</audio>
```

### Image Shortcode (layouts/shortcodes/image.html)

```html
<figure>
  <img src="{{ .Get "src" }}" alt="{{ .Get "alt" }}" style="max-width: 100%;">
  {{ with .Get "caption" }}<figcaption>{{ . }}</figcaption>{{ end }}
</figure>
```

## Content Example (content/docs/my-first-page.md)

```markdown
---
title: "My First Page"
weight: 1
---

# My First Page

## Image Example
{{< image src="/images/your-image.jpg" alt="Description" caption="Image Caption" >}}

## Video Example
{{< video src="/video/your-video.mp4" >}}

## Audio Example
{{< audio src="/audio/your-audio.mp3" >}}
```

## Running the Server

```bash
hugo server -D
```

## Troubleshooting Media Files

If media files don't play:

1. Check file paths are correct
2. Verify media files are in the right format (MP4 for video, MP3 for audio)
3. Try accessing media directly at http://localhost:1313/video/your-video.mp4
4. Check browser console for errors (F12 > Console)
5. Try in different browsers (Firefox, Chrome, Edge)
