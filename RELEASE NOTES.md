# Release Notes

## D3 Software Version 1.2.1 (March 15, 2021)

Developers
- Fixed a bug with GUI debug mode

## D3 Software Version 1.2.0 (March 15, 2021)

Drivers
- In-Call Sidebar Apps
  - New "Satellite Camera" app shares a person's mobile phone camera with the driver
  - New "On-Screen Text" app lets you type words on the robot screen
  - Share Web Page: added QR code option
  - Developer API to create custom sidebar apps, see more: https://github.com/doublerobotics/d3-sdk
- Detect QR Codes option (with mixed reality graphics)
- New toolbar layout to support sidebar apps
- Moved local video to the left and sidebar to the right

Bug Fixes
- Fixed volume button not showing sometimes
- Brought back fade transition to narrow camera
- Improved frame rate performance with default call settings
- Mixed reality graphics render in narrow camera
- Fixed anonymous viewers list display in Multi-Viewer
- Better error message when a Visitor Pass robot not available

Developers
- In-Call Sidebar Apps:
  - Monitor > Sidebar tab development tool
  - Documentation: https://github.com/doublerobotics/d3-sdk/blob/master/docs/Sidebar%20Apps.md
- QR Code Detector:
  - Enable with camera.tagDetector.enable
  - See options for customizing in Monitor > API > camera
- Fixed ptz in and out API commands
- Merged Monitor > System tab into Dashboard
- New Monitor > API tab replaces Commands and Events
- Monitor > API > Watch Event
- Notifications for RealSense firmware installation
- Monitor fixes on Windows
- Changed Monitor > Terminal to default to double user
- Endpoint option to not retract kickstands at start of call

## D3 Software Version 1.1.2 (February 10, 2021)

Drivers
- New "call connecting" screen
- Show driver's name on connecting screen and if the driver doesn't have a camera
- Fixed bug with calls from iOS disconnecting
- Updated to Electron 9.4.3 and dependencies

Developers
- Notifications in Developer Monitor
- Endpoint option to play call begin and end chimes (coming soon to FM)
- fix DREndpointModule cancelPreheat killing Monitor call

## D3 Software Version 1.1.1 (January 29, 2021)

- Beta test of shiny floor driving improvements - This is disabled by default. If you'd like to test this in your facility, please contact support@doublerobotics.com to schedule a time. We'd like to learn from your environment and tweak the improvements.
- Improved reliability of installing base firmware.
- More automated tests for field calibration to avoid shipping to a repair center.
- Optimized animated standby screen background for lower power usage.
- Updated to Electron 9.4.2 and dependencies.

## D3 Software Version 1.1.0 (January 12, 2021)

For Drivers
- Potentially improved battery life during calls due to improved code performance and other tweaks
- Low bandwidth and resolution options (robot-to-driver bandwidth):
  - Low (1.5 Mbps)
  - Medium (2.5 Mbps)
  - High (4.5 Mbps, default)
  - 1080 (6.5 Mbps)
- Improved touch driver controls:
  - Tap-to-Drive
  - Docking
  - Pinch zoom
  - Two-finger drag to pan and tilt
- On-screen alerts:
  - When the kickstands can't retract due to leaning
  - When WiFi signal is weak
- Fleet Management:
  - After-call redirect URL option for Visitor Pass
- Fixed bugs:
  - Photo rotation
  - A bug where D3 might think that a call is still active, even though the driver got disconnected quickly
  - A bug that could cause kickstands to not deploy after docking
  - A bug that could cause video to not start streaming to the driver for 30+ robots
  - A bug where robots sometimes don't appear on map after ending a call
  - A bug with screen sharing to Double 2
- Web driver client remembers the last camera and mic
- Improved zoom camera overlay
- Zoom camera photo is returned when it's the majority camera in view
- Potentially faster connection times

