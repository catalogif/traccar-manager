# A TRACK FLEET App - Complete Deployment Checklist

Use this checklist to track your progress from development to Play Store publication.

## Phase 1: Development Environment Setup

### Install Required Tools
- [ ] Install Flutter SDK 3.7.2+ (https://docs.flutter.dev/get-started/install)
- [ ] Add Flutter to system PATH
- [ ] Run `flutter doctor` and fix any issues
- [ ] Install Android Studio (for Android development)
- [ ] Install Android SDK and command-line tools
- [ ] Install JDK 11 or higher
- [ ] (Optional for iOS) Install Xcode on macOS

### Verify Installation
```bash
flutter --version
flutter doctor -v
```

## Phase 2: Project Setup

### Get the Code
- [ ] Clone the repository
- [ ] Navigate to project directory: `cd traccar-manager`
- [ ] Install dependencies: `flutter pub get`
- [ ] Verify no errors in output

### Verify Rebranding
- [ ] Check app name is "A TRACK FLEET" in Android manifest
- [ ] Check app name is "A TRACK FLEET" in iOS Info.plist
- [ ] Verify server URL is `https://server.atrack.com.pk/` in lib/main_screen.dart
- [ ] Check custom icons are installed in android/app/src/main/res/mipmap-*
- [ ] Check custom icons are installed in ios/Runner/Assets.xcassets/AppIcon.appiconset/

## Phase 3: Testing

### Debug Build
- [ ] Build debug APK: `flutter build apk --debug`
- [ ] Verify APK created at: `build/app/outputs/flutter-apk/app-debug.apk`
- [ ] Transfer APK to Android device
- [ ] Install and test on device
- [ ] Verify app name shows as "A TRACK FLEET"
- [ ] Verify app icon displays correctly
- [ ] Test login to https://server.atrack.com.pk/
- [ ] Verify all core features work
- [ ] Test error screen shows company branding

### Test Checklist
- [ ] App launches successfully
- [ ] App name displays as "A TRACK FLEET"
- [ ] Custom icon shows on home screen
- [ ] Connects to https://server.atrack.com.pk/
- [ ] Login works with test credentials
- [ ] Main features are functional
- [ ] Error screen shows "A TRACK FLEET (SMC-PRIVATE) LIMITED"
- [ ] Error screen shows https://atrack.com.pk
- [ ] No references to "Traccar" visible anywhere
- [ ] Push notifications work (if applicable)

## Phase 4: Release Preparation

### Create Signing Keystore
- [ ] Generate keystore: 
  ```bash
  keytool -genkey -v -keystore ~/atrack-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias atrack
  ```
- [ ] Choose strong passwords (write them down!)
- [ ] Complete certificate information
- [ ] Backup keystore to secure location
- [ ] Create second backup in different location
- [ ] **CRITICAL**: Store passwords securely!

### Configure Signing
- [ ] Create directory: `../../environment/` (relative to project)
- [ ] Create `key.properties` file with:
  ```
  storePassword=<YOUR_KEYSTORE_PASSWORD>
  keyPassword=<YOUR_KEY_PASSWORD>
  keyAlias=atrack
  storeFile=/absolute/path/to/atrack-keystore.jks
  ```
- [ ] Verify paths are correct
- [ ] Test signing configuration

### Build Release
- [ ] Update version in pubspec.yaml if needed
- [ ] Build app bundle: `flutter build appbundle --release`
- [ ] Verify AAB created at: `build/app/outputs/bundle/release/app-release.aab`
- [ ] Check file size (should be ~20-40 MB)
- [ ] Keep a copy of this AAB for your records

## Phase 5: Google Play Console Setup

### Create Account
- [ ] Go to https://play.google.com/console
- [ ] Create Google Play Developer account ($25 one-time fee)
- [ ] Complete account verification
- [ ] Accept Developer Distribution Agreement

### Create App
- [ ] Click "Create app"
- [ ] Enter app details:
  - Name: **A TRACK FLEET**
  - Default language: **English (United States)**
  - App or game: **App**
  - Free or paid: **Free** (or Paid)
- [ ] Declare app details (not for kids, etc.)
- [ ] Click "Create app"

### Configure Store Listing
- [ ] Add app name: **A TRACK FLEET**
- [ ] Add short description (max 80 chars):
  ```
  Fleet management and GPS tracking for A TRACK FLEET customers
  ```
- [ ] Add full description:
  ```
  A TRACK FLEET is a comprehensive fleet management and GPS tracking mobile 
  application by A TRACK FLEET (SMC-PRIVATE) LIMITED. 
  
  Features:
  • Live GPS tracking of all your vehicles
  • Real-time device management
  • Event notifications and alerts
  • Route history and comprehensive reports
  • Secure and reliable tracking
  
  Connect to your A TRACK FLEET account to manage and monitor your fleet 
  from anywhere. This app requires an active A TRACK FLEET account.
  
  For more information, visit https://atrack.com.pk
  ```
- [ ] Upload app icon (512x512 PNG from IconKitchen-Output.zip)
- [ ] Upload screenshots (minimum 2 for phone, 2 for tablet)
- [ ] (Optional) Upload feature graphic (1024x500)
- [ ] Select category: **Business** or **Maps & Navigation**
- [ ] Add contact email
- [ ] Add website: https://atrack.com.pk
- [ ] Add privacy policy URL (you need to provide this)

### Content Settings
- [ ] Complete content rating questionnaire
  - Select "Business or services app"
  - Answer questions honestly
  - Should receive "Everyone" rating
- [ ] Set target audience
- [ ] Complete data safety form
- [ ] Set up news apps if required

### Pricing and Distribution
- [ ] Select countries/regions (at minimum: Pakistan)
- [ ] Confirm it's free (or set price)
- [ ] Accept content guidelines
- [ ] Enable app signing by Google Play (recommended)

## Phase 6: Upload and Release

### Internal Testing (Optional but Recommended)
- [ ] Create internal testing track
- [ ] Upload AAB to internal testing
- [ ] Add test users (your email)
- [ ] Share internal test link
- [ ] Test thoroughly
- [ ] Fix any issues found
- [ ] Build and upload new version if needed

### Production Release
- [ ] Go to "Production" in left menu
- [ ] Click "Create new release"
- [ ] Upload app-release.aab
- [ ] Add release notes:
  ```
  Initial release of A TRACK FLEET mobile app
  
  Features:
  • Live fleet tracking
  • Real-time GPS monitoring
  • Device management
  • Event notifications
  • Route history and reports
  
  Requires an A TRACK FLEET account to use.
  ```
- [ ] Set rollout percentage (start with 20% for safety)
- [ ] Review release
- [ ] Click "Start rollout to Production"

### Wait for Review
- [ ] Submitted for review
- [ ] Review typically takes 1-7 days
- [ ] Monitor email for updates
- [ ] Check Play Console for status

### Post-Approval
- [ ] App approved and published! 🎉
- [ ] Increase rollout to 50%
- [ ] Monitor crash reports and reviews
- [ ] Increase to 100% after 24-48 hours
- [ ] Share Play Store link with customers

## Phase 7: Post-Launch

### Monitor
- [ ] Check Play Console daily for:
  - Crash reports
  - User reviews
  - App statistics
  - Performance metrics
- [ ] Respond to user reviews
- [ ] Track download numbers
- [ ] Monitor ratings

### Marketing
- [ ] Add Play Store badge to website
- [ ] Share link on social media
- [ ] Email existing customers
- [ ] Create user guide/tutorial
- [ ] Provide customer support

### Maintenance
- [ ] Plan regular updates
- [ ] Monitor for security issues
- [ ] Update dependencies periodically
- [ ] Respond to user feedback
- [ ] Add requested features

## Important Reminders

### Security
- ⚠️ **NEVER LOSE YOUR KEYSTORE!** You cannot update the app without it.
- ⚠️ Store keystore in at least 2 secure locations
- ⚠️ Keep passwords in a password manager
- ⚠️ Never commit keystore or passwords to version control

### Version Management
- Increment version for each release
- Format: `major.minor.patch+buildNumber`
- Example: `1.0.0+1`, `1.0.1+2`, `1.1.0+3`
- Update in `pubspec.yaml`

### Testing Before Release
- Always test on real devices
- Test different Android versions
- Test different screen sizes
- Test offline scenarios
- Test with poor network conditions

## Need Help?

### Documentation
- **QUICKSTART.md** - Quick build guide
- **BUILDING.md** - Detailed build instructions
- **REBRANDING_SUMMARY.md** - All changes made
- **README.md** - Project overview

### Support Resources
- Flutter Docs: https://docs.flutter.dev
- Play Console Help: https://support.google.com/googleplay/android-developer
- Android Developer: https://developer.android.com

## Congratulations! 🎉

When you've completed all checkboxes, your app is live on the Play Store!

**Play Store Link Format:**
https://play.google.com/store/apps/details?id=org.traccar.manager

(Note: If you change the package name, the link will be different)

---

**Current Progress:** Track your completion percentage by counting checked boxes!

**Last Updated:** Version 1.0 - Ready for initial release
