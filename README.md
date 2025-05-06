# Spatial Video Demos

## Stereo Viewer

This repository includes a minimal stereo viewer application for Meta Quest built with the [Spatial SDK](https://developers.meta.com/horizon/develop/spatial-sdk). To get started:
1. Open project root in Android Studio
2. Set `LK_SERVER` and `LK_TOKEN` in  [*ImmersiveActivity.kt*](/LiveKitStereoViewer/app/src/main/java/io/livekit/LiveKitStereoViewer/ImmersiveActivity.kt)
3. Build and run on device

When run, a viewer panel will appear in the immersive environment. Once a stereoscopic video track is published by a remote participant, it will be displayed on the panel. See the following section for setting up ingress to get a video to display.

## Ingress
If not already familiar with ingress, please begin by reading [Ingress Overview](https://docs.livekit.io/home/ingress/overview/) from the LiveKit docs.

### Camera Input
TODO:

### Static Video
For testing purposes, ingest a stereoscopic video from a static file:

1. Make sure `LIVEKIT_URL`, `LIVEKIT_API_KEY`, and `LIVEKIT_API_SECRET` are set in the environment.
2. Set the url property in `requests/static.json` to point to the video file to ingest (or use the default).
3. Create the ingress:
```
lk ingress create requests/static.json
```

### File hosting

The video file needs to be served from an HTTP server with the proper MIME type set in order for ingress to work. I used this procedure to host static video files using Google Drive for testing:

1. Upload media to Google Drive
2. Share the file, set access to "Anyone with link". Copy the share URL
3. The share URL will have the following format: `https://drive.google.com/file/d/<id>/view?usp=sharing`. Using the file's ID, rewrite the URL as follows: `https://drive.google.com/uc?id=<id>` for direct access.

Here are a few examples I have already prepared:
- Fish: https://drive.google.com/uc?id=1DrBMHqvQIoJkrOsDSQDhaWWc8v0X_1zl
- Dog: https://drive.google.com/uc?id=1DqNowRNXLK_HQ2ilgAVU6BaF3qGp0o4j