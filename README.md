<p align="center">
  <a href="https://play.google.com/store/apps/dev?id=7086930298279250852" target="_blank">
    <img alt="" src="https://github-production-user-asset-6210df.s3.amazonaws.com/125717930/246971879-8ce757c3-90dc-438d-807f-3f3d29ddc064.png" width=500/>
  </a>  
</p>

👏 Product List

https://github.com/kby-ai/Product

👏  We have published the Face Liveness Detection, Face Recognition SDK and ID Card Recognition SDK for the server.

  - [FaceLivenessDetection-Docker](https://github.com/kby-ai/FaceLivenessDetection-Docker)

  - [FaceRecognition-Docker](https://github.com/kby-ai/FaceRecognition-Docker)

  - [IDCardRecognition-Docker](https://github.com/kby-ai/IDCardRecognition-Docker)

# FaceLivenessDetection-Android

## Overview
The demo project showcases real-time Face Liveness Detection technology.

> The demo is integrated with KBY-AI's Basic Face Mobile SDK.

  | Basic      | Standard | Premium |
  |------------------|------------------|------------------|
  | Face Detection        | Face Detection    | Face Detection |
  | Face Liveness Detection        | Face Liveness Detection    | Face Liveness Detection |
  | Pose Estimation        | Pose Estimation    | Pose Estimation |
  |         | Face Recognition    | Face Recognition |
  |         |         | 68 points Face Landmark Detection |
  |         |         | Face Quality Calculation |
  |         |         | Face Occlusion Detection |
  |         |         | Eye Closure Detection |
  |         |         | Age, Gender Estimation |

> [Face Liveness Detection - Android(Basic SDK)](https://github.com/kby-ai/FaceLivenessDetection-Android)
> 
> [Face Liveness Detection - iOS(Basic SDK)](https://github.com/kby-ai/FaceLivenessDetection-iOS)
> 
> [Face Recognition - Android(Standard SDK)](https://github.com/kby-ai/FaceRecognition-Android)
> 
> [Face Recognition - iOS(Standard SDK)](https://github.com/kby-ai/FaceRecognition-iOS)
> 
> [Face Recognition - Flutter(Standard SDK)](https://github.com/kby-ai/FaceRecognition-Flutter)
> 
> [Face Recognition - React-Native(Standard SDK)](https://github.com/kby-ai/FaceRecognition-React-Native)
>
> [Face Attribute - Android(Premium SDK)](https://github.com/kby-ai/FaceAttribute-Android)
> 
> [Face Attribute - iOS(Premium SDK)](https://github.com/kby-ai/FaceAttribute-iOS)
> 

## Try the APK

### Google Play

<a href="https://play.google.com/store/apps/details?id=com.kbyai.facelivedemo" target="_blank">
  <img alt="" src="https://user-images.githubusercontent.com/125717930/230804673-17c99e7d-6a21-4a64-8b9e-a465142da148.png" height=80/>
</a>

### Google Drive

https://drive.google.com/file/d/1U7-wHmRYb8VV32kOb6JdG_sdZA_3bSLe/view?usp=sharing

## SDK License

This project uses kby-ai's liveness detection SDK. The SDK requires a license per application ID.

- The code below shows how to use the license: https://github.com/kby-ai/FaceLivenessDetection-Android/blob/f81f001b0a2f65330d2adaabc9b001003af9a112/app/src/main/java/com/kbyai/facelivedemo/CameraActivity.java#L69-L77

- To request a license, please contact us:
```
Email: contact@kby-ai.com

Telegram: @kbyai

WhatsApp: +19092802609

Skype: live:.cid.66e2522354b1049b

Facebook: https://www.facebook.com/KBYAI
```

## About SDK

### Set up
1. Copy the SDK (libfacesdk folder) to the root folder of your project.

2. Add SDK to the project in settings.gradle
```
include ':libfacesdk'
```

3. Add dependency to your build.gradle
```
implementation project(path: ':libfacesdk')
```

### Initializing an SDK

- Step One

To begin, you need to activate the SDK using the license that you have received.
```
FaceSDK.setActivation("...")
```

If activation is successful, the return value will be SDK_SUCCESS. Otherwise, an error value will be returned.

- Step Two

After activation, call the SDK's initialization function.
```
FaceSDK.init(getAssets());
```
If initialization is successful, the return value will be SDK_SUCCESS. Otherwise, an error value will be returned.

### Face Detection and Liveness Detection

The FaceSDK offers a single function for detecting face and liveness detection, which can be used as follows:
```
FaceSDK.faceDetection(bitmap)
```

This function takes a single parameter, which is a bitmap object. The return value of the function is a list of FaceBox objects. Each FaceBox object contains the detected face rectangle, liveness score, and facial angles such as yaw, roll, and pitch.

### Yuv to Bitmap
The SDK provides a function called yuv2Bitmap, which converts a yuv frame to a bitmap. Since camera frames are typically in yuv format, this function is necessary to convert them to bitmaps. The usage of this function is as follows:
```
Bitmap bitmap = FaceSDK.yuv2Bitmap(nv21, image.getWidth(), image.getHeight(), 7);
```
The first parameter is an nv21 byte array containing the yuv data. 

The second parameter is the width of the yuv frame, and the third parameter is its height. 

The fourth parameter is the conversion mode, which is determined by the camera orientation.

To determine the appropriate conversion mode, the following method can be used:
```
 1        2       3      4         5            6           7          8

 888888  888888      88  88      8888888888  88                  88  8888888888
 88          88      88  88      88  88      88  88          88  88      88  88
 8888      8888    8888  8888    88          8888888888  8888888888          88
 88          88      88  88
 88          88  888888  888888
```
