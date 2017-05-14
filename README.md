# chromium-for-android-56-debug-video

前言:

&emsp;&emsp;在开发chromium for android时一个很繁琐的问题就是对应用层java代码的调试。

&emsp;&emsp;虽然我们可以通过在java代码中加入

```cpp
try {
     throw new Exception("Call Stack Trace");
} catch(Exception e) {
     Log.i("hsner", "xxx", e)
     }
```
    

&emsp;&emsp;的方式打印堆栈信息。

&emsp;&emsp;但如果我们想使用android studio调试代码，就需要将java层代码抽取出来。

&emsp;&emsp;从365浏览器(https://github.com/mogoweb/365browser) 中可以得之这种方法是可行的。

&emsp;&emsp;并在delion(https://github.com/derry/delion) 以及AndroidChromium (https://github.com/JackyAndroid/AndroidChromium) 的基础上我们抽取了56.0.2924.87版本的java层代码。

注意:

&emsp;&emsp;一、本版本之所以称为debug版本是因为在args.gn中is_debug设置为true, 不过本版本可能容易崩溃。release版本见https://github.com/rkshuai/chromium-for-android-56-release-video 

&emsp;&emsp;二、本版本在args.gn中对video编码进行了设置，因此可以播放视频。

&emsp;&emsp;三、本版本和365 delion AndroidChromium在抽取上的差别是将en-US.pak和zh-CN.pak资源放到assets里面，因为BuildConfig.java这个生成文件和之前的chromium版本不同。新版本中增加了两个变量COMPRESSED_LOCALES和 UNCOMPRESSED_LOCALES，我们需要将COMPRESSED_LOCALES数组置空，而将UNCOMPRESSED_LOCALES数组置为”en-US”， ”zh-CN”（反之也行）。如果不这样进行设置运行apk时就会发生崩溃。

&emsp;&emsp;四、如果使用android studio 2.0以上版本并且开启了instant run功能，需关闭后再进行编译。

效果图展示:

![](https://github.com/rkshuai/chromium-for-android-56-debug-video/blob/master/photo/setting.png)     ![](https://github.com/rkshuai/chromium-for-android-56-debug-video/blob/master/photo/video.png)
