# Building A TRACK FLEET Mobile App

This document provides detailed instructions for building and publishing the A TRACK FLEET mobile application.

## Prerequisites

### Required Software

1. **Flutter SDK** (v3.7.2 or higher)
   - Download from: https://docs.flutter.dev/get-started/install
   - Add Flutter to your PATH

2. **For Android Development:**
   - Android Studio or VS Code
   - Android SDK (API level 21 or higher)
   - Java Development Kit (JDK) 11 or higher
   - Gradle (comes with Android Studio)

3. **For iOS Development (macOS only):**
   - Xcode 14 or higher
   - CocoaPods
   - Apple Developer Account (for distribution)

## Initial Setup

### 1. Install Flutter

#### Windows
```bash
# Download Flutter SDK from https://docs.flutter.dev/get-started/install/windows
# Extract to C:\src\flutter
# Add to PATH: C:\src\flutter\bin
```

#### macOS
```bash
cd ~/development
unzip ~/Downloads/flutter_macos_3.x.x-stable.zip
export PATH="$PATH:`pwd`/flutter/bin"
# Add to ~/.zshrc or ~/.bash_profile for persistence
```

#### Linux
```bash
cd ~/development
tar xf ~/Downloads/flutter_linux_3.x.x-stable.tar.xz
export PATH="$PATH:`pwd`/flutter/bin"
# Add to ~/.bashrc for persistence
```

### 2. Verify Installation

```bash
flutter doctor -v
```

This command checks your environment and displays a report. Fix any issues it identifies.

### 3. Clone Repository and Install Dependencies

```bash
git clone <repository-url>
cd traccar-manager
flutter pub get
```

## Building for Android

### Development Build

```bash
# Debug APK
flutter build apk --debug

# The APK will be at: build/app/outputs/flutter-apk/app-debug.apk
```

### Release Build (Unsigned)

```bash
flutter build apk --release
```

### Release Build (Signed for Play Store)

#### Step 1: Create a Keystore

```bash
keytool -genkey -v -keystore ~/atrack-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias atrack
```

You'll be prompted for:
- Keystore password (remember this!)
- Key password (remember this!)
- Your name, organization, etc.

**IMPORTANT:** Store the keystore file and passwords securely! You cannot publish updates without them.

#### Step 2: Create Key Properties File

Create a file at `../../environment/key.properties` (relative to the android folder) with:

```properties
storePassword=YOUR_KEYSTORE_PASSWORD
keyPassword=YOUR_KEY_PASSWORD
keyAlias=atrack
storeFile=/absolute/path/to/atrack-keystore.jks
```

Example:
```properties
storePassword=myStrongPassword123
keyPassword=myStrongPassword123
keyAlias=atrack
storeFile=/Users/username/atrack-keystore.jks
```

#### Step 3: Build Signed App Bundle (Recommended for Play Store)

```bash
flutter build appbundle --release
```

The app bundle will be at: `build/app/outputs/bundle/release/app-release.aab`

#### Step 4: Build Signed APK (Alternative)

```bash
flutter build apk --release
```

The APK will be at: `build/app/outputs/flutter-apk/app-release.apk`

## Building for iOS

### Development Build

```bash
flutter build ios --debug
```

### Release Build

```bash
flutter build ios --release
```

### Creating an Archive for App Store

1. Open the project in Xcode:
   ```bash
   open ios/Runner.xcworkspace
   ```

2. In Xcode:
   - Select "Product" > "Archive"
   - Once archived, the Organizer window opens
   - Select "Distribute App"
   - Choose "App Store Connect"
   - Follow the prompts to upload

## Testing the Build

### Run on Emulator/Simulator

```bash
# List available devices
flutter devices

# Run on specific device
flutter run -d <device-id>
```

### Run on Physical Device

#### Android
1. Enable Developer Options on your Android device
2. Enable USB Debugging
3. Connect via USB
4. Run: `flutter run`

#### iOS
1. Connect iPhone/iPad via USB
2. Trust the computer on the device
3. In Xcode, select your device
4. Run: `flutter run`

### Install APK Manually

```bash
# Using ADB
adb install build/app/outputs/flutter-apk/app-release.apk

# Or copy to device and install
```

## Publishing to Google Play Store

### 1. Prepare App for Release

- Ensure version is updated in `pubspec.yaml`:
  ```yaml
  version: 1.0.0+1  # version_name+version_code
  ```
- Build signed app bundle (see above)

### 2. Create Google Play Console Account

1. Go to https://play.google.com/console
2. Sign up ($25 one-time fee)
3. Complete account verification

### 3. Create App in Console

1. Click "Create app"
2. Fill in app details:
   - **App name:** A TRACK FLEET
   - **Default language:** English (United States)
   - **App or game:** App
   - **Free or paid:** Free (or Paid)
