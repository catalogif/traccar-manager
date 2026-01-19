# A TRACK FLEET - Fleet Management System

## Overview

A TRACK FLEET is a comprehensive fleet management and GPS tracking mobile application by A TRACK FLEET (SMC-PRIVATE) LIMITED. This app connects exclusively to the A TRACK FLEET server to provide real-time tracking and management of your fleet.

- **Live Tracking**: View the real-time location of all your devices on an interactive map.
- **Device Management**: Add, edit, or remove devices directly from your mobile device.
- **Event Notifications**: Receive alerts for geofence crossings, device status changes, and more.
- **History and Reports**: Review past routes and generate trip history for any device.
- **Secure and Private**: All your data stays on our secure server.

## Company Information

**A TRACK FLEET (SMC-PRIVATE) LIMITED**
- Website: https://atrack.com.pk
- Server: https://server.atrack.com.pk/

## Building the App

### Prerequisites
- Flutter SDK (3.7.2 or higher)
- Android Studio or VS Code with Flutter extensions
- For Android: Android SDK, Java 11+
- For iOS: Xcode (macOS only)

### Setup Instructions

1. **Install Flutter**
   ```bash
   # Follow official Flutter installation guide
   # https://docs.flutter.dev/get-started/install
   ```

2. **Clone and Setup**
   ```bash
   git clone <repository-url>
   cd traccar-manager
   flutter pub get
   ```

3. **Build for Android**
   ```bash
   # Debug build
   flutter build apk --debug
   
   # Release build (requires signing configuration)
   flutter build apk --release
   
   # App Bundle for Play Store
   flutter build appbundle --release
   ```

4. **Build for iOS** (macOS only)
   ```bash
   # Debug build
   flutter build ios --debug
   
   # Release build
   flutter build ios --release
   ```

### Signing Configuration (Android)

For release builds, create a `key.properties` file at `../../environment/key.properties` with:
```
storePassword=<your-keystore-password>
keyPassword=<your-key-password>
keyAlias=<your-key-alias>
storeFile=<path-to-keystore-file>
```

Generate a keystore:
```bash
keytool -genkey -v -keystore ~/atrack-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias atrack
```

## Publishing to Google Play Store

1. **Prepare Release Build**
   - Ensure signing is configured (see above)
   - Build app bundle: `flutter build appbundle --release`
   - Output will be at: `build/app/outputs/bundle/release/app-release.aab`

2. **Google Play Console Setup**
   - Go to https://play.google.com/console
   - Create a new app or select existing app
   - Fill in app details:
     - App name: A TRACK FLEET
     - Description: Fleet management and GPS tracking system
     - Category: Business / Productivity
   - Upload screenshots and promotional graphics

3. **Upload App Bundle**
   - Go to Production → Create new release
   - Upload the `app-release.aab` file
   - Add release notes
   - Review and rollout

4. **Content Rating**
   - Complete the content rating questionnaire
   - App is suitable for all ages

5. **Privacy Policy**
   - Ensure you have a privacy policy URL
   - Add it in the app details

6. **Review and Publish**
   - Complete all required sections
   - Submit for review
   - Wait for Google's approval (typically 1-7 days)

## Testing

Run tests:
```bash
flutter test
```

Run the app in debug mode:
```bash
flutter run
```

## License

    Apache License, Version 2.0

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
