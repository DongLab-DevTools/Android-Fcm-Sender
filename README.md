# Android-Fcm-Sender

[![Hits](https://myhits.vercel.app/api/hit/https%3A%2F%2Fgithub.com%2FDongLab-DevTools%2FAndroid-Fcm-Sender%3Ftab%3Dreadme-ov-file?color=blue&label=hits&size=small)](https://myhits.vercel.app)
[![Platform](https://img.shields.io/badge/platform-Android-3DDC84?style=flat-square&logo=android)](https://developer.android.com)
[![Min SDK](https://img.shields.io/badge/min%20sdk-24-green?style=flat-square)](https://developer.android.com)
[![Jitpack](https://jitpack.io/v/DongLab-DevTools/Android-Fcm-Sender.svg)](https://jitpack.io/#DongLab-DevTools/Android-Fcm-Sender)

**[한국어 README](./README_ko.md)**

## Overview

Android-Fcm-Sender is a testing library for Firebase Cloud Messaging (FCM) that provides a ready-to-use Activity for sending push notifications directly from your Android device without needing a backend server.

<table>
  <tr>
    <td align="center"><b>Main Screen</b></td>
    <td align="center"><b>No JSON Uploaded</b></td>
    <td align="center"><b>Property Settings</b></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/164afd0c-24d8-4844-b578-472b9e864d4f" width="240"></td>
    <td><img src="https://github.com/user-attachments/assets/26c3e82c-7c24-43e5-af59-c08e98d37ef3" width="240"></td>
    <td><img src="https://github.com/user-attachments/assets/872da42c-231d-4512-b277-e2ccff9fb7e2" width="240"></td>
  </tr>
  <tr>
    <td align="center"><b>Notification Send</b></td>
    <td align="center"><b>Data Send</b></td>
    <td align="center"><b>Delete Data</b></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/735ea9e4-8323-4938-9c5a-081711ea270e" width="240"></td>
    <td><img src="https://github.com/user-attachments/assets/23963942-7706-4584-b4d7-40589d1c4da9" width="240"></td>
    <td><img src="https://github.com/user-attachments/assets/e738fbde-8d34-425e-9f72-4ffeb551911a" width="240"></td>
  </tr>
</table>

<br>
<br>

This library enables quick verification of push notification functionality during development and QA stages. Simply add it to your project and launch the provided Activity to compose and send push messages locally using the FCM HTTP v1 API without needing the Firebase Console or a separate backend server.

<br>

## Features

- **Service Account Key Management**: Upload and manage Firebase Service Account JSON files
- **Notification Field Configuration**: Configure title, body, image, channelId, and other notification properties
- **Data Field Configuration**: Add custom key-value data payloads
- **Priority Settings**: Specify message priority (high/normal) for delivery
- **Real-time Transmission Testing**: Direct FCM API calls with response verification
- **UI-based Operation**: Easy testing with a pre-built Activity interface

<br>

## Installation

### Step 1: Add Jitpack repository

Add the Jitpack repository to your project's `settings.gradle.kts`:

```kotlin
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven { url = uri("https://jitpack.io") }
    }
}
```

### Step 2: Add dependency

Add the library to your module's `build.gradle.kts`:

```kotlin
dependencies {
    implementation("com.github.DongLab-DevTools:Android-Fcm-Sender:latestVersion")
}
```

<br>

### Requirements

- Android API 24 (Android 7.0) or higher
- Firebase project with Cloud Messaging enabled
- Firebase Service Account JSON key file

<br>

## Usage

### Launch FCM Sender Activity

Simply launch the FCM Sender Activity from anywhere in your app:

```kotlin
import android.content.Intent
import com.your.package.FcmSenderActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        // Launch FCM Sender Activity
        findViewById<Button>(R.id.openFcmSender).setOnClickListener {
            val intent = Intent(this, FcmSenderActivity::class.java)
            startActivity(intent)
        }
    }
}
```

### Using the FCM Sender Screen

1. **Obtain Firebase Service Account Key**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Select your project
   - Navigate to **Project Settings → Service Accounts**
   - Click **Generate New Private Key** and download the JSON file

2. **Upload JSON File**
   - Tap the upload button in the FCM Sender Activity
   - Select your Service Account JSON file
   - The app will parse and store the credentials

3. **Configure Message**
   - **Device Token**: Enter the FCM registration token of the target device
   - **Title**: Notification title
   - **Body**: Notification message body
   - **Image URL**: (Optional) Image URL for rich notifications
   - **Channel ID**: Android notification channel ID
   - **Priority**: Select HIGH or NORMAL

4. **Send Message**
   - Tap the **Send** button to transmit via FCM HTTP v1 API
   - View the response status and any errors

<br>

## Tech Stack

| Category | Details |
|----------|---------|
| **Language** | Kotlin |
| **Platform** | Android (minSdk 24) |
| **API** | Firebase Cloud Messaging HTTP v1 |
| **Authentication** | Google Service Account OAuth2 (JWT) |
| **Libraries** | Retrofit2, Gson, OkHttp |

<br>

## Upcoming Features

- **Message History**: Save and resend previous messages
- **Log Viewer**: View success/failure logs for sent messages
- **Template System**: Save frequently used message structures
- **Payload Preview**: JSON formatting and pre-send validation
- **Theme Support**: Dark/Light mode toggle

<br>