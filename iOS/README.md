FAQ
====

1. AVAssetReaderTrackOutput
----

**Question:**
CGBitmapContextCreateImage: invalid context 0x0.

**Solution:**
```
NSDictionary *settings = @{
  (id)kCVPixelBufferPixelFormatTypeKey: [NSNumber numberWithUnsignedInt:kCVPixelFormatType_32BGRA]
};
[[AVAssetReaderTrackOutput alloc] initWithTrack:track outputSettings:settings];
```

2. AVAssetReaderTrackOutput
----

**Question:**
Blank image frame, with correct width & height, using the snippet [here](http://stackoverflow.com/questions/3305862/uiimage-created-from-cmsamplebufferref-not-displayed-in-uiimageview).

**Solution:**
replace [CVPixelBufferGetBaseAddressOfPlane](https://developer.apple.com/library/Mac/DOCUMENTATION/QuartzCore/Reference/CVPixelBufferRef/Reference/reference.html#//apple_ref/c/func/CVPixelBufferGetBaseAddressOfPlane) with [CVPixelBufferGetBaseAddress](https://developer.apple.com/library/Mac/DOCUMENTATION/QuartzCore/Reference/CVPixelBufferRef/Reference/reference.html#//apple_ref/c/func/CVPixelBufferLockBaseAddress)
```
uint8_t *baseAddress = (uint8_t *)CVPixelBufferGetBaseAddress(imageBuffer);
// uint8_t *baseAddress = (uint8_t *)CVPixelBufferGetBaseAddressOfPlane(imageBuffer, 0);
```

3. AVAssetReaderTrackOutput
----

**Question:**
Blank image frame, when using while to grab the video frame

**Solution:**
Use a timer based on the FPS of the video.
```
    NSTimer *timer = [NSTimer timerWithTimeInterval:1 / self.videoFPS
                                           target:self
                                         selector:@selector(onTimer:)
                                         userInfo:nil repeats:YES];
    [[NSRunLoop mainRunLoop] addTimer:timer forMode:NSRunLoopCommonModes];
```