3. Accept declarations and click "Create app"

### 4. Set Up App Details

#### Store Listing
- **App name:** A TRACK FLEET
- **Short description:** Fleet management and GPS tracking system
- **Full description:**
  ```
  A TRACK FLEET is a comprehensive fleet management and GPS tracking mobile application 
  by A TRACK FLEET (SMC-PRIVATE) LIMITED. 
  
  Features:
  - Live GPS tracking
  - Device management
  - Event notifications
  - Route history and reports
  - Secure and reliable
  
  Connect to your A TRACK FLEET account to manage and monitor your fleet from anywhere.
  ```
- **App icon:** Upload 512x512 PNG (from `IconKitchen-Output.zip`)
- **Screenshots:** Required for phone, tablet (minimum 2 each)
- **Feature graphic:** 1024x500 (optional but recommended)

#### App Category
- **Category:** Business or Maps & Navigation
- **Tags:** fleet management, GPS tracking, vehicle tracking

#### Contact Details
- **Email:** Your support email
- **Website:** https://atrack.com.pk
- **Privacy Policy URL:** Your privacy policy URL (required)

### 5. Content Rating

1. Go to "Content rating"
2. Fill out the questionnaire
3. App should be rated for Everyone

### 6. Select Countries/Regions

1. Go to "Countries/regions"
2. Select countries where you want to distribute
3. For Pakistan and your target markets

### 7. Upload App Bundle

1. Go to "Production" → "Releases"
2. Click "Create new release"
3. Upload `app-release.aab`
4. Add release notes:
   ```
   Initial release of A TRACK FLEET
   - Fleet management
   - Real-time GPS tracking
   - Device monitoring
   - Reports and analytics
   ```
5. Save and review

### 8. Complete All Required Sections

Ensure these are complete (green checkmarks):
- Store listing
- Store settings
- App content (Content rating, Target audience, etc.)
- Pricing and distribution
- Release

### 9. Submit for Review

1. Click "Send for review"
2. Review can take 1-7 days
3. You'll receive email updates on status

### 10. After Approval

- App will be published automatically (or based on your settings)
- Monitor reviews and analytics in Play Console
- Respond to user reviews

## Publishing to Apple App Store

### 1. Apple Developer Account

1. Enroll at https://developer.apple.com ($99/year)
2. Complete enrollment and verification

### 2. Configure App in App Store Connect

1. Go to https://appstoreconnect.apple.com
2. Click "My Apps" → "+" → "New App"
3. Fill in:
   - **Platform:** iOS
   - **Name:** A TRACK FLEET
   - **Primary Language:** English (U.S.)
   - **Bundle ID:** org.traccar.manager (or your custom ID)
   - **SKU:** A unique identifier

### 3. Upload Build

1. Build and archive in Xcode (see above)
2. Upload via Xcode Organizer or Transporter app
3. Build appears in App Store Connect after processing (10-30 min)

### 4. Complete App Information

Similar to Google Play:
- App description
- Keywords
- Screenshots (required for all device sizes)
- App icon
- Privacy policy
- Support URL

### 5. Submit for Review

1. Select the uploaded build
2. Fill in all required information
3. Submit for review
4. Review typically takes 24-48 hours

## Updating the App

### Version Numbers

In `pubspec.yaml`, update:
```yaml
version: 1.0.1+2  # Increment version name and code
```

### Build and Upload

1. Build new signed app bundle/archive
2. Upload to respective store
3. Add release notes describing changes
4. Submit for review

## Troubleshooting

### Common Issues

1. **Build fails - dependencies**
   ```bash
   flutter clean
   flutter pub get
   ```

2. **Android signing issues**
   - Verify key.properties path is correct
   - Ensure keystore file exists
   - Check passwords are correct

3. **iOS code signing**
   - Ensure certificates are valid in Xcode
   - Check provisioning profiles
   - Trust developer account on device

4. **Play Store rejection**
   - Read rejection reason carefully
   - Common: Missing privacy policy, inappropriate content rating
   - Fix issues and resubmit

### Getting Help

- Flutter documentation: https://docs.flutter.dev
- Play Console help: https://support.google.com/googleplay/android-developer
- App Store Connect help: https://developer.apple.com/support/app-store-connect/

## Security Notes

1. **Never commit keystore files or passwords to version control**
2. **Keep backups of your keystore in a secure location**
3. **Use strong passwords for keystores**
4. **Keep Firebase configuration files secure**
5. **Regularly update dependencies for security patches**

## Additional Resources

- Flutter Build Documentation: https://docs.flutter.dev/deployment
- Android App Bundle: https://developer.android.com/guide/app-bundle
- iOS Distribution: https://developer.apple.com/ios/submit/
