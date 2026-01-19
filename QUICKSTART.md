# Quick Start Guide - Building A TRACK FLEET App

This is a simplified quick start guide. For complete details, see `BUILDING.md`.

## 🚀 Quick Build Instructions

### Prerequisites
1. Install Flutter SDK 3.7.2 or higher from https://docs.flutter.dev/get-started/install
2. Install Android Studio (for Android builds)
3. Install Xcode (for iOS builds, macOS only)

### Build Steps

#### 1. Setup
```bash
cd traccar-manager
flutter pub get
```

#### 2. Build Debug APK (for testing)
```bash
flutter build apk --debug
```
Output: `build/app/outputs/flutter-apk/app-debug.apk`

#### 3. Build Release (for Play Store)

**First time only** - Create keystore:
```bash
keytool -genkey -v -keystore ~/atrack-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias atrack
```

Create `../../environment/key.properties`:
```
storePassword=YOUR_PASSWORD
keyPassword=YOUR_PASSWORD
keyAlias=atrack
storeFile=/absolute/path/to/atrack-keystore.jks
```

**Build app bundle**:
```bash
flutter build appbundle --release
```
Output: `build/app/outputs/bundle/release/app-release.aab`

## 📱 Play Store Publishing

### One-time Setup
1. Create Google Play Developer account: https://play.google.com/console ($25 fee)
2. Create new app
3. Fill in app details:
   - **Name**: A TRACK FLEET
   - **Category**: Business
   - **Icon**: Use 512x512 from `IconKitchen-Output.zip`

### Upload Release
1. Go to Production → Create new release
2. Upload `app-release.aab`
3. Add release notes
4. Submit for review
5. Wait 1-7 days for approval

## ✅ What Was Changed

- ✅ App name: "A TRACK FLEET"
- ✅ Server URL: Hardcoded to https://server.atrack.com.pk/
- ✅ Custom icons: Installed from IconKitchen-Output.zip
- ✅ Company branding: A TRACK FLEET (SMC-PRIVATE) LIMITED
- ✅ Website: https://atrack.com.pk

## ⚠️ Important Notes

1. **Server is hardcoded** - Users can ONLY connect to https://server.atrack.com.pk/
2. **Keep keystore safe** - You cannot update the app without it!
3. **Package name** - Currently `org.traccar.manager` (consider changing for new app)

## 📚 Documentation

- **BUILDING.md** - Complete build and publishing guide
- **REBRANDING_SUMMARY.md** - All changes made during rebranding
- **README.md** - Project overview

## 🆘 Need Help?

Common issues:
- **Flutter not found**: Add Flutter to your PATH
- **Build fails**: Run `flutter clean && flutter pub get`
- **Signing errors**: Check `key.properties` paths and passwords

For detailed troubleshooting, see `BUILDING.md`.

## 🎯 Next Steps

1. Test the debug build on your device
2. Create release keystore (keep it safe!)
3. Build release version
4. Create Play Store listing
5. Upload and submit for review
6. Wait for approval
7. Your app goes live! 🎉

---

**Ready to build?** Start with: `flutter pub get` then `flutter build apk --debug`
