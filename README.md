# 🎵 YouTube Audio Splitter

[![Python](https://img.shields.io/badge/python-3.7+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![yt-dlp](https://img.shields.io/badge/yt--dlp-latest-red.svg)](https://github.com/yt-dlp/yt-dlp)

> Transform YouTube videos into perfectly split audio tracks with just a timestamp file!

## 🚀 Features

- **🎯 Single Download** - Downloads the YouTube video only once, saving bandwidth and time
- **✂️ Precise Splitting** - Split audio at exact timestamps with millisecond precision
- **📝 Simple Format** - Use a plain text file with timestamps and track names
- **🎨 Customizable Quality** - Choose from 128, 192, 256, or 320 kbps MP3
- **📁 Organized Output** - Automatically numbers tracks and creates output directories
- **🌍 Unicode Support** - Handles international characters in track names
- **⚡ Efficient** - Uses pydub for fast audio processing

## 📋 Requirements

- Python 3.7+
- FFmpeg
- yt-dlp
- pydub

## 🛠️ Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/yourusername/youtube-audio-splitter.git
    cd youtube-audio-splitter
    ```

2. Install Python dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. Install FFmpeg:
- **Windows**: Download from [FFmpeg website](https://www.gyan.dev/ffmpeg/builds/) or use [Chocolatey](https://chocolatey.org/install) to install: `choco install ffmpeg`
- **macOS**: `brew install ffmpeg`
- **Linux**: `sudo apt install ffmpeg`

## 📖 Usage

### Basic Usage

1. Create a tracklist file (`tracks.txt`):
    ```
    0:00:00 - Opening Theme
    0:03:45 - Epic Battle
    0:07:30 - Victory Celebration
    0:11:15 - Closing Credits
    ```

2. Run the splitter:
    ```bash
    python youtube_audio_splitter.py "https://youtube.com/watch?v=VIDEO_ID" tracks.txt
    ```

### Advanced Options

```bash
# Custom output directory
python youtube_audio_splitter.py "URL" tracks.txt -o "Album Name"

# Different quality settings
python youtube_audio_splitter.py "URL" tracks.txt -q 192

# Keep the original downloaded file
python youtube_audio_splitter.py "URL" tracks.txt -k
```

### Command Line Options

| Option | Description | Default |
|--------|-------------|---------|
| `url` | YouTube video URL | Required |
| `tracklist` | Text file with timestamps | Required |
| `-o, --output-dir` | Output directory name | `output` |
| `-q, --quality` | MP3 bitrate (128/192/256/320) | `320` |
| `-k, --keep-original` | Keep the complete audio file | `False` |


### ⚠️ Important Notes

1. **320kbps** is the maximum quality for MP3
2. Not all YouTube videos have audio quality sufficient to justify 320kbps
3. yt-dlp will always download the best available quality and convert to the specified bitrate
4. For music, 320kbps is ideal; for podcasts or narration, 192kbps may be sufficient

## 📝 Tracklist Format

The tracklist file supports various formats:

```
# Comments start with #
# Format: TIMESTAMP - TRACK NAME

0:00:00 - First Track
03:45 - Second Track       # HH:MM:SS or MM:SS
7:30 | Third Track         # Various separators supported
11:15 : Fourth Track
1:23:45 - Long Track       # Supports hours
```

## 🎯 Use Cases

- **📀 Album Splits** - Split full album uploads into individual tracks
- **🎙️ Podcast Chapters** - Extract specific segments from long podcasts
- **🎼 Music Mixes** - Split DJ sets or compilation videos
- **📚 Audiobook Chapters** - Divide audiobooks into chapters
- **🎓 Educational Content** - Extract specific lessons from long tutorials

## 💡 Pro Tips

### **Quality Guidelines**:
   - 320 kbps: Best for music (2.4 MB/min)
   - 192 kbps: Good balance (1.4 MB/min)
   - 128 kbps: Fine for speech (1 MB/min)

   **Practical example:**

   A 60-minute album will result in approximately:
   - 128 kbps: ~60 MB
   - 192 kbps: ~84 MB
   - 256 kbps: ~114 MB
   - 320 kbps: ~144 MB


### **Timestamp Accuracy**
YouTube's audio might have slight variations, so add 1-2 seconds padding if needed

### **Batch Processing**
 Create a shell script to process multiple videos:
   ```bash
   #!/bin/bash
   python youtube_audio_splitter.py "URL1" album1.txt -o "Album 1"
   python youtube_audio_splitter.py "URL2" album2.txt -o "Album 2"
   ```

### File organization
Recommended structure:
```
project/
├── youtube_audio_splitter.py
├── tracklists/
│   ├── album1.txt
│   ├── album2.txt
│   ├── audiobook.txt
│   └── podcast.txt
└── output/
    ├── album1/
    ├── album2/
    ├── audiobook/
    └── podcast/
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚠️ Disclaimer

This tool is for personal use only. Please respect copyright laws and YouTube's Terms of Service. Only download content you have permission to use.

## 🙏 Acknowledgments

- [yt-dlp](https://github.com/yt-dlp/yt-dlp) - YouTube downloading backend
- [pydub](https://github.com/jiaaro/pydub) - Audio processing
- [FFmpeg](https://ffmpeg.org/) - Audio conversion

---

**Made with ❤️ by Vitor R. Di Toro"**

*If you find this tool useful, please consider giving it a ⭐!*