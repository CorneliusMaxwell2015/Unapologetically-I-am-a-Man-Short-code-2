🎬 Automated Workflow: Clipchamp → GitHub → YouTube

This README outlines a fully automated pipeline for exporting videos from Clipchamp, uploading them to GitHub for version control and distribution, and publishing them to YouTube with metadata and discoverability enhancements.

⚙️ Workflow Overview

Export from Clipchamp

Upload to GitHub

Trigger GitHub Action

Auto-publish to YouTube

Embed YouTube link in README

📤 Step 1: Export from Clipchamp

Export your video in 1080p MP4 format.

Save locally as Unapologetically_Trailer.mp4.

📁 Step 2: Upload to GitHub

Navigate to your GitHub repo (e.g., VideoEditingAssets).

Upload the video to /assets/videos/.

Commit with a message like Add trailer video from Clipchamp.

🤖 Step 3: GitHub Action (Auto-Publish)

Create .github/workflows/youtube-upload.yml with the following content:

name: Upload Video to YouTube

on:
  push:
    paths:
      - 'assets/videos/Unapologetically_Trailer.mp4'

jobs:
  upload:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repo
        uses: actions/checkout@v3

      - name: Upload to YouTube
        uses: ibrahimguner/youtube-upload-action@v1.2
        with:
          client_id: ${{ secrets.YOUTUBE_CLIENT_ID }}
          client_secret: ${{ secrets.YOUTUBE_CLIENT_SECRET }}
          refresh_token: ${{ secrets.YOUTUBE_REFRESH_TOKEN }}
          video_file: 'assets/videos/Unapologetically_Trailer.mp4'
          title: 'Unapologetically: I Am a Man – Official Trailer'
          description: |
            Poetry movement trailer. GitHub-powered.
            Learn more: https://github.com/your-username/VideoEditingAssets
          tags: 'poetry, empowerment, Black history, trailer'
          privacy_status: 'public'

🔗 Step 4: Embed YouTube Link in README

Once uploaded, embed the video:

## 📺 Watch the Trailer

[![Watch on YouTube](https://img.shields.io/badge/Watch-Trailer-red?logo=youtube)](https://www.youtube.com/watch?v=YOUR_VIDEO_ID)

Replace YOUR_VIDEO_ID with the actual ID from YouTube.

🧠 Pro Tips

Use GitHub Secrets to store YouTube API credentials securely.

Add thumbnails and captions via YouTube Studio.

Fork this repo to offer clients a ready-to-use pipeline.

🏁 Badge Summary

[![Watch on YouTube](https://img.shields.io/badge/Watch-Trailer-red?logo=youtube)](https://www.youtube.com/watch?v=YOUR_VIDEO_ID)

📚 License & Attribution

This workflow is part of the Cornelius Maxwell creative ecosystem. Built for scalable video editing, poetic storytelling, and GitHub-powered distribution.

© 2026 Cornelius Maxwell. All rights reserved.
