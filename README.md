# 👁️ AI Vision Assistant for Blind Users

### An AI-Powered Android Application for Visually Impaired People

## 📌 Project Overview

AI Vision Assistant is an Android-based assistive application designed to help blind and visually impaired individuals understand their surroundings using Artificial Intelligence (AI), Computer Vision, and Voice Assistance.

The application allows users to capture images using their smartphone camera or select images from their gallery. It processes visual information using Google ML Kit and provides accessible information through text and audio feedback.

## 🎯 Objectives

- Help visually impaired users understand visual information.
- Identify objects and concepts present in images.
- Extract readable text from images.
- Translate image labels from English into Hindi.
- Convert displayed information into speech.
- Improve accessibility through AI-powered assistance.

## ✨ Features

### 1. Camera Capture
- Capture images using the smartphone camera.
- Save captured images to the device.
- Process captured images for further analysis.

### 2. Gallery Image Selection
- Select existing images from the device gallery.
- Use selected images for OCR and image labeling.

### 3. Text Recognition (OCR)
- Uses Google ML Kit Text Recognition.
- Extracts text from captured or selected images.
- Displays recognized text on the screen.

### 4. AI-Based Image Description
- Uses Google ML Kit Image Labeling.
- Identifies objects and concepts in images.
- Filters detected labels based on confidence scores.
- Translates English labels into Hindi using ML Kit Translation.
- Displays English labels and Hindi descriptions.

### 5. Text-to-Speech
- Uses Android's built-in TextToSpeech API.
- Converts displayed information into audio.
- Allows users to listen to recognized text and descriptions.

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Java | Android application development |
| Android Studio | Development environment |
| XML | User interface design |
| Google ML Kit OCR | Text recognition |
| Google ML Kit Image Labeling | Image and object identification |
| Google ML Kit Translation | English-to-Hindi translation |
| Android TextToSpeech | Audio output |
| Android Activity Result APIs | Camera and gallery integration |
| Gradle Kotlin DSL | Build configuration |

## ⚙️ Application Workflow

```text
                Start Application
                       |
             ---------------------
             |                   |
        Capture Image       Choose Image
             |                   |
             --------+----------
                     |
               Selected Image
                     |
           -----------------------
           |                     |
        Read Text          Describe Image
           |                     |
       ML Kit OCR         Image Labeling
           |                     |
      Extract Text        Filter Labels
           |                     |
      Display Text       English-to-Hindi
                          Translation
           |                     |
           --------+-------------
                    |
              Listen to Result
                    |
            Android TextToSpeech
```

## 📂 Project Structure

```text
Demo_App-main/
│
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
│       │
│       ├── androidTest/
│       └── test/
│
├── gradle/
│   ├── libs.versions.toml
│   └── wrapper/
│
├── build.gradle.kts
├── gradle.properties
├── settings.gradle.kts
├── gradlew
├── gradlew.bat
└── LICENSE
```

## 🚀 Getting Started

### Prerequisites

- Android Studio
- Android SDK Platform 37
- Android device or emulator (Android 7.0 or above)
- Internet connection for downloading the Hindi translation model
- Device camera for image capture

### Installation

**1. Clone the repository**

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

**2. Open the project**

- Open Android Studio.
- Select Open Project.
- Choose the cloned project directory.
- Allow Gradle synchronization to complete.

**3. Run the application**

- Connect an Android device or start an emulator.
- Enable USB debugging if using a physical device.
- Click the Run button in Android Studio.

## 📦 Main Dependencies

```kotlin
implementation("com.google.mlkit:text-recognition:16.0.1")

implementation("com.google.mlkit:image-labeling:17.0.9")

implementation("com.google.mlkit:translate:17.0.3")
```

The application also uses AndroidX Activity, AppCompat, Material Components, and Android's native TextToSpeech API.

## 🔍 Implementation Details

- OCR uses Google ML Kit's default Latin text recognizer.
- Image labels are filtered using a minimum confidence threshold of `0.40`.
- Image labels are translated from English to Hindi.
- TextToSpeech currently uses the US English locale.
- The Hindi translation model is downloaded when required.

**Note:** The current implementation processes individual captured or selected images. Real-time object detection, obstacle avoidance, navigation assistance, and voice-command control are not yet implemented.

## 🔮 Future Enhancements

- Real-time object detection.
- Voice-based commands for hands-free operation.
- Hindi Text-to-Speech support.
- Obstacle detection and warning alerts.
- Currency recognition.
- Multilingual assistance.
- Improved scene understanding.
- Offline AI processing.
- Accessible navigation with TalkBack support.

## 🌍 Real-World Impact

AI Vision Assistant aims to make everyday visual information more accessible to blind and visually impaired individuals.

By integrating Artificial Intelligence, Computer Vision, OCR, image labeling, translation, and speech technologies, this project explores how smartphones can become useful assistive tools for improving accessibility and independence.

## 👩‍💻 Developer

Developed as an Android-based AI accessibility project.

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

**AI Vision Assistant – Making the World More Accessible Through Artificial Intelligence.**
