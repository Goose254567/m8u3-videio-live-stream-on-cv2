Here is the plain text README file content (no markdown, no highlighting):

HLS Live Stream Player

A Python script that continuously downloads HLS (m3u8) video segments and plays them in real time using OpenCV.

Features

- Continuously fetches the latest m3u8 playlist and downloads new segments as they become available
- Plays video segments seamlessly using OpenCV
- Background download thread prevents buffering delays
- Handles both absolute and relative segment URLs
- Stops cleanly by pressing the Q key

Requirements

Python 3.6 or newer
OpenCV (cv2)
Requests library

Installation

pip install opencv-python requests

Usage

1. Get a fresh m3u8 URL from your browser's developer tools (Network tab) while the live stream is playing.
2. Replace the M3U8_URL variable in the script with your URL.
3. Adjust HEADERS and COOKIES if necessary (for example Referer or User-Agent).
4. Run the script:

python hls_player.py

Press Q in the video window to stop playback.

Important Notes

The m3u8 URL expires quickly, often after a few minutes. You must obtain a fresh URL each time you run the script.

Some streams require specific headers like Referer or cookies. Update them in the script.

The script does not re-encode or permanently save the stream. It plays segments on the fly.

Encrypted streams (AES-128) are not supported.

How It Works

A background thread periodically requests the m3u8 playlist. It extracts new segment URLs and downloads them. Each segment is written to a temporary file and played frame by frame with OpenCV. The main thread displays the video while the downloader keeps the queue filled.

Troubleshooting

403 Forbidden: The URL expired or headers are incorrect. Get a new m3u8 link.

No video window: Check your OpenCV installation. cv2.imshow requires a GUI backend.

Segments not playing: The stream may be encrypted. This script does not support decryption.

License

MIT
