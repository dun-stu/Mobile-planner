# MobilePlanner

A minimal Android app scaffold built with Kotlin + Gradle, targeting SDK 34.

## Project Structure

```
MobilePlanner/
├── app/
│   ├── src/main/
│   │   ├── kotlin/com/mobileplanner/app/
│   │   │   └── MainActivity.kt          # Main activity (blank screen)
│   │   ├── res/
│   │   │   └── values/
│   │   │       └── strings.xml          # App strings
│   │   └── AndroidManifest.xml          # App manifest
│   └── build.gradle.kts                 # App module build configuration
├── gradle/
│   └── wrapper/                         # Gradle wrapper files
├── build.gradle.kts                     # Root build configuration
├── settings.gradle.kts                  # Project settings
├── gradle.properties                    # Gradle properties
├── gradlew                              # Gradle wrapper script (Unix)
├── gradlew.bat                          # Gradle wrapper script (Windows)
├── .gitignore                           # Git ignore file
├── LICENSE                              # MIT License
└── README.md                            # This file
```

## Prerequisites

Before building the app, ensure you have the following installed:

1. **JDK 17 or higher**
   - Download from: https://adoptium.net/
   - Verify installation: `java -version`

2. **Android SDK**
   - Install via Android Studio or command-line tools
   - Required: Android SDK 34 (API level 34)
   - Set `ANDROID_HOME` environment variable to your SDK location

3. **Android SDK Build Tools**
   - Version 34.0.0 or higher
   - Can be installed via SDK Manager in Android Studio

## Building the Debug APK

Follow these steps to build a debug APK:

1. **Clone the repository**
   ```bash
   git clone https://github.com/dun-stu/Mobile-planner.git
   cd Mobile-planner
   ```

2. **Configure Android SDK path** (if not using Android Studio)
   
   Create a `local.properties` file in the project root:
   ```properties
   sdk.dir=/path/to/your/android/sdk
   ```
   
   On macOS/Linux, the default path is usually:
   - `/Users/USERNAME/Library/Android/sdk` (macOS)
   - `/home/USERNAME/Android/Sdk` (Linux)
   
   On Windows:
   - `C:\\Users\\USERNAME\\AppData\\Local\\Android\\Sdk`

3. **Build the debug APK**
   ```bash
   ./gradlew assembleDebug
   ```
   
   On Windows, use:
   ```cmd
   gradlew.bat assembleDebug
   ```

4. **Locate the APK**
   
   After a successful build, the APK will be located at:
   ```
   app/build/outputs/apk/debug/app-debug.apk
   ```

## Installing on a Google Pixel Device

### Method 1: Using ADB (Recommended)

1. **Enable Developer Options on your Pixel**
   - Go to Settings > About phone
   - Tap "Build number" 7 times
   - Go back to Settings > System > Developer options
   - Enable "USB debugging"

2. **Connect your Pixel to your computer**
   - Connect via USB cable
   - Accept the USB debugging prompt on your device

3. **Verify device connection**
   ```bash
   adb devices
   ```
   Your device should appear in the list

4. **Install the APK**
   ```bash
   adb install app/build/outputs/apk/debug/app-debug.apk
   ```
   
   To reinstall (if already installed):
   ```bash
   adb install -r app/build/outputs/apk/debug/app-debug.apk
   ```

5. **Launch the app**
   ```bash
   adb shell am start -n com.mobileplanner.app/.MainActivity
   ```

### Method 2: Manual Installation

1. **Transfer the APK to your device**
   - Email the APK to yourself
   - Or upload to Google Drive/Dropbox and download on device
   - Or use a USB cable and copy to device storage

2. **Enable installation from unknown sources**
   - Go to Settings > Security
   - Enable "Install unknown apps" for the file manager or browser you'll use

3. **Install the APK**
   - Open the file manager on your device
   - Navigate to where you saved the APK
   - Tap the APK file and follow the installation prompts

## Uninstalling

Via ADB:
```bash
adb uninstall com.mobileplanner.app
```

Or manually from device:
- Go to Settings > Apps > MobilePlanner
- Tap "Uninstall"

## Troubleshooting

### Build Issues

- **"SDK location not found"**: Ensure `local.properties` exists with the correct `sdk.dir` path
- **"Failed to resolve dependencies"**: Check your internet connection; Gradle needs to download dependencies
- **"Unsupported class file major version"**: Update to JDK 17 or higher

### Installation Issues

- **"INSTALL_FAILED_UPDATE_INCOMPATIBLE"**: Uninstall the existing app first
- **"device unauthorized"**: Accept the USB debugging prompt on your device
- **"no devices/emulators found"**: Ensure USB debugging is enabled and device is connected

## Development

This is a minimal scaffold with just a blank MainActivity. The app displays a blank screen when launched.

To add features:
1. Modify `MainActivity.kt` to add UI and functionality
2. Add new activities/fragments as needed
3. Update `app/build.gradle.kts` to add dependencies
4. Run `./gradlew assembleDebug` to rebuild

## CI/CD

This project includes a GitHub Actions workflow that automatically builds the APK on every push. The built APK is available as an artifact in the Actions tab.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Note

This scaffold provides the minimal structure needed for an Android app. It includes:
- ✅ Kotlin + Gradle setup
- ✅ Target SDK 34
- ✅ Minimal MainActivity (blank screen)
- ✅ Proper .gitignore for Android/Gradle
- ✅ Build instructions for debug APK
- ✅ Sideloading instructions for Google Pixel
- ✅ MIT License
- ✅ GitHub Actions workflow for CI/CD
