# Table of Contents

1. [Hook failed with error code 127](#hook-failed-with-error-code-127)
2. [Manifest merger failed](#manifest-merger-failed)
3. [error: cannot find symbol](#error-cannot-find-symbol)
4. [error: Value for SWIFT_VERSION cannot be empty](#error-value-for-swift_version-cannot-be-empty)

---

## Hook failed with error code 127

The following error message appeared:

```sh
➜ cordova plugin add cordova-plugin-lottie-splashscreen
Installing "cordova-plugin-lottie-splashscreen" for ios
Running command: /Users/timbru31/work/cordova-plugin-lottie-splashscreen/hooks/ios/update_pod_repo.sh /Users/timbru31/work/hello
/Users/timbru/work/ume/cordova-plugin-lottie-splashscreen/hooks/ios/update_pod_repo.sh: line 2: pod: command not found
/Users/timbru/work/ume/cordova-plugin-lottie-splashscreen/hooks/ios/update_pod_repo.sh: line 3: pod: command not found
Failed to install 'cordova-plugin-lottie-splashscreen': Error: Hook failed with error code 127: /Users/timbru31/work/cordova-plugin-lottie-splashscreen/hooks/ios/update_pod_repo.sh
    at /usr/local/lib/node_modules/cordova/node_modules/cordova-lib/src/hooks/HooksRunner.js:224:23
    at _rejected (/usr/local/lib/node_modules/cordova/node_modules/q/q.js:864:24)
    at /usr/local/lib/node_modules/cordova/node_modules/q/q.js:890:30
    at Promise.when (/usr/local/lib/node_modules/cordova/node_modules/q/q.js:1142:31)
    at Promise.promise.promiseDispatch (/usr/local/lib/node_modules/cordova/node_modules/q/q.js:808:41)
    at /usr/local/lib/node_modules/cordova/node_modules/q/q.js:624:44
    at runSingle (/usr/local/lib/node_modules/cordova/node_modules/q/q.js:137:13)
    at flush (/usr/local/lib/node_modules/cordova/node_modules/q/q.js:125:13)
    at processTicksAndRejections (internal/process/task_queues.js:79:9)
Hook failed with error code 127: /Users/timbru31/work/cordova-plugin-lottie-splashscreen/hooks/ios/update_pod_repo.sh
```

### Answer

It seems that the `pod` gem (the [package manager for Swift and Objective-C](https://cocoapods.org/) projects) is not installed. Fix it with:

```sh
$ sudo gem install cocoapods
$ pod setup
$ cordova plugin add cordova-plugin-lottie-splashscreen
```

## Manifest merger failed

```
> Manifest merger failed : Attribute application@appComponentFactory value=(android.support.v4.app.CoreComponentFactory) from [com.android.support:support-compat:28.0.0] AndroidManifest.xml:22:18-91
  	is also present at [androidx.core:core:1.0.0] AndroidManifest.xml:22:18-86 value=(androidx.core.app.CoreComponentFactory).
  	Suggestion: add 'tools:replace="android:appComponentFactory"' to <application> element at AndroidManifest.xml:5:5-12:19 to override.
```

### Answer

Install the add cordova-plugin-androidx and cordova-plugin-androidx-adapter plugins.

```sh
$ cordova plugin add cordova-plugin-androidx
$ cordova plugin add cordova-plugin-androidx-adapter
```

## error: cannot find symbol

```
/Users/timbrust/Coding/cordova-hello-world/platforms/android/app/src/main/java/cordova/plugins/Diagnostic_Notifications.java:35: error: cannot find symbol
import android.support.v4.app.NotificationManagerCompat;
```

### Answer

Install the add cordova-plugin-androidx and cordova-plugin-androidx-adapter plugins.

```sh
$ cordova plugin add cordova-plugin-androidx
$ cordova plugin add cordova-plugin-androidx-adapter
```

## error: Value for SWIFT_VERSION cannot be empty

```
error: Value for SWIFT_VERSION cannot be empty. (in target 'HelloCordova')

** BUILD FAILED **

xcodebuild: Command failed with exit code 65
```

### Answer

Add the following preference to the `config.xml` iOS section: `<preference name="SwiftVersion" value="4.2" />`.
