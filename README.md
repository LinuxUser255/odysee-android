# Odysee Android

<a href="https://github.com/OdyseeTeam/odysee-android/blob/master/LICENSE" title="MIT licensed">
   <img alt="license" src="https://img.shields.io/github/license/OdyseeTeam/odysee-android?style=for-the-badge">
</a>

## Build from Source
**Instructions:**

1. Download and install [Android Studio](https://developer.android.com/studio#downloads) or [Intellij Idea](https://www.jetbrains.com/idea/), ( Intellij IDE worked for me in building this APK)


2. git clone this repo into a directory of your chosinng on your machine

 `git clone https://github.com/LinuxUser255/odysee-android.git`

3. You will have to update the JDK, and SDK in the IDE when you open this repo. (I used the Android API 35 SDK)


4. Then navigate in the file tree to `app/twitter.properties.sample` and copy it and name the copy: `app/twitter.properties`


5. Open the  copy of twitter .properties you made and delete the XXXXXX values so that it looks like this:

```
TWITTER_CONSUMER_KEY=
TWITTER_CONSUMER_SECRET=
```

6. Now to proceed to the next step, you will need to have a signing key/digital signature to build this APK, this is done using the IDE


7. In the menu go to-> `buid/Generate signed APK`
   follow the prompts, and remember the passwords and alias you created


8. At this point you now need to add your APK digital signature to the `app/build.gradle` file
   Adding it using the `build.gradle` provided by Odysee can be tricky, so I am including mine to use as a template,
   It looks like this, but just edit the one here in my fork of this repo. See line 40 in my [build.gradle](https://github.com/LinuxUser255/odysee-android/blob/master/build.gradle
   ) and type in the creds you created.



```groovy
android {
    signingConfigs {
        release {
            storeFile file('<<put full path to the .JKS Java keychain file>>')
            storePassword '<<password of the file>>'
            keyAlias '<<the alias you chose for the digital signature>>'
            keyPassword '<<the password for the key>>'
        }
    }
(...)

    buildTypes {
      release {
          (...)
          debuggable false
          signingConfig signingConfigs.release
      }
```

9. Then you will be able to build a signed APK file via `Build/Generate Signed Bundle/APK`... menu item on Android Studio
   There are two build variants: Full and FOSS. The Full variant uses Google APIs and the FOSS variant doesn't.
   You can switch between them on the "Build Variants" tab in Android Studio.


11. In the IDE menu navigate to: Build/Generate Signed Bundle/APK
    Observe the file/directory location where the APK will be stored. You need to know this when side loading it on your phone.


12. Once you succesfully completed the steps above, you can side load it using Android Debug Bridge `adb` in the command line
    https://developer.android.com/tools/adb
    There are some decent online tutorials on how to do this.






## Contributing
We :heart: contributions from everyone and contributions to this project are encouraged, and compensated. We welcome [bug reports](https://github.com/OdyseeTeam/odysee-android/issues/), [bug fixes](https://github.com/OdyseeTeam/odysee-android/pulls) and feedback is always appreciated.

## [![contributions welcome](https://img.shields.io/github/issues/OdyseeTeam/odysee-android?style=for-the-badge&color=informational)](https://github.com/OdyseeTeam/odysee-android/issues) [![GitHub contributors](https://img.shields.io/github/contributors/OdyseeTeam/odysee-android?style=for-the-badge)](https://gitHub.com/OdyseeTeam/odysee-android/graphs/contributors/)

## License
~~This project is MIT licensed. For the full license, see [LICENSE](LICENSE).~~

**My fork of this project uses the [GNU Public License Version 3 (GPLv3)](https://www.gnu.org/licenses/quick-guide-gplv3.html)**


## Security
We take security seriously. Please contact security@odysee.com regarding any security issues.

## Contact
The primary contact for this project is [@akinwale](https://github.com/akinwale) (akinwale.ariwodola@odysee.com)
