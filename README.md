# OWASP DIVA on Modern Android Studio (2026 Fix Guide)

This repository provides a fully working build of OWASP DIVA on modern Android Studio, including fixes for AndroidX migration, Gradle compatibility, and emulator configuration.

## Overview
OWASP DIVA (Damn Insecure and Vulnerable App) is an intentionally vulnerable Android application used for learning mobile penetration testing and reverse engineering.

The original project is very old and does not build on modern Android Studio. This project fixes those issues and documents the full build process.

---

## Environment

| Component | Version |
|----------|--------|
| Android Studio | 2024+ |
| Gradle | 8.x |
| Android Gradle Plugin | 8.x |
| Java | 17 |
| Emulator | Pixel 3 |
| Android Version | API 28 |

API 28 emulator is recommended for compatibility.

---

## Fixes Applied

### 1. AndroidX Migration
Replaced old support libraries:
- android.support.v7 → androidx.appcompat
- android.support.design → com.google.android.material

### 2. Layout Fix
Replaced:
- android.support.design.widget.CoordinatorLayout → androidx.coordinatorlayout.widget.CoordinatorLayout
- android.support.design.widget.AppBarLayout → com.google.android.material.appbar.AppBarLayout

### 3. Added Dependencies

Add to app/build.gradle:

```
implementation 'androidx.coordinatorlayout:coordinatorlayout:1.2.0'
implementation 'androidx.appcompat:appcompat:1.6.1'
implementation 'com.google.android.material:material:1.11.0'
```

### 4. Android 12 Exported Fix
Added:
```
android:exported="true"
```
to activities with intent filters.

### 5. Removed Old Tests
Deleted deprecated androidTest folder.

---

## Build APK

Build → Rebuild Project

APK location:
```
app/build/outputs/apk/debug/app-debug.apk
```

---

## Run Emulator

Create emulator:
- Pixel 3
- Android 9 (API 28)

Install APK:
```
adb install -r app-debug.apk
```

---


## Credits
Original OWASP DIVA:
https://github.com/payatu/diva-android
