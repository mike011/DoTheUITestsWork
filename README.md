# DoTheUITestsWork

This repo was created to log a bug against ios-snapshot-test-case. The issue logged is that some supporting library aren't being loaded when trying to run the tests after setting up Cocoapods. Here is a link to the issue: https://github.com/uber/ios-snapshot-test-case/issues/55

Environment:
- Mojave with Xcode 10
- Snapshot 2.2.0

Example Workspace:
https://github.com/mike011/DoTheUITestsWork/tree/master/DoTheUITestsWork

Steps:
1. Create Project
2. From terminal run: **pod init**
3. In the pod spec add: **pod 'iOSSnapshotTestCase'**
4. From terminal run **pod install**
4. Open newly created workspace
5. Run tests.

The tests do not run and following error output is reproduced. 
```
2018-10-15 20:58:13.473893-0400 DoTheUITestsWork[31059:673798] Failed to load test bundle from file:///Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator/DoTheUITestsWork.app/PlugIns/DoTheUITestsWorkTests.xctest/: Error Domain=NSCocoaErrorDomain Code=3587 "dlopen_preflight(/Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator/DoTheUITestsWork.app/PlugIns/DoTheUITestsWorkTests.xctest/DoTheUITestsWorkTests): Library not loaded: @rpath/libswiftSwiftOnoneSupport.dylib
  Referenced from: /Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator/DoTheUITestsWork.app/PlugIns/DoTheUITestsWorkTests.xctest/Frameworks/FBSnapshotTestCase.framework/FBSnapshotTestCase
  Reason: image not found" UserInfo={NSLocalizedFailureReason=The bundle is damaged or missing necessary resources., NSLocalizedRecoverySuggestion=Try reinstalling the bundle., NSFilePath=/Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator/DoTheUITestsWork.app/PlugIns/DoTheUITestsWorkTests.xctest/DoTheUITestsWorkTests, NSDebugDescription=dlopen_preflight(/Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator/DoTheUITestsWork.app/PlugIns/DoTheUITestsWorkTests.xctest/DoTheUITestsWorkTests): Library not loaded: @rpath/libswiftSwiftOnoneSupport.dylib
  Referenced from: /Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator/DoTheUITestsWork.app/PlugIns/DoTheUITestsWorkTests.xctest/Frameworks/FBSnapshotTestCase.framework/FBSnapshotTestCase
  Reason: image not found, NSBundlePath=/Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator/DoTheUITestsWork.app/PlugIns/DoTheUITestsWorkTests.xctest, NSLocalizedDescription=The bundle “DoTheUITestsWorkTests” couldn’t be loaded because it is damaged or missing necessary resources.}
2018-10-15 20:58:13.475911-0400 DoTheUITestsWork[31059:673798] libXCTestBundleInject Arguments:
2018-10-15 20:58:13.476085-0400 DoTheUITestsWork[31059:673798]   /Users/michael/Library/Developer/CoreSimulator/Devices/851B3429-9701-4780-AEAF-B06284218EBC/data/Containers/Bundle/Application/B9C15E25-215C-47E7-9007-A9367BD66802/DoTheUITestsWork.app/DoTheUITestsWork
2018-10-15 20:58:13.476173-0400 DoTheUITestsWork[31059:673798]   -NSTreatUnknownArgumentsAsOpen
2018-10-15 20:58:13.476271-0400 DoTheUITestsWork[31059:673798]   NO
2018-10-15 20:58:13.476358-0400 DoTheUITestsWork[31059:673798]   -ApplePersistenceIgnoreState
2018-10-15 20:58:13.476443-0400 DoTheUITestsWork[31059:673798]   YES
2018-10-15 20:58:13.476528-0400 DoTheUITestsWork[31059:673798] libXCTestBundleInject Environment:
2018-10-15 20:58:13.476730-0400 DoTheUITestsWork[31059:673798]   CFFIXED_USER_HOME = /Users/michael/Library/Developer/CoreSimulator/Devices/851B3429-9701-4780-AEAF-B06284218EBC/data/Containers/Data/Application/254341CA-44A7-4130-B908-EBFAC65E26DE
2018-10-15 20:58:13.490029-0400 DoTheUITestsWork[31059:673798]   OS_ACTIVITY_DT_MODE = YES
2018-10-15 20:58:13.490153-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_RUNTIME_VERSION = 12.0
2018-10-15 20:58:13.490237-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_AUDIO_DEVICES_PLIST_PATH = /Users/michael/Library/Developer/CoreSimulator/Devices/851B3429-9701-4780-AEAF-B06284218EBC/data/var/run/com.apple.coresimulator.audio.plist
2018-10-15 20:58:13.490315-0400 DoTheUITestsWork[31059:673798]   __XPC_DYLD_FRAMEWORK_PATH = /Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator
2018-10-15 20:58:13.490393-0400 DoTheUITestsWork[31059:673798]   CUPS_SERVER = /private/tmp/com.apple.launchd.aOPYFesDFz/Listeners
2018-10-15 20:58:13.490467-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_VERSION_INFO = CoreSimulator 572.2 - Device: iPhone XR - Runtime: iOS 12.0 (16A366) - DeviceType: iPhone XR
2018-10-15 20:58:13.490540-0400 DoTheUITestsWork[31059:673798]   DYLD_FALLBACK_LIBRARY_PATH = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/usr/lib
2018-10-15 20:58:13.490728-0400 DoTheUITestsWork[31059:673798]   DYLD_FALLBACK_FRAMEWORK_PATH = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/System/Library/Frameworks
2018-10-15 20:58:13.491062-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_DEVICE_NAME = iPhone XR
2018-10-15 20:58:13.491360-0400 DoTheUITestsWork[31059:673798]   __XCODE_BUILT_PRODUCTS_DIR_PATHS = /Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator
2018-10-15 20:58:13.491674-0400 DoTheUITestsWork[31059:673798]   IPHONE_TVOUT_EXTENDED_PROPERTIES = /Users/michael/Library/Developer/CoreSimulator/Devices/851B3429-9701-4780-AEAF-B06284218EBC/data/Library/Application Support/Simulator/extended_display.plist
2018-10-15 20:58:13.491975-0400 DoTheUITestsWork[31059:673798]   DYLD_ROOT_PATH = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot
2018-10-15 20:58:13.492279-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_BOOT_TIME = 1539650743
2018-10-15 20:58:13.492549-0400 DoTheUITestsWork[31059:673798]   XCTestConfigurationFilePath = /Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Logs/Test/Test-DoTheUITestsWork-2018.10.15_20-58-01--0400.xcresult/1_Test/Diagnostics/DoTheUITestsWorkTests-30D1D9E2-F701-46FD-8170-9CED601C7532/DoTheUITestsWorkTests-05EE2269-72B8-47D3-901E-394E689F6A9C/LaunchSessions/08D5EB67-F746-4188-8894-C22D9041952C/remote-container/tmp/DoTheUITestsWorkTests-08D5EB67-F746-4188-8894-C22D9041952C.xctestconfiguration
2018-10-15 20:58:13.492884-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_EXTENDED_DISPLAY_PROPERTIES = /Users/michael/Library/Developer/CoreSimulator/Devices/851B3429-9701-4780-AEAF-B06284218EBC/data/Library/Application Support/Simulator/extended_display.plist
2018-10-15 20:58:13.493240-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_RUNTIME_BUILD_VERSION = 16A366
2018-10-15 20:58:13.493562-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_MAINSCREEN_SCALE = 2.000000
2018-10-15 20:58:13.493896-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_PRODUCT_CLASS = N84
2018-10-15 20:58:13.494235-0400 DoTheUITestsWork[31059:673798]   HOME = /Users/michael/Library/Developer/CoreSimulator/Devices/851B3429-9701-4780-AEAF-B06284218EBC/data/Containers/Data/Application/254341CA-44A7-4130-B908-EBFAC65E26DE
2018-10-15 20:58:13.494599-0400 DoTheUITestsWork[31059:673798]   CA_ASSERT_MAIN_THREAD_TRANSACTIONS = 0
2018-10-15 20:58:13.494872-0400 DoTheUITestsWork[31059:673798]   NSUnbufferedIO = YES
2018-10-15 20:58:13.495297-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_LEGACY_ASSET_SUFFIX = iphone
2018-10-15 20:58:13.495651-0400 DoTheUITestsWork[31059:673798]   TESTMANAGERD_SIM_SOCK = /private/tmp/com.apple.launchd.vJxpSH9mtd/com.apple.testmanagerd.unix-domain.socket
2018-10-15 20:58:13.495989-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_MEMORY_WARNINGS = /Users/michael/Library/Developer/CoreSimulator/Devices/851B3429-9701-4780-AEAF-B06284218EBC/data/var/run/memory_warning_simulation
2018-10-15 20:58:13.496333-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_MAINSCREEN_PITCH = 326.000000
2018-10-15 20:58:13.496884-0400 DoTheUITestsWork[31059:673798]   XPC_SERVICE_NAME = UIKitApplication:ca.charland.DoTheUITestsWork[0xf28e][29701]
2018-10-15 20:58:13.497370-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_MAINSCREEN_HEIGHT = 1792
2018-10-15 20:58:13.497675-0400 DoTheUITestsWork[31059:673798]   TMPDIR = /Users/michael/Library/Developer/CoreSimulator/Devices/851B3429-9701-4780-AEAF-B06284218EBC/data/Containers/Data/Application/254341CA-44A7-4130-B908-EBFAC65E26DE/tmp
2018-10-15 20:58:13.497952-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_LOG_ROOT = /Users/michael/Library/Logs/CoreSimulator/851B3429-9701-4780-AEAF-B06284218EBC
2018-10-15 20:58:13.498255-0400 DoTheUITestsWork[31059:673798]   PATH = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/usr/bin:/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/bin:/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/usr/sbin:/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/sbin:/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/usr/local/bin
2018-10-15 20:58:13.498564-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_HID_SYSTEM_MANAGER = /Library/Developer/PrivateFrameworks/CoreSimulator.framework/Resources/Platforms/iphoneos/Library/Frameworks/SimulatorHID.framework
2018-10-15 20:58:13.498890-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_MAINSCREEN_WIDTH = 828
2018-10-15 20:58:13.499182-0400 DoTheUITestsWork[31059:673798]   IOS_SIMULATOR_SYSLOG_SOCKET = /tmp/com.apple.CoreSimulator.SimDevice.851B3429-9701-4780-AEAF-B06284218EBC/syslogsock
2018-10-15 20:58:13.499448-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_CAPABILITIES = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/DeviceTypes/iPhone XR.simdevicetype/Contents/Resources/capabilities.plist
2018-10-15 20:58:13.499655-0400 DoTheUITestsWork[31059:673798]   RWI_LISTEN_SOCKET = /private/tmp/com.apple.launchd.oAPb9uYsFP/com.apple.webinspectord_sim.socket
2018-10-15 20:58:13.499929-0400 DoTheUITestsWork[31059:673798]   XPC_SIMULATOR_LAUNCHD_NAME = com.apple.CoreSimulator.SimDevice.851B3429-9701-4780-AEAF-B06284218EBC
2018-10-15 20:58:13.500207-0400 DoTheUITestsWork[31059:673798]   CA_DEBUG_TRANSACTIONS = 0
2018-10-15 20:58:13.500447-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_ROOT = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot
2018-10-15 20:58:13.500732-0400 DoTheUITestsWork[31059:673798]   XCInjectBundleInto = /Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator/DoTheUITestsWork.app/DoTheUITestsWork
2018-10-15 20:58:13.501037-0400 DoTheUITestsWork[31059:673798]   DYLD_LIBRARY_PATH = /Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator
2018-10-15 20:58:13.501338-0400 DoTheUITestsWork[31059:673798]   XPC_FLAGS = 0x0
2018-10-15 20:58:13.501632-0400 DoTheUITestsWork[31059:673798]   DYLD_INSERT_LIBRARIES = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot/usr/lib/libMainThreadChecker.dylib
2018-10-15 20:58:13.501862-0400 DoTheUITestsWork[31059:673798]   MTC_CRASH_ON_REPORT = 1
2018-10-15 20:58:13.502140-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_HOST_HOME = /Users/michael
2018-10-15 20:58:13.502420-0400 DoTheUITestsWork[31059:673798]   DYLD_FRAMEWORK_PATH = /Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator:
2018-10-15 20:58:13.502735-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_AUDIO_SETTINGS_PATH = /Users/michael/Library/Developer/CoreSimulator/Devices/851B3429-9701-4780-AEAF-B06284218EBC/data/var/run/simulatoraudio/audiosettings.plist
2018-10-15 20:58:13.503032-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_SHARED_RESOURCES_DIRECTORY = /Users/michael/Library/Developer/CoreSimulator/Devices/851B3429-9701-4780-AEAF-B06284218EBC/data
2018-10-15 20:58:13.503322-0400 DoTheUITestsWork[31059:673798]   SQLITE_ENABLE_THREAD_ASSERTIONS = 1
2018-10-15 20:58:13.503624-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_UDID = 851B3429-9701-4780-AEAF-B06284218EBC
2018-10-15 20:58:13.503915-0400 DoTheUITestsWork[31059:673798]   SIMULATOR_MODEL_IDENTIFIER = iPhone11,8
2018-10-15 20:58:13.504221-0400 DoTheUITestsWork[31059:673798]   IPHONE_SIMULATOR_ROOT = /Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/Library/CoreSimulator/Profiles/Runtimes/iOS.simruntime/Contents/Resources/RuntimeRoot
2018-10-15 20:58:13.504523-0400 DoTheUITestsWork[31059:673798]   __XPC_DYLD_LIBRARY_PATH = /Users/michael/Library/Developer/Xcode/DerivedData/DoTheUITestsWork-drkfmdibjmrlmibmewfcsultxnau/Build/Products/Debug-iphonesimulator
2018-10-15 20:58:13.504817-0400 DoTheUITestsWork[31059:673798]   CLASSIC = 0
2018-10-15 20:58:13.505100-0400 DoTheUITestsWork[31059:673798]   IPHONE_SHARED_RESOURCES_DIRECTORY = /Users/michael/Library/Developer/CoreSimulator/Devices/851B3429-9701-4780-AEAF-B06284218EBC/data
```

Notes:
- Deleting derived data did not fix the issue
- Commenting out the line 'pod 'iOSSnapshotTestCase'' the tests run as expected
