# ADB Uninstall Script

This guide provides step-by-step instructions on how to install ADB (Android Debug Bridge) and remove bloatware from an android device.

## Prerequisites

- ADB (Android Debug Bridge) must be installed and added to your system's PATH. (Download [here](https://developer.android.com/studio/releases/platform-tools).)
- A connected Android device with USB debugging enabled.
- PowerShell (installed by default on Windows).

## Usage

1. Ensure your Android device is connected and ADB is properly set up. 
2. Open PowerShell.
3. Run the following script:
```
Get-Content <path/to/list> | ForEach-Object {
    if ($_ -notmatch '^#') {
        adb shell pm uninstall --user 0 $_
    }
}
```
Note: Removing system apps can potentially cause issues with your device. Make sure that you only remove apps that you are sure you don't need.

## File Structure

The `remove.txt` file should contain the package names of the applications to be uninstalled, each on a new line. Lines starting with `#` are treated as comments and will be ignored by the script.

### Example `remove.txt`

```plaintext
# Social Media Apps
com.example.facebook
com.example.twitter

# Gaming Apps
com.example.game1
com.example.game2
