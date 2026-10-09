# Esmail-name: Build Noor Salah APK

on:
workflow_dispatch:
push:
branches:
- main

jobs:
build:
runs-on: ubuntu-latest

steps:
  - name: Download project
    uses: actions/checkout@v4

  - name: Install Java
    uses: actions/setup-java@v4
    with:
      distribution: temurin
      java-version: '17'

  - name: Setup Gradle
    uses: gradle/actions/setup-gradle@v4

  - name: Install Android SDK
    uses: android-actions/setup-android@v3

  - name: Install Android packages
    run: sdkmanager "platforms;android-36" "build-tools;36.0.0"

  - name: Build APK
    run: gradle assembleDebug --no-daemon

  - name: Upload APK
    uses: actions/upload-artifact@v4
    with:
      name: Noor-Salah-APK
      path: app/build/outputs/apk/debug/app-debug.apk
تطبيق نور الصلاة لمواقيت الصلاة في منطقة القراية 
