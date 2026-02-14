<div align='center'>
  <h1> 17. Media Services & WebRTC </h1>
  <h2> On-demand Streaming AWS Pipeline </h2>
</div>

# Table of Contents

- [On-demand Streaming AWS Pipeline](#on-demand-streaming-aws-pipeline)

---

# On-demand Streaming AWS Pipeline

```bash
Amazon S3 (raw video source) → MediaConvert (transcoding) → MediaPackage (optional: encryption, DVR, playback) → CloudFront (content delivery at scale) → End Users
```
