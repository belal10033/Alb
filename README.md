name: Build TachiyomiJ2K APK

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3

    - uses: actions/setup-java@v3
      with:
        distribution: temurin
        java-version: 17

    - run: chmod +x ./gradlew

    - run: ./gradlew assembleDebug

    - uses: actions/upload-artifact@v3
      with:
        name: tachiyomiJ2K-debug-apk
        path: app/build/outputs/apk/debug/app-debug.apk
