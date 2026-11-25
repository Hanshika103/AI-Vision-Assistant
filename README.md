from pathlib import Path
readme = r'''# AI Vision Assistant for Blind Users

An Android application that helps users access visual information from images through **text recognition, image labeling, Hindi translation, and text-to-speech**.

The app allows a user to capture a photo with the device camera or choose an existing image from the gallery. It can then extract visible text or identify image labels and present the results on screen. The displayed information can be spoken aloud using Android Text-to-Speech.

> **Current scope:** This README describes the functionality present in the uploaded source code. The current implementation processes a selected or captured image; it does not provide continuous real-time scene detection, obstacle avoidance, navigation, or voice-command control.

## Features

### 1. Capture an image
- Opens the device camera using Android's `TakePicture` activity-result contract.
- Saves the captured image in the device's Pictures collection.
- Uses the captured image as the input for text recognition or image description.

### 2. Choose an image
- Opens the Android image picker.
- Allows the user to select an existing image.
- Uses the selected image for OCR or image labeling.

### 3. Read text from an image (OCR)
- Uses **Google ML Kit Text Recognition** with the default Latin recognizer.
- Extracts text detected in the selected or captured image.
- Displays the recognized text in the app.
- Shows a helpful message when no text is detected or processing fails.

### 4. Describe an image
- Uses **Google ML Kit Image Labeling** to identify recognizable content in an image.
- Keeps labels with a confidence score of at least `0.40`.
- Uses **Google ML Kit Translation** to translate the detected English labels into Hindi.
- Displays the English labels and a simple Hindi description.

### 5. Listen to the displayed result
- Uses Android's built-in **TextToSpeech** API.
- Speaks the text currently displayed in the status/result area.
- Uses the device's US English TTS locale in the current implementation.

## Technology Stack

| Technology | Usage |
|---|---|
| Java | Android application logic |
| Android Studio | Android development environment |
| XML | Screen layout |
| Google ML Kit Text Recognition | Extract text from images |
| Google ML Kit Image Labeling | Identify objects and concepts in images |
| Google ML Kit Translation | Translate image labels from English to Hindi |
| Android TextToSpeech | Read displayed text aloud |
| Android Activity Result APIs | Camera capture and image selection |
| Gradle Kotlin DSL | Build configuration |

## Application Workflow

```text
                 Start Application
                         |
             -------------------------
             |                       |
        Capture Image           Choose Image
             |                       |
             -----------+-------------
                        |
                 Selected Image
                        |
             -----------------------
             |                     |
          Read Text           Describe Image
             |                     |
       ML Kit OCR          ML Kit Image Labeling
             |                     |
       Extract Text        Filter Labels (>= 0.40)
             |                     |
       Display Text        English-to-Hindi Translation
             |                     |
             |              Display Description
             |                     |
             -----------+-----------
                        |
                Listen to Result
                        |
               Android TextToSpeech
```

## Project Structure

```text
Demo_App-main/
├── app/
│   ├── build.gradle.kts
│   └── src/
│       ├── main/
│       │   ├── AndroidManifest.xml
│       │   ├── java/com/example/demo/
│       │   │   └── MainActivity.java
│       │   └── res/
│       │       ├── layout/
│       │       │   └── activity_main.xml
│       │       ├── drawable/
│       │       ├── mipmap-*/
│       │       └── values/
│       ├── androidTest/
│       └── test/
├── gradle/
│   ├── libs.versions.toml
│   └── wrapper/
├── build.gradle.kts
├── gradle.properties
├── settings.gradle.kts
├── gradlew
├── gradlew.bat
└── LICENSE
```

## User Interface

The main screen provides five actions:

| Button | Function |
|---|---|
| Capture Image | Take a new photo using the camera |
| Choose Image | Select an image from the gallery |
| Read Text | Extract and display text from the selected image |
| Listen to Text | Speak the text currently displayed |
| Describe Image | Detect image labels, translate them into Hindi, and display a description |

## Requirements

- Android Studio with support for the project's Android Gradle Plugin.
- Android SDK Platform 37 as configured in the project.
- Android device or emulator running Android 7.0 (API 24) or later.
- Internet access when ML Kit needs to download the Hindi translation model.
- A device with a working camera for the capture feature.
- A supported Android Text-to-Speech engine for audio output.

## Getting Started

### 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

### 2. Open the project

1. Open Android Studio.
2. Select **Open**.
3. Choose the cloned `Demo_App-main` project folder.
4. Allow Gradle to sync and download the required dependencies.

### 3. Run the application

1. Connect an Android device with USB debugging enabled, or start an emulator.
2. Select the device in Android Studio.
3. Click **Run**.

### 4. Try the features

1. Tap **Capture Image** or **Choose Image**.
2. To extract printed text, tap **Read Text**.
3. To identify image content and view the Hindi description, tap **Describe Image**.
4. Tap **Listen to Text** to hear the text currently shown on the screen.

## Gradle Dependencies

The app's `app/build.gradle.kts` includes these main ML Kit dependencies:

```kotlin
implementation("com.google.mlkit:text-recognition:16.0.1")
implementation("com.google.mlkit:image-labeling:17.0.9")
implementation("com.google.mlkit:translate:17.0.3")
```

It also uses AndroidX Activity, AppCompat, Material Components, and the Android platform TextToSpeech API. See `app/build.gradle.kts` and `gradle/libs.versions.toml` for the complete build configuration.

## Important Implementation Notes

- The OCR recognizer is configured with `TextRecognizerOptions.DEFAULT_OPTIONS`, which is the Latin text recognizer.
- Image labels are included only when their confidence is at least `0.40`.
- The translation client is configured for English-to-Hindi translation. The Hindi model is downloaded when the image-description feature is used.
- The current Text-to-Speech setup selects `Locale.US`; the spoken language may therefore not match the Hindi description. A Hindi TTS locale can be configured separately if supported by the device.
- The app currently uses a standard button-based interface. Dedicated voice-command input and continuous hands-free interaction are not implemented in the uploaded code.
- Image labeling provides labels for an image; it is not a real-time object tracking or obstacle-detection system.

## Future Improvements

Potential next steps for the project include:

- Hindi Text-to-Speech output and language selection.
- Voice commands for hands-free operation.
- More accessible navigation and TalkBack testing.
- Continuous camera-based object detection.
- Distance estimation and obstacle alerts, with suitable sensing and safety testing.
- Improved scene descriptions and support for additional languages.
- Clearer spoken feedback for errors and processing states.

These are planned enhancements, not features claimed to be implemented in the current version.

## Testing

The repository contains Android unit-test and instrumented-test source sets. The current sample test files are Android Studio templates; feature-specific automated tests should be added for OCR, image labeling, translation, and speech behavior.

## License

This project is distributed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

---

**AI Vision Assistant** — making image-based information more accessible through Android and on-device machine learning.
'''
path = Path("/mnt/data/README.md")
path.write_text(readme, encoding="utf-8")
print(f"Created {path} ({path.stat().st_size} bytes)")
