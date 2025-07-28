<div align='center'>
  <h1> Media Service & WebRTC </h1>
</div>

# Table of Contents

- [Elemental MediaLive](#Elemental-MediaLive)
- [Elemental MediaConvert](#Elemental-MediaConvert)
- [Elemental MediaPackage](#Elemental-MediaPackage)
- [IVS](#IVS)
- [Chime SDK](#Chime-SDK)
- [On-demand Streaming AWS Pipeline](#On-demand-Streaming-AWS-Pipeline)
- [Live Streaming AWS Pipeline](#Live-Streaming-AWS-Pipeline)

---

# [Elemental MediaLive](https://aws.amazon.com/medialive/)

Elemental MediaLive is a real-time video encoder for **live streaming** used to convert raw video streams into compressed formats for broadcast. It does not deliver content to end users.

# [Elemental MediaConvert](https://aws.amazon.com/mediaconvert/)

Elemental MediaConvert is a professional-grade, file-based video transcoding service used to convert **on-demand** video content (e.g., MP4 uploads) into adaptive bitrate streaming formats (e.g., HLS, DASH, CMAF) and other codecs, including AVC (H.264 or MPEG-4 Part 10), HEVC (H.265), and more.

# [Elemental MediaPackage](https://aws.amazon.com/pt/mediapackage/)

Elemental MediaPackage serves the video content into adaptive bitrate streaming formats (e.g., HLS, DASH, CMAF) and enables DVR features (pause, resume, start-over) using offset.

# [IVS](https://aws.amazon.com/ivs/)

IVS can handle the entire live video streaming pipeline from ingestion to delivery.

# [Chime SDK](https://aws.amazon.com/chime/chime-sdk/)

"Deliver high-quality audio, video, and screenshare in your e-learning applications." —AWS.

Amazon Chime is suitable for high-throughput, real-time audio/video communication (e.g., video calls). It uses WebRTC under the hood and includes built-in NAT traversal support using the ICE framework, without the need to set up STUN or TURN servers.

# On-demand Streaming AWS Pipeline

```bash
AWS S3 (raw video source) → MediaConvert (transcoding) → MediaPackage (optional: encryption, DVR, playback) → CloudFront (content delivery at scale) → End Users
```

# Live Streaming AWS Pipeline

```bash
MediaLive (real-time encoding) → MediaPackage (optional: encryption, DVR, playback) → CloudFront (content delivery at scale) → End Users
```
