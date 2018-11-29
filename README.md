# ijkplayer
[![](https://img.shields.io/badge/platform-android-orange.svg)](https://github.com/hacknife) [![](https://img.shields.io/badge/language-java-yellow.svg)](https://github.com/hacknife) [![](https://img.shields.io/badge/jcenter-0.8.8-brightgreen.svg)](http://jcenter.bintray.com/com/hacknife/ijkplayer) [![](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/hacknife) [![](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/hacknife) [![](https://img.shields.io/badge/api-19+-green.svg)](https://github.com/hacknife)<br/><br/>
基于android端编译的ijkplayer、支持Https、附带编译教程，可快速引入项目。
### 快速引入项目
```
allprojects {
    repositories {
        jcenter()
    }
}

dependencies {
    # required, enough for most devices.
    compile 'com.hacknife.ijkplayer:ijkplayer-java:0.8.8'
    compile 'com.hacknife.ijkplayer:ijkplayer-armv7a:0.8.8'

    # Other ABIs: optional
    compile 'com.hacknife.ijkplayer:ijkplayer-armv5:0.8.8'
    compile 'com.hacknife.ijkplayer:ijkplayer-arm64:0.8.8'
    compile 'com.hacknife.ijkplayer:ijkplayer-x86:0.8.8'
    compile 'com.hacknife.ijkplayer:ijkplayer-x86_64:0.8.8'

    # ExoPlayer as IMediaPlayer: optional, experimental
    compile 'tv.danmaku.ijk.media:ijkplayer-exo:0.8.8'
}
```
### 配置环境
```
# 你的NDK路径
NDK=/home/hacknife/Android/Sdk/ndk-bundle
export NDK
# 你的ADB路径
ADB=/home/hacknife/Android/Sdk/platform-tools
export ADB
# 你的ANDROID_NDK和ANDROID_SDK 路径
ANDROID_NDK=/home/hacknife/Android/Sdk/ndk-bundle
export ANDROID_NDK
ANDROID_SDK=/home/hacknife/Android/Sdk
export ANDROID_SDK 
# 加入到PATH路径
PATH=${PATH}:${NDK}:${ADB}:${ANDROID_NDK}:${ANDROID_SDK}
```
### 开始编译
#### 拉取ijkplayer源码
```
git clone https://github.com/Bilibili/ijkplayer.git ijkplayer-android
cd ijkplayer-android
git checkout -B latest k0.8.8
```
#### 初始化android
```
./init-android.sh
```
#### 初始化openssl支持Https
```
./init-android-openssl.sh
```
#### 清除一波
```
cd android/contrib
./compile-openssl.sh clean
./compile-ffmpeg.sh clean
```
#### 编译openssl
```
./compile-openssl.sh all
```
#### 编译ffmpeg
这里的话看你需要，如果想编译所有版本的so库，就跟all，如果是特定 CPU架构就跟cpu架构，比如：./compile-ffmpeg.sh armv7a编译特定需要的肯定是比全部耗时短~
```
./compile-ffmpeg.sh all
```
#### 编译ijkplayer
加all默认编译所有架构的so库，不加默认只编译armv7a架构！
```
cd ..
./compile-ijk.sh all
```