For Developers
- Performance Model: With the new optimizations, calls start in the lowest performance model (Nvidia's "nvpmodel", plus a few extra tweaks). This limits the CPU, GPU, and other system clocks to low speeds to conserve power. If you need to guarantee higher performance, you should disable this behavior by adding the "PERFORMANCE_MODEL":"highest" entry to your startup.json. The default value is "auto", meaning that the system will change the Performance Model at any time based on the D3 software's internal needs.
- RealSense:
  - new librealsense version 2.41.0 (this will replace any previously installed librealsense)
  - new RealSense firmware version 5.12.10.0 (automatically installs on startup)
  - depth quality score
  - field calibration
  - visual preset options
  - detector for wheel height
  - emitter brightness changes based on the scene lux from the camera
- Scene "lux" value from camera ISP available in DRCamera.frameComplete event
- Endpoint options:
  - hide Visitor Pass button (hideVisitorPassButton)
  - default audio boost level (defaultAudioBoostLevel)
  - minimum Performance Model during calls (minimumPerformanceModel)
- Fleet Rest API: after-call redirect URL option for Visitor Pass
- Monitor UI tweaks and toolbar icons

## D3 Software Version 1.0.32 (November 19, 2020)

For Drivers
- Better support for Captive Portals on WiFi networks
- Improved noise reduction during pole motion (option to disable it in endpoint.setOptions)
- More reliable checking for internet connection

For Developers
- Optional keyboard with Accessory Web View
- Events for significant WiFi signal changes (user interface alerts to come later)
- Small Developer Monitor tweaks
- Updated Electron to 9.3.4 and other dependencies.
- Two new calibration values and a few other remote support tools.

## D3 Software Version 1.0.31 (October 21, 2020)

This update fixes a bug while creating a new connection to a WPA2 Enterprise network.

## D3 Software Version 1.0.28 (October 12, 2020)

WiFi
- More feedback during connecting process
- Better errors for wrong password and failed connection
- Better roaming on some WiFi network types (wpa_supplicant bgscan setting)
- Ability to join open and hidden WiFi network
- Option to disable internet check
- Hidden debug log screen (tap top left corner of screen)

System
- Upgrade to Electron 9.3.2 and other dependencies
- Option to ignore ultrasonic (navigate and endpoint)
- Backup time sync for when NTP doesn't work
- Other small fixes and performance improvements

Fleet Management
- SAML SSO added to Fleet Management recently

## D3 Software Version 1.0.26 (August 10, 2020)

- Multi-Viewer support on D3 and drive.doublerobotics.com
- WiFi onboarding screen:
  - Show MAC address on the wifi screen
  - Connection status bar
  - Better retry after failed scan
  - Reconnect to saved network without password
  - Forget saved network
- Floor depth:
  - When docked forwards, auto-expose for back of base area
  - Z calibration value
- GUI:
  - Protect against multiple accessoryWebViews opening
  - Restart after too many standbyWatchdog
- Endpoint option for default obstacleAvoidanceLevel (1 or 2)
- Fixed lowering pole when docking

## D3 Software Version 1.0.23 (May 18, 2020)

User-facing:
- Support for driving from iOS

Developers:
- camera.hitTest command and DRCamera.hitResult for testing if a point in the frame is either a dock icon or clickable floor
- Lower DRFloorDepth fps to 15
- Better Argus cleanup when disabling camera
- Fixed bug when disabling/enabling camera multiple times rapidly
- Monitor: moved Terminal to separate tab

## D3 Software Version 1.0.22 (May 1, 2020)

- Fixed remote DevTools for GUI/Electron
- camera.setMaxFps: Limit frame rate
- camera.output: Scale output to any resolution or aspect ratio
- camera.output: v4l2 template to /dev/video9 and GUI/Electron
- camera.output: template can be an array for both WebRTC and v4l2 simultaneously
- camera.hitTest: Send click/tap in camera POV to test for a dock icon

Fleet REST API - Brand New!
The Fleet REST API gives you programmatic access to your Fleet's data, such as robots, users, call logs, and visitor passes. You'll need to create a secret API key and include it with all HTTP requests the API endpoints. It's new, so let us know if you spot any problems.
https://admin.doublerobotics.com/api-rest

Double 3 Visitor Pass Sidebar Content
After creating a Visitor Pass for a Double 3, you can add a parameter to the URL that will open content in an iframe next to the video stream. This can be useful to provide visitors with information about where they are visiting.
https://admin.doublerobotics.com/api-sidebar
