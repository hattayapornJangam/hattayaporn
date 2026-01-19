name: Flutter CI/CD

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      # 1. ดึงโค้ดจาก repo
      - name: Checkout source code
        uses: actions/checkout@v4

      # 2. ติดตั้ง Flutter
      - name: Setup Flutter
        uses: subosito/flutter-action@v2
        with:
          flutter-version: '3.19.0'
          channel: 'stable'

      # 3. ติดตั้ง dependencies
      - name: Install dependencies
        run: flutter pub get

      # 4. ตรวจรูปแบบโค้ด Dart
      - name: Verify formatting
        run: dart format --output=none --set-exit-if-changed .

      # 5. วิเคราะห์โค้ด (error / warning)
      - name: Analyze project
        run: flutter analyze

      # 6. รัน test
      - name: Run tests
        run: flutter test

      # 7. Build APK (Android)
      - name: Build APK
        run: flutter build apk --release
