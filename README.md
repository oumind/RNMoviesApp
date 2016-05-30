#项目说明

该项目是从 react-native项目中的 Examples/Movies 迁移过来，主要是因为react-native官方的几个例子都不是标准的 react-native init 的结果，编译运行也不能使用 react-native 命令，而且编译 android 需要NDK(安装包太大)

#当前版本

v0.26.2

#项目创建过程

1. 下载 https://github.com/facebook/react-native 项目下载到 react-native 目录
2. 执行 react-native init RNMoviesApp 命令
3. 将 react-native/Examples/Movies 文件复制到 RNMoviesApp 目录下，除了以下文件
   - android 目录
   - README.md 文件
   - Movies 目录
   - Movies.xcodeproj
   - __tests__ 目录
4. 删除 index.android.js 和 index.ios.js 文件
5. 分别将 MoviesApp.android.js 和 MoviesApp.ios.js 重名为 index.android.js 和 index.ios.js
6. 将 index.android.js 和 index.ios.js 中的
    ```
    AppRegistry.registerComponent('MoviesApp', () => MoviesApp);
    修改为
    AppRegistry.registerComponent('RNMoviesApp', () => MoviesApp);
    ```
7. 添加 package.json 文件, 内容如下：
    ```
    {
      "name": "RNMoviesApp",
      "version": "0.26.2",
      "private": true,
      "scripts": {
        "start": "node_modules/react-native/packager/packager.sh"
      },
      "dependencies": {
        "react": "15.0.2",
        "react-native": "^0.26.2"
      }
    }
    ```

##android 项目修改如下

1. 复制图片，复制 react-native/Examples/Movies/android/app/src/main/res/ drawable打头的所有目录  到 RNMoviesApp/android/app/src/main/res/ 目录
3. 修改权限，修改 AndroidManifest.xml 文件

    ```
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW"/>

    修改为

    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW"/>

    ```
4. 修改图标，修改 AndroidManifest.xml 文件

    ```
    android:icon="@mipmap/ic_launcher"
    修改为
    android:icon="@drawable/launcher_icon"
    ```

##iOS 项目无需修改

#TODO
>项目自动化生成
