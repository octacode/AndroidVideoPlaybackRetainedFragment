This sample projects demonstrates video playback in Android using a retained Fragment rather than an Activity that handles configuration changes manually.  The resulting experience is identical to how the YouTube app handles rotation during video playback.  In other words, the video does not need to be paused, rebuffered, or reloaded, and does not skip or drop any audio frames when the device orientation changes.

This implementation uses a TextureView and its accompaning SurfaceTexture to dump vieo frames to.  A SurfaceTexture uses a GL texture object (referenced by an integer from the GL context).  Thus, I believe it's okay to retain a reference to a SurfaceTexture through configuration changes.  The TextureView itself is destroyed and recreated during the configuration change (along with the backing Activity) and the newly created TextureView is simply update with the SurfaceTexture reference before it is attached.