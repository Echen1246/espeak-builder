# espeak-builder

GitHub Actions workflow to build `libespeak-ng.so` for Android with the public C API exposed.

## What this builds

- `libespeak-ng.so` for **arm64-v8a** (modern Android phones)
- `libespeak-ng.so` for **armeabi-v7a** (older Android phones)
- `espeak-ng-data/` folder (dictionaries, phoneme data, voices)

## Why?

The official espeak-ng Android APK statically links the library into a JNI wrapper, 
hiding the raw C API. This build creates a standalone shared library with exported 
symbols like `espeak_TextToPhonemes` that can be called directly via Dart FFI.

## Usage

1. Go to the **Actions** tab
2. Click on the latest successful workflow run
3. Download the `espeak-android-build` artifact
4. Extract and use in your Flutter/Android project:
   - Place `.so` files in `android/app/src/main/jniLibs/`
   - Place `espeak-ng-data` in your app's assets

## Build triggers

- Push to main branch
- Manual trigger via `workflow_dispatch`

## License

espeak-ng is licensed under GPL-3.0. See https://github.com/espeak-ng/espeak-ng
