# Android-SSL-pinning-Bypass
Android SSL pinning bypass is a method used to subvert the security mechanisms of Android applications that employ SSL certificate pinning. SSL pinning is a security feature that enforces trust in a specific certificate, making it challenging for malicious actors to intercept or manipulate network traffic. Bypassing this mechanism involves modifying the app or using proxy tools to intercept and tamper with SSL communications, potentially compromising the confidentiality and integrity of data being transmitted. This poses significant security risks and is often associated with unauthorized access to sensitive information.

## Install Genymotion:
 - Go here to download Genymotion `https://www.genymotion.com/download/`
 - Tutorial: `https://youtu.be/_HRpLPrlg1U` (Thanks to InsiderPhD)

## Downlaod Platform-tool
 - Go here to download ADB `https://developer.android.com/tools/releases/platform-tools`

## Install Certificate:
 - Downlaod Burp Suite Certificate (Burp Suite > Proxy > Options Import / export CA certificate)
 - Rename the certificate file as `cert.crt`
 - Execute the following command in the command prompt `adb root && adb remount && adb push cert.crt /system/etc/security/cacerts/ && adb shell chmod 644 /system/etc/security/cacerts/cert.crt && adb shell sync && adb shell reboot`

Note: cert.crt should be in the adb folder.

## Burp Suite Proxy Setup:
 - Set: `adb shell settings put global http_proxy IP:PORT`
 - Disable: `adb shell settings put global http_proxy :0`

## Install Frida and frida server:
 - Install frida on windows `pip3 install Frida ` then `pip install frida-tools`
 - Check frida version `frida --version`
 - Verify the emulator device's processor type `adb shell getprop ro.product.cpu.abi`
 - Download the matching version of Frida Server with the compatible processor type from here `https://github.com/frida/frida/releases`
 - Upload Frida Server on device `adb push frida-server /data/local/tmp`
 - Change the frida-server file permission `adb shell chmod 777 /data/local/tmp/frida-server`
 - Run Frida Server `adb shell /data/local/tmp/frida-server &`

## Bypass SSL using Frida
 - Execute the following command in the command prompt `frida -U -f package_name -l injected.js`

## Find package_name
 - Method 1: Execute the following command `Frida-ps -Uai`
 - Method 2: Install the app on the device `https://play.google.com/store/apps/details?id=com.csdroid.pkg`

## Frida Projects Resource
 - Visit https://codeshare.frida.re

## Contact
If you experience any problems, don't hesitate to contact me on [Twitter](https://twitter.com/0xadik).
