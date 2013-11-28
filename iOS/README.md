1. AVAssetReaderTrackOutput
----

**Context:**
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

**Context**
Blank image frame, with correct width & height, using the snippet [here](http://stackoverflow.com/questions/3305862/uiimage-created-from-cmsamplebufferref-not-displayed-in-uiimageview).

**Solution:**
replace [CVPixelBufferGetBaseAddressOfPlane](https://developer.apple.com/library/Mac/DOCUMENTATION/QuartzCore/Reference/CVPixelBufferRef/Reference/reference.html#//apple_ref/c/func/CVPixelBufferGetBaseAddressOfPlane) with [CVPixelBufferGetBaseAddress](https://developer.apple.com/library/Mac/DOCUMENTATION/QuartzCore/Reference/CVPixelBufferRef/Reference/reference.html#//apple_ref/c/func/CVPixelBufferLockBaseAddress)
```
uint8_t *baseAddress = (uint8_t *)CVPixelBufferGetBaseAddress(imageBuffer);
// uint8_t *baseAddress = (uint8_t *)CVPixelBufferGetBaseAddressOfPlane(imageBuffer, 0);
```

