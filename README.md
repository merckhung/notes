Debug trap on platforms
================================
| Architecture       | debug_break() |
| -------------      | ------------- |
| x86/x86-64         | `int3`  |
| ARM mode, 32-bit   | `.inst 0xe7f001f0`  |
| Thumb mode, 32-bit | `.inst 0xde01`  |
| AArch64, ARMv8     | `.inst 0xd4200000` |
| MSVC compiler      | `__debugbreak` |
| Apple compiler on AArch64     | `__builtin_trap()` |

Basic SKIA drawing
================================
```C++
  SkRect r = SkRect::MakeXYWH(0, 0, w_, h_);
  SkPaint p;
  p.setColor(0xFFFFFFFF);
  p.setStyle(SkPaint::kFill_Style);
  canvas->drawRect(r, p);
```

Android Introduction
================================
0) Android architecture:
- https://source.android.com/devices/architecture
- https://developer.android.com/guide/platform

1) Flash Pixel phones online:
- https://flash.android.com

2) Android source code:
- https://cs.android.com/

3) GUI programming language paradigm:
- Imperative
- Declarative

4) ADB: Android Debug Bridge
- adb can be used via USB and WI-FI (TCP/IP) connections.
- ADB Commands:
- adb logcat
- adb shell
- adb disable-verity
- adb reboot
- adb reboot bootloader

5) Fastboot is a flash tool fot Android phones:
- fastboot reboot
- fastboot erase <PARTITION>
- fastboot flash <PARTITION> <IMAGE_FILE>

6) To unlock/lock the bootloader of an Android phone:
- https://source.android.com/setup/build/running#unlocking-the-bootloader
- fastboot flashing unlock
- fastboot flashing lock

7) System partitions:
- /sys  -> More IO peripheral controls
- /proc -> More Linux kernel related controls
- /data -> All downloaded APKs and runtime files
- /system -> Android framework and APIs
- /vendor -> Vendor specific implementation

8) Zygote (How does a Android app start):
- https://android.jlelse.eu/android-application-launch-explained-from-zygote-to-your-activity-oncreate-8a8f036864b

9) Android App Lifecycle:
- https://www.geeksforgeeks.org/activity-lifecycle-in-android-with-demo-app/

10) I/O peripherals an Android App can access via Java APIs:
- Proximity
- G-sensor
- GPS, WiFi
- 4G-LTE, 3G
- Camera
- Microphone
- Speaker

Android App Development
================================
0) Android Studio, SDK, NDK, am, pm, adb install, aapt, download an APK, APK file structure
- Android Studio: https://developer.android.com/studio
- https://developer.android.com/ndk/guides
- adb pull /system/app/Maps/Maps.apk
- adb install ABC.apk
- adb uninstall ABC
- adb install -r ABC.apk
- APK key signing: https://developer.android.com/studio/publish/app-signing
- https://www.techotopia.com/index.php/Generating_a_Signed_Release_APK_File_in_Android_Studio
- adb shell pm dump all
- adb shell pm list packages
- https://stackoverflow.com/questions/22634446/sending-intent-to-broadcastreceiver-from-adb
- adb shell am start -n com.example.demo/com.example.test.MainActivity
- adb shell am force-stop <PACKAGE>
- adb shell ps -A
- adb shell kill <PID>

1) A simple Andorid app (API version, Android OS version, deprecated APIs, event handling, compilation flow)
- https://developer.android.com/reference
- https://www.xda-developers.com/android-version-distribution-statistics-android-studio/
- https://developer.android.com/guide/topics/ui/ui-events
- https://www.tutorialspoint.com/android/android_event_handling.htm
- https://en.wikibooks.org/wiki/Java_Programming/Compilation
- https://medium.com/@banmarkovic/process-of-compiling-android-app-with-java-kotlin-code-27edcfcce616

2) Layout, resource R.*, Button, Login page, button listener
- https://developer.android.com/guide/topics/ui/declaring-layout
- https://developer.android.com/reference/android/R
- https://www.tutorialspoint.com/android/android_user_interface_layouts.htm
- https://guides.codepath.com/android/Basic-Event-Listeners

3) Debug, Profiling, GPU inspector, Man-in-the-middle (MITM), SSL pinning
- https://gpuinspector.dev/
- https://developer.android.com/studio/profile/network-profiler
- https://www.charlesproxy.com/documentation/proxying/ssl-proxying/
- https://blog.approov.io/securing-https-with-certificate-pinning-on-android
- https://levelup.gitconnected.com/bypassing-ssl-pinning-on-android-3c82f5c51d86

4) logcat
- https://developer.android.com/reference/android/util/Log
- __android_log_print();
- https://developer.android.com/ndk/reference/group/logging

5) Main UI thread and AsyncTask
- https://developer.android.com/reference/android/os/AsyncTask
- https://www.journaldev.com/8988/android-studio-tutorial-hello-world-app
- https://stackoverflow.com/questions/9671546/asynctask-android-example

6) Permission, HTTP example, network policy
- https://developer.android.com/training/basics/network-ops/connecting#java
- https://developer.android.com/reference/android/Manifest.permission
- https://developer.android.com/reference/java/net/HttpURLConnection

7) Perfetto and systrace
- https://developer.android.com/studio/command-line/perfetto
- https://ui.perfetto.dev/#!/
- https://developer.android.com/topic/performance/tracing/command-line
- https://source.android.com/devices/tech/debug/systrace

8) Practice the usage of UI widgets
- https://www.tutorialspoint.com/android/android_alert_dialoges.htm

9) Practice Java APIs
- https://developer.android.com/reference
- https://www.geeksforgeeks.org/java-io-inputstream-class-in-java/
