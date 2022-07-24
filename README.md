# AndroidIDE-NDK
This bash script will install ndk r24 by jzinferno to AndroidIDE app.
- Install NDK-r24 for AndroidIDE in one command :
```cd && pkg up && pkg in wget &&
wget https://github.com/MrIkso/AndroidIDE-NDK/raw/main/ndk-install.sh && chmod +x ndk-install.sh && ./ndk-install.sh
```
- Set ndkVersion in your build.gradle to ```ndkVersion "24.0.8215888"``` and set cmake version to ```version '3.23.1'```

Demo

```
plugins {
    id 'com.android.application'
}

android {
    compileSdk 32
    buildToolsVersion "33.0.0"
    ndkVersion "24.0.8215888"

    defaultConfig {
        applicationId "com.myapplication"
        minSdk 23
        targetSdk 32
        versionCode 1
        versionName "1.0"
    }
    
    buildTypes {
        release {
            minifyEnabled false
            proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
        }
    }

    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }

    externalNativeBuild {
        cmake {
            path file('src/main/cpp/CMakeLists.txt')
            version '3.23.1'
        }
    }
}

dependencies {
   ...
}
```

Thanks to jzinferno and Lzhiyong
